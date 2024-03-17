https://www.yuque.com/u295415/xbahyh/odow2zkn1kr00a6n?singleDoc#

1.在 全部 配置 typeorm 映射库

2.在 auth 模块中配置 jwt 的策略

3.在app.molues 中配置守卫 负责拦截所有请求

TypeORM+MySQL

登录+JWT+加密

![image-20240316125411951](assets\image-20240316125411951.png)

## 前期工作

创建项目

```
nest new auth-test
```

配置package.json

安装依赖

```
npm install
```

![image-20240316121955376](assets\image-20240316121955376.png)

创建模块

```
nest g res auth
? What transport layer do you use? REST API
? Would you like to generate CRUD entry points? Yes
CREATE src/auth/auth.controller.ts (917 bytes)
CREATE src/auth/auth.controller.spec.ts (576 bytes)
CREATE src/auth/auth.module.ts (250 bytes)
CREATE src/auth/auth.service.ts (633 bytes)
CREATE src/auth/auth.service.spec.ts (464 bytes)
CREATE src/auth/dto/create-auth.dto.ts (31 bytes)
CREATE src/auth/dto/update-auth.dto.ts (173 bytes)
CREATE src/auth/entities/auth.entity.ts (22 bytes)
UPDATE src/app.module.ts (318 bytes)
```

### 连接数据库

在app.module中

```
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { AuthModule } from './auth/auth.module';
// 连接数据库
import { TypeOrmModule } from '@nestjs/typeorm';

@Module({
  imports: [AuthModule, 
    // 连接数据库
    TypeOrmModule.forRoot({
    type: 'mysql', // 数据库类型
    host: 'localhost', // 主机名
    port: 3306, // 端口
    username: 'root', // 用户名
    password: '111111', // 密码
    database: 'auth', // 数据库名称
    synchronize: true,
    retryDelay: 500, //重试连接数据库间隔
    retryAttempts: 10,//重试连接数据库的次数
    autoLoadEntities: true, //如果为true,将自动加载实体 forFeature()方法注册的每个实体都将自动添加到配置对象的实体数组中
  })],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}

```

```
CREATE TABLE NV_Users (
  id int NOT NULL AUTO_INCREMENT,
  username varchar(255) NOT NULL,
  password varchar(255) NOT NULL,
  PRIMARY KEY (id)
);
```

### 配置实体类，建立映射

```
import { Column, PrimaryGeneratedColumn } from "typeorm";

@Entity()
export class NV_Users {

    @PrimaryGeneratedColumn()
    id:number

    @Column()
    username:string

    @Column()
    password:string
}

```

### 定义请求DTO

```
export class CreateAuthDto {
    username: string
    password: string
}

```

### 授权控制

common/public.decorator.ts

```
import { SetMetadata } from "@nestjs/common";

export const IS_PUBLIC_KEY = 'isPublic'
export const Public = () => SetMetadata(IS_PUBLIC_KEY, true);
```



### 写业务逻辑

```
import { BadRequestException, Injectable } from '@nestjs/common';
import { CreateAuthDto } from './dto/create-auth.dto';
import { NV_Users } from './entities/auth.entity';
import { Repository } from 'typeorm';
import { InjectRepository } from '@nestjs/typeorm';
import * as bcryptjs from "bcryptjs"
import { JwtService } from "@nestjs/jwt"


@Injectable()
export class AuthService {
    constructor(
        @InjectRepository(NV_Users) private readonly user: Repository<NV_Users>,
        private readonly JwtService: JwtService
    ) { }
    // 注册
    async signup(signupData: CreateAuthDto) {
        
        const findUser = await this.user.findOne({
            where: { username: signupData.username }
        })
        if (findUser && findUser.username === signupData.username) return "用户已存在"
        // 对密码进行加密处理
        signupData.password = bcryptjs.hashSync(signupData.password, 10)
        await this.user.save(signupData)
        return "注册成功"
    }

    // 登录
    async login(loginData: CreateAuthDto) {
        const findUser = await this.user.findOne({
            where: { username: loginData.username }
        })
        // 没有找到
        if (!findUser) return new BadRequestException("用户不存在")

        // 找到了对比密码
        const compareRes: boolean = bcryptjs.compareSync(loginData.password, findUser.password)
        // 密码不正确
        if (!compareRes) return new BadRequestException("密码不正确")
        const payload = { username: findUser.username }

        return {
            access_token: this.JwtService.sign(payload),
            msg: "登录成功"
        }
    }
}

```



### 写请求层

```
import { Controller, Post, Body } from '@nestjs/common';
import { AuthService } from './auth.service';
import { CreateAuthDto } from './dto/create-auth.dto';
import { Public } from 'src/common/public.decorator';

@Controller('auth')
export class AuthController {
  constructor(private readonly authService: AuthService) { }

  // 注册
  // @Public()
  @Post("/signup")
  signup(@Body() signupData: CreateAuthDto) {
    return this.authService.signup(signupData)
  }

  // 登录
  @Public()//Public():需要进行授权，才能进行访问
  @Post("/login")
  login(@Body() loginData: CreateAuthDto) {
    return this.authService.login(loginData)
  }
}

```



### 配置拦截守卫

jwt-auth.gard

```
import { ExecutionContext, Injectable } from "@nestjs/common";
import { Reflector } from '@nestjs/core';
import { AuthGuard } from '@nestjs/passport';
import { Observable } from "rxjs";
import { IS_PUBLIC_KEY } from "src/common/public.decorator";

@Injectable()
export class JwtAuthGuard extends AuthGuard("jwt") {
    constructor(private reflector: Reflector) {
        super()
    }

    canActivate(context: ExecutionContext): boolean | Promise<boolean> | Observable<boolean> {
        const isPublic = this.reflector.getAllAndOverride<boolean>(IS_PUBLIC_KEY, [
            context.getHandler(),
            context.getClass()
        ])
        console.log(isPublic, "isPublic");
        if (isPublic) return true
        return super.canActivate(context)
    }
}
```

main.st配置

```
import { Module } from '@nestjs/common';
import { AuthService } from './auth.service';
import { AuthController } from './auth.controller';
import { TypeOrmModule } from '@nestjs/typeorm';
import { NV_Users } from './entities/auth.entity';
import { JwtModule } from '@nestjs/jwt';
import { jwtConstants } from "./constants"
import { JwtAuthStrategy } from "./jwt-auth.strategy"


@Module({
  imports: [TypeOrmModule.forFeature([NV_Users]), JwtModule.register({
    secret: jwtConstants.secret,
    signOptions: { expiresIn: jwtConstants.expiresIn }
  })],
  controllers: [AuthController],
  providers: [AuthService, JwtAuthStrategy]
})
export class AuthModule { }

```

auth.module配置

```
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { AuthModule } from './auth/auth.module';
import { TypeOrmModule } from '@nestjs/typeorm';
import { APP_GUARD } from '@nestjs/core';
import { JwtAuthGuard } from './auth/jwt-auth.grard';

@Module({
  imports: [AuthModule, TypeOrmModule.forRoot({
    type: 'mysql', // 数据库类型
    host: 'localhost', // 主机名
    port: 3306, // 端口
    username: 'root', // 用户名
    password: 'root', // 密码
    database: 'auth', // 数据库名称
    synchronize: true,
    retryDelay: 500, //重试连接数据库间隔
    retryAttempts: 10,//重试连接数据库的次数
    autoLoadEntities: true, //如果为true,将自动加载实体 forFeature()方法注册的每个实体都将自动添加到配置对象的实体数组中
  })],
  controllers: [AppController],
  // 注册为全局守卫
  providers: [AppService, {
    provide: APP_GUARD,
    useClass: JwtAuthGuard
  }],
})
export class AppModule { }

```



### 设置密钥有效时间

constants.ts

```
export const jwtConstants = {
    secret: "leeKey", // 密钥
    expiresIn: "60s" // token有效时间  
}
```

### auth策略

jwt-auth.strategy.ts

```
import { Injectable } from "@nestjs/common";
import { PassportStrategy } from "@nestjs/passport";
import { ExtractJwt, Strategy } from "passport-jwt";
import { jwtConstants } from "./constants";


interface JwtPayload {
    username: string
}

@Injectable()
// 验证请求头中的token
export class JwtAuthStrategy extends PassportStrategy(Strategy, "jwt") {
    constructor() {
        super(
        {
            jwtFromRequest: ExtractJwt.fromAuthHeaderAsBearerToken(),
            ignoreExpiration: false,
            secretOrKey: jwtConstants.secret
        }
        )
    }

    async validate(payload: JwtPayload) {
        console.log(payload.username);
        const { username } = payload
        return {
            username
        }
    }
}
```

## 测试

![image-20240316130335203](assets\image-20240316130335203.png)

登录

![image-20240316130437931](assets\image-20240316130437931.png)

![image-20240316130526606](assets\image-20240316130526606.png)