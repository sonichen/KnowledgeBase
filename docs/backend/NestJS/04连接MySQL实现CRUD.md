TypeORM

https://www.typeorm.org/

在app.module.ts中

## 连接数据库



1.定义数据库连接模块

NestJS提供了ORM库来安装mysql，库名typeorm

```
npm add @nestjs/typeorm mysql
```

引入并且配置

```typescript
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { TypeOrmModule } from '@nestjs/typeorm';
// 装饰器
// 模块注册中心， 类似Vue中App.vue
// 所有的模块都在这里注册，后续app.module会把模块交给factory
// 1. 所有子模块都定义在 根模块上
@Module({
  imports: [
    TypeOrmModule.forRoot({
      type: 'mysql', // 数据库类型
      host: 'localhost', // 数据库ip地址
      port: 3306, // 端口
      username: 'root', // 登录名
      password: '111111', // 密码
      database: 'test', // 数据库名称
      entities: [__dirname + '/**/*.entity{.ts,.js}'], // 扫描本项目中.entity.ts或者.entity.js的文件
      synchronize: true, // 定义数据库表结构与实体类字段同步(这里一旦数据库少了字段就会自动加入,根据需要来使用)
    })
  ],
  // 控制器请求
  controllers: [AppController],
  providers: [AppService],
})
// AppModule
// 1. 只要被provider所修饰，@Injectable()装配注解所修饰
// 2. 写一个service， 被其他地方调用，@Injectable()
// 3. 可以被放到provider放的类、接口，都是被@Injectable()
export class AppModule {}

```

```sql
CREATE TABLE `users` (
  `id` int NOT NULL AUTO_INCREMENT COMMENT 'primary key',
  `name` varchar(30) DEFAULT NULL COMMENT 'user name',
  `age` int DEFAULT NULL COMMENT 'user age',
  `created_at` datetime DEFAULT NULL COMMENT 'created time',
  `updated_at` datetime DEFAULT NULL COMMENT 'updated time',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=11 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_0900_ai_ci COMMENT='user'

INSERT INTO users(id, name, age, created_at, updated_at)VALUES(1, 'John Doe', 25, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(2, 'Jane Smith', 30, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(3, 'Michael Johnson', 40, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(4, 'Emily Davis', 22, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(5, 'David Wilson', 35, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(6, 'Sarah Anderson', 28, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(7, 'Daniel Thompson', 32, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(8, 'Olivia Martin', 29, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(9, 'Matthew Roberts', 27, '2023-10-26 08:02:44', '2023-10-26 08:02:44');
INSERT INTO users(id, name, age, created_at, updated_at)VALUES(10, 'Isabella Clark', 33, '2023-10-26 08:02:44', '2023-10-26 08:02:44');

```



## CRUD

如何提供一个Restful API?(面试经常被问到)，以Java的角度来看是

1.创建实体类entity

2.写mapper，写XML（数据库查询语句）

3.写DAO接口，写service实现application logic

4.写controller

这里也同理

- 创建 实体 ORM 映射关系 

### 创建 实体 ORM 映射关系 

```typescript
import { Entity, Column, PrimaryGeneratedColumn, CreateDateColumn, UpdateDateColumn } from 'typeorm';

// 表名
@Entity({ name: 'users' })
export class User {
  @PrimaryGeneratedColumn()
  id: number;

  @Column({ length: 30, nullable: true, comment: 'user name' })
  name: string;

  @Column({ nullable: true, comment: 'user age' })
  age: number;

  @CreateDateColumn({ name: 'created_at', type: 'datetime', comment: 'created time' })
  createdAt: Date;

  @UpdateDateColumn({ name: 'updated_at', type: 'datetime', comment: 'updated time' })
  updatedAt: Date;
}
```

### 配置

创建module

```
nest g mo
? What name would you like to use for the module? user
CREATE src/user/user.module.ts (85 bytes)
UPDATE src/app.module.ts (1352 bytes)
```



创建controller

```
nest g co
? What name would you like to use for the controller? user
CREATE src/user/user.controller.ts (101 bytes)
UPDATE src/user/user.module.ts (209 bytes)
```



创建service

```
nest g s
? What name would you like to use for the service? user
CREATE src/user/user.service.ts (92 bytes)
```

回到user.module中

注册信息，标明和哪一张表进行交互

![image-20240314210610306](assets\image-20240314210610306.png)

```typescript
import { Module } from '@nestjs/common';
import { UserController } from './user.controller';
import { UserService } from './user.service';
import {User} from "./user.entity";
import { TypeOrmModule } from '@nestjs/typeorm';

@Module({
    imports:[TypeOrmModule.forFeature([User])],
    providers:[UserService],
    controllers:[UserController]
})
export class UserModule {}

```

业务逻辑写在service里面

主要两步走

1.在main.ts 根module创建数据库的连接

2.业务module创建映射关系

## CRUD

在user.servcie中

```
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { User } from './user.entity';
//   @typeorm用于建立连接
//  * typeorm用于进行增删改查

@Injectable()
export class UserService {
    // 创建操作数据库的对象InjectRepository query、update
    // 注入 this.repository=userRepository
    constructor(@InjectRepository(User)private readonly userRepository:Repository<User>){}
    
    // 查询用户的方法
    async getList():Promise<User[]>{
        return await this.userRepository.find();
    }
    // 通过ID查询用户
    async getUserById(id):Promise<User>{
        return await this.userRepository.findOne({where:{id:id}});
    }
    // 新增用户
    async addUser(body):Promise<User>{
        return await this.userRepository.save(body);
    }
    // 更新用户
    async updateUser(user): Promise<string>{
        await this.userRepository.update({id:user.id},user);
        return "更新成功";
    }
    async deleteUser(params): Promise<object> {
        const res = await this.userRepository.delete({ id: params.id });
        if (res.affected > 0) {
          return {
            code: 0,
            data: "",
            msg: "删除成功"
          };
        } else {
          return {
            code: 0,
            data: "",
            msg: "删除失败"
          };
        }
      }

}

```

在user.controller中

```typescript
import { Controller, Get, Post, Request, Query, Body, Param } from '@nestjs/common';
import { UserService } from './user.service';
import { User } from './user.entity';

@Controller('user')
export class UserController {
    constructor(private userService: UserService) { }

    @Get('list')
    getList(): Promise<User[]> {
        return this.userService.getList();
    }
    // 通过id查询用户
    @Get('getUserById')
    async getUserById(@Query('id') id: string): Promise<User> {
        const userId: number = parseInt(id);
        return this.userService.getUserById(userId);
    }
    // 增加用户
    @Post('addUser')
    addUser(@Body() body): Promise<User> {
        return this.userService.addUser(body);
    }
    // 更新用户
    @Post('updateUser')
    updateUser(@Body() body): Promise<string> {
          return this.userService.updateUser(body);
         
    }
    // 删除用户
    @Post('deleteUser')
    delUser(@Body() body): Promise<object> {
        return this.userService.deleteUser(body);
    }
}

```

user.controller

```typescript
import { Controller, Get } from '@nestjs/common';
import { UserService } from './user.service';
import { User } from './user.entity';

@Controller('user')
export class UserController {
    constructor( private userService:UserService){}

    @Get('list')
    getList():Promise<User[]>{
        return this.userService.getList();
    }

}

```

![image-20240315104117061](assets\image-20240315104117061.png)



## 分页查询

user.service

```
   async findAll(page: number = 1, limit: number = 10): Promise<[User[], number]> {
        const [users, total] = await this.usersRepository.findAndCount({
          skip: (page - 1) * limit,
          take: limit,
        });
        return [users, total];
      }

```

user.controller

```

  @Get('pageList')
  async findAll(@Query('page') page: number, @Query('pagesize') pagesize: number) {
    const [users, total] = await this.usersService.findAll(page, pagesize);
    return {
      data: users,
      total,
      page,
      pagesize,
    };
  }

```



## 条件查询

使用 TypeORM 中的 `FindConditions` 类型时

1. 创建查询条件对象的实例，并指定条件

2. 将条件对象传递给 `find` 方法来执行查询