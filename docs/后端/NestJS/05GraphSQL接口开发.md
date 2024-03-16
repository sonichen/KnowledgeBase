## 安装

```
npm i @nestjs/graphql @nestjs/apollo @apollo/server graphql
```

## 在根目录进行配置

```typescript
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { TypeOrmModule } from '@nestjs/typeorm';
import { UserModule } from './user/user.module';
import { GraphQLModule } from '@nestjs/graphql';
import { ApolloDriverConfig,ApolloDriver } from '@nestjs/apollo'
import { join } from 'path';
// 装饰器
// 模块注册中心， 类似Vue中App.vue
// 所有的模块都在这里注册，后续app.module会把模块交给factory
// 1. 所有子模块都定义在 根模块上
@Module({
  imports: [
    // 连接MySQL
    TypeOrmModule.forRoot({
      type: 'mysql', // 数据库类型
      host: 'localhost', // 数据库ip地址
      port: 3306, // 端口
      username: 'root', // 登录名
      password: '111111', // 密码
      database: 'test', // 数据库名称
      entities: [__dirname + '/**/*.entity{.ts,.js}'], // 扫描本项目中.entity.ts或者.entity.js的文件
      synchronize: true, // 定义数据库表结构与实体类字段同步(这里一旦数据库少了字段就会自动加入,根据需要来使用)
    }),
    // 配置GraghQL
    GraphQLModule.forRoot<ApolloDriverConfig>({
      driver: ApolloDriver,
      autoSchemaFile: join(process.cwd(), 'src/schema.gql'),
    }),
    UserModule
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

![image-20240315161502166](assets\image-20240315161502166.png)

创建文件

![image-20240315161628888](assets\image-20240315161628888.png)

快速生成crud

```shell
nest g res
? What name would you like to use for this resource (plural, e.g., "users")? student
? What transport layer do you use? GraphQL (code first)
? Would you like to generate CRUD entry points? Yes
CREATE src/student/student.module.ts (247 bytes)
CREATE src/student/student.resolver.ts (1241 bytes)
CREATE src/student/student.service.ts (691 bytes)
CREATE src/student/dto/create-student.input.ts (206 bytes)
CREATE src/student/dto/update-student.input.ts (263 bytes)
CREATE src/student/entities/student.entity.ts (197 bytes)
UPDATE src/app.module.ts (1768 bytes)
```

![image-20240315161841669](assets\image-20240315161841669.png)

访问：http://localhost:3000/graphql

![image-20240315162127800](assets\image-20240315162127800.png)