> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_42897427/article/details/134775142?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_utm_term~default-1-134775142-blog-134060860.235^v43^pc_blog_bottom_relevance_base9&spm=1001.2101.3001.4242.1&utm_relevant_index=4)

距离上次认真花时间写作，似乎已经过了许久许久，前端讲了一个新框架 ，叫 Nest.js  
下方是[课件](https://so.csdn.net/so/search?q=%E8%AF%BE%E4%BB%B6&spm=1001.2101.3001.7020)，有过一定开发经验可跟随视频学习

B 站 地址 ： [https://www.bilibili.com/video/BV1Lg4y197u1/?vd_source=ad427ffaf8a5c8344ec0b6ba368461f0](https://www.bilibili.com/video/BV1Lg4y197u1/?vd_source=ad427ffaf8a5c8344ec0b6ba368461f0)

#### 文章目录

*   *   *   [NestJs 介绍](#NestJs__8)
        *   *   [1.1 什么是 Nest.js](#11__Nestjs_23)
            *   [1.2 Nest.js 优点](#12_Nestjs__38)
            *   [1.3. Nest.js 核心概念 （学完理解）](#13_Nestjs___61)
            *   [1.4 快速开始](#14__93)
        *   [NestJs 基础学习](#NestJs__187)
        *   *   [代码生成器](#_199)
            *   [常用装饰器使用](#_236)
            *   [Nest JS 测试](#Nest_JS__403)
        *   [NextJs 增删改查](#NextJs__438)
        *   *   [测试数据](#_440)
            *   [安装 所需依赖](#__473)
            *   [实现 CURD](#_CURD_481)
            *   [安装 VSCode 插件测试](#VSCode__656)
            *   [补充分页查询](#_685)
            *   [条件查询](#_717)
            *   [GraphQL 接口开发实现](#GraphQL__792)
            *   *   [graphQL 介绍](#graphQL__817)
                *   [何时使用 grphQL](#grphQL_837)
                *   [操作实例](#_845)
        *   [NestJs 中间件](#NestJs__1097)
        *   *   [AOP 概念](#AOP_1099)
            *   [Middleware(中间件)](#Middleware_1103)
            *   [MiddlewareConsumer](#MiddlewareConsumer_1164)
        *   [NestJs 异常处理](#NestJs__1373)
        *   *   [异常过滤器](#_1376)
        *   [Nestjs 拦截器](#Nestjs__1603)
        *   *   [案例使用](#_1686)
        *   [NestJs Swagger 接口文档](#NestJs_Swagger__1772)
        *   [Nest js 整合 **Knife4j**](#Nest_js__Knife4j_1861)
        
        *   [NestJs 文件上传](#NestJs__1923)
        *   *   [本地文件上传与下载](#_1927)
            *   [OSS 文件上传](#OSS__2124)
            
        *   [Nest Js 项目实战](#Nest_Js__2308)
        *   [参考](#_2311)

#### NestJs 介绍

![](https://img-blog.csdnimg.cn/img_convert/96d14ce5989d09de88fb345b7577de0c.jpeg)

> `中文官网`: [https://nestjs.bootcss.com/](https://nestjs.bootcss.com/)  
> `中文社区文档`： [https://docs.nestjs.cn/](https://docs.nestjs.cn/)  
> `英文官网`: [https://docs.nestjs.com/graphql/quick-start](https://docs.nestjs.com/graphql/quick-start)  
> `三方文档`: [https://www.kancloud.cn/juukee/nestjs/2676779](https://www.kancloud.cn/juukee/nestjs/2676779)

##### 1.1 什么是 Nest.js

Nest (NestJS) 是一个用于构建高效、可扩展的 [Node.js](https://nodejs.cn/) 服务器端应用的框架。 它使用渐进式 JavaScript，构建并完全支持 [TypeScript](http://ts.nodejs.cn/)（但仍然允许开发者使用纯 JavaScript 进行编码）并结合了 OOP（面向对象编程）、FP（函数式编程）和 FRP（函数式反应式编程）的元素。  
在幕后，Nest 使用强大的 HTTP 服务器框架，如 [Express](https://express.nodejs.cn/)（默认），也可以选择配置为使用 [Fastify](https://fastify.nodejs.cn/)！  
Nest 在这些常见的 Node.js 框架（Express/Fastify）之上提供了一个抽象级别，但也直接向开发者公开了它们的 API。 这使开发者可以自由使用可用于底层平台的无数第三方模块。

1.  NestJS 是一个基于 Node.js 的**服务端应用开发框架**
2.  **完全支持 TypeScript**，也可以使用纯 JS 开发
3.  支持多种编程范式，例如 **OOP 和 FR**
4.  底层处理 HTTP 请求，还是使用了 **Express(默认)**，也可切换为 Fastify
5.  有无数的**第三方模块**可供使用

##### 1.2 Nest.js 优点

支持 TypeScript，使语法更加规范  
兼容 Express 中间件，Express 是最早出现的轻量级的 node server 端框架  
层层处理，可以约束代码，比如何时使用中间件、使用 Guards 守卫 等  
依赖注入及模块化的思想，提供了完整的 MVC 链路，使代码结构清晰，便于维护

有很多人说 Nest js 和 SpringBoot 很类似 ，其实 Nest 就是 Node 当中的 SpringBoot 框架，能够帮助我们快速构建 Web 应用

<table><thead><tr><th>Nestjs</th><th>SpringBoot</th></tr></thead><tbody><tr><td>1. 轻量级，更快；</td><td></td></tr><tr><td>2. 更擅长处理 I/O 任务；</td><td></td></tr><tr><td>3.<strong> 单线程, 内存使用率低</strong>。</td><td>1. 大量成熟组件；</td></tr><tr><td>2.<strong> 支持多线程</strong>；</td><td></td></tr><tr><td>3. 更容易维护。</td><td></td></tr><tr><td>1. 缺少多线程支持；</td><td></td></tr><tr><td>2. 执行计算量大的任务时表现不佳；</td><td></td></tr><tr><td>3. <s>缺少严格的类型检测, 更容易出现导致运行时问题。</s>（如果使用 TypeScript 也会避免此问题)</td><td>1.<strong> 高内存使用率</strong>；</td></tr><tr><td>2. 没用的依赖比较多；</td><td></td></tr><tr><td>3. 大量的模板代码导致调式变困难。</td><td></td></tr></tbody></table>

##### 1.3. Nest.js 核心概念 （学完理解）

**Nest.js 的核心概念和设计原则：**

1.  模块化架构（Modularity）：Nest.js 使用模块化的方式组织应用程序，将功能划分为模块，每个模块负责特定的任务。模块提供了一种封装和隔离的机制，使代码更具可维护性和可测试性。
2.  依赖注入（Dependency Injection）：Nest.js 支持依赖注入模式，通过注入依赖项来解耦组件之间的依赖关系。依赖注入提供了灵活性和可测试性，并促进了代码的重用和可维护性。
3.  控制器与路由（Controllers and Routing）：Nest.js 使用控制器来处理 HTTP 请求，并使用装饰器和路由来定义请求的处理方法。控制器负责处理输入和输出，并将请求转发给相应的服务。
4.  提供者（Providers）：提供者是 Nest.js 应用程序的基本构建块，它们是可注入的类，用于处理业务逻辑、数据访问、服务调用等任务。提供者可以在模块中定义，并通过依赖注入在应用程序中使用。
5.  中间件（Middleware）：中间件是在请求和响应之间进行处理的功能组件，用于处理请求前、请求后和错误处理等任务。Nest.js 中的中间件提供了对请求和响应的灵活处理和修改的机制。
6.  过滤器（Filters）：过滤器用于在异常发生时对异常进行全局处理。它们提供了一种集中处理错误和异常的机制，可以捕获和转换异常，并生成标准化的错误响应。
7.  Guards：守卫是一种用于权限验证和路由保护的功能组件。它们提供了在路由处理之前进行身份验证和授权的机制，以确保只有满足特定条件的请求可以通过。
8.  拦截器（Interceptors）：拦截器用于在请求处理过程中进行全局拦截和修改。它们提供了对请求和响应的拦截和修改的机制，可以在请求前、请求后和异常发生时进行处理。
9.  异常处理（Exception Handling）：Nest.js 提供了一种统一的异常处理机制，可以捕获和处理应用程序中的异常。通过自定义异常过滤器，可以对异常进行全局处理和转换。

*   **控制器 Controller**

客户端的请求，最终交给 哪个函数 / 模块 ，都需要通过预先处理，直接处理客户端请求（路由、方法等）的模块，称之为 控制器

*   **控制器原理：**

控制器 —— 接收应用的特定请求  
路由机制 —— 控制哪个控制器接收哪些请求  
控制器及路由的关系 —— 一个控制器有多个路由，不同路由 执行 不同操作

![](https://img-blog.csdnimg.cn/img_convert/3dc9356bfd2137f09d72a7adf95c8106.png)

> 几乎所有的东西都可以被认为是提供者（例如：service, repository, factory, helper…），提供者的本质：用 @Injectable() 装饰器 注解的简单类

##### 1.4 快速开始

Nestjs 官方提供了一个很好用的脚手架工具，可以用来快速创建，开发和构建一个 Nestjs 应用。  
首先全局安装脚手架工具：

```
npm install -g @nestjs/cli
```

查看脚手架版本号：

```
nest -v
9.1.8
```

使用脚手架提供的 new 命令创建项目：

nest new [项目名] ，后面输入项目名即可

```
nest new hello-nest
```

命令行中会提示选择一个你想要的包管理工具，本文使用 Yarn ，等待几分钟即可

![](https://img-blog.csdnimg.cn/img_convert/805a1e5336e5f4f50db8e9cb73b7acf8.png)

*   等待 1-2 分钟

![](https://img-blog.csdnimg.cn/img_convert/da8dc003aabcf95301c9dfd88d6fad7b.png)

使用 yarn start 快速启动 ，启动成功之后就可以看到 访问默认地址了

![](https://img-blog.csdnimg.cn/img_convert/642824825ce5ee4cce5b01a565484cba.png)

[http://localhost:3000/](http://localhost:3000/)  
![](https://img-blog.csdnimg.cn/img_convert/590c34237aa2cdd16d9978025536ec48.png)

*   项目结构解释

```
+-- dist[目录]                      // 编译后的目录，用于预览项目
+-- node_modules[目录]              // 项目使用的包目录，开发使用和上线使用的都在里边
+-- src[目录]                       // 源文件/代码，程序员主要编写的目录
|  +-- app.controller.spec.ts      // 对于基本控制器的单元测试样例
|  +-- app.controller.ts           // 控制器文件，可以简单理解为路由文件
|  +-- app.module.ts               // 模块文件，在NestJS世界里主要操作的就是模块
|  +-- app.service.ts              // 服务文件，提供的服务文件，业务逻辑编写在这里
|  +-- app.main.ts                 // 项目的入口文件，里边包括项目的主模块和监听端口号
+-- test[目录]                      // 测试文件目录，对项目测试时使用的目录，比如单元测试...
|  +-- app.e2e-spec.ts             // e2e测试，端对端测试文件，测试流程和功能使用
|  +-- jest-e2e.json               // jest测试文件，jset是一款简介的JavaScript测试框架
+-- .eslintrc.js                   // ESlint的配置文件
+-- .gitignore                     // git的配置文件，用于控制哪些文件不受Git管理
+-- .prettierrc                    // prettier配置文件，用于美化/格式化代码的
+-- nest-cli.json                  // 整个项目的配置文件，这个需要根据项目进行不同的配置
+-- package-lock.json              // 防止由于包不同，导致项目无法启动的配置文件，固定包版本
+-- package.json                   // 项目依赖包管理文件和Script文件，比如如何启动项目的命令
+-- README.md                      // 对项目的描述文件，markdown语法
+-- tsconfig.build.json            // TypeScript语法构建时的配置文件
+-- tsconfig.json                  // TypeScript的配置文件，控制TypeScript编译器的一些行为
```

**src 目录下的文件说明** src 目录是日常工作编写代码的主要目录，从基本的目录结构也可以对 NestJS 编写模式有很好的了解。

```
+-- src[目录]                       // 源文件/代码，程序员主要编写的目录
|  +-- app.controller.spec.ts      // 对于基本控制器的单元测试样例
|  +-- app.controller.ts           // 控制器文件，可以简单理解为路由文件
|  +-- app.module.ts               // 模块文件，在NestJS世界里主要操作的就是模块
|  +-- app.service.ts              // 服务文件，提供的服务文件，业务逻辑编写在这里
|  +-- app.main.ts                 // 项目的入口文件，里边包括项目的主模块和监听端口号
```

![](https://img-blog.csdnimg.cn/img_convert/63970868f01a8114467ef10287064558.png)

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

#### NestJs 基础学习

** 核心梳理： **

1.  `/controllers`目录：存放控制器文件，每个控制器对应一组路由和请求处理方法。控制器处理来自客户端的 HTTP 请求，并返回相应的响应。
2.  `/modules`目录：存放模块文件，每个模块代表应用程序的一个功能模块或组件。模块是 Nest.js 应用程序的基本构建块，用于组织和管理相关的控制器、服务和其他组件。
3.  `/services`目录：存放服务文件，服务是一种可注入的类，用于处理业务逻辑、数据访问和其他与控制器无关的功能。服务负责处理控制器的业务逻辑，通常会被控制器注入使用。
4.  `main.ts`文件：应用程序的入口文件，通常用于创建 Nest.js 应用实例并启动服务器。
5.  `app.module.ts`文件：根模块文件，用于定义应用程序的根模块。根模块负责引入和配置其他模块、控制器、服务等组件。

##### 代码生成器

![](https://img-blog.csdnimg.cn/img_convert/767bbde65f599606340549d85fd1a40a.png)

在一个项目的生命周期中，当我们新增特性的时候，我们通常需要在应用中添加新的资源。这些资源通常需要我们在每次新增资源的时候进行一些重复操作。

@nestjs/cli 是 NestJS 官方提供的一个非常好用的脚手架工具。执行下面的命令，看下 @nestjs/cli 为开发者提供了哪些好用的命令。

想象一下真实世界中的场景，我们需要通过两个 CRUD 的终端暴露 User 和 Product 两个实体。参考最佳实践，我们为每个实体进行以下操作。

*   生成一个模块 (nest g mo) 来组织代码，使其保持清晰的界限（将相关模块分组）
*   生成一个控制器 (nest g co) 来定义 CRUD 路径（或者 GraphQL 应用的查询和变更）
*   生成一个服务 (nest g s) 来表示 / 隔离业务逻辑
*   生成一个实体类 / 接口来代表资源数据类型
*   生成数据转换对象（或者 GraphQL 应用输入）来决定数据如何通过网络传输
*   帮忙命令 （nest -h） 可查看 各种使用 方法
*   nest g resource user 生成项目级别, user 代表文件夹名
*   nest g controller 文件名 --no-spec

很多步骤！  
为了加速执行重复步骤，Nest CLI 提供了一个生成器（schematic(原理)）可以自动生成所有的模板文件以减少上述步骤，同时让开发者感觉更易用。  
该 schematic 支持生成 HTTP 控制器，微服务控制器，[GraphQL](https://so.csdn.net/so/search?q=GraphQL&spm=1001.2101.3001.7020) 处理器（代码优先或者原理优先），以及 WebSocket 网关等。

![](https://img-blog.csdnimg.cn/img_convert/5d6324a66c193f97497dc88489f4c5de.png)

*   停止生成

如果你不想生成测试文件, 可以在 nest-cli.json 中配置

```
"generateOptions": {
    "spec": false
  }
```

##### 常用装饰器使用

当查看以上装饰器应用于特定对象时，我们可以整理成如下表格：

<table><thead><tr><th>装饰器</th><th>特定对象</th><th>备注</th></tr></thead><tbody><tr><td>@Request()</td><td>req</td><td>从请求对象中提取数据</td></tr><tr><td>@Response()</td><td>res</td><td>原生的响应对象</td></tr><tr><td>@Res()</td><td>res</td><td>简写形式，用于注入响应对象</td></tr><tr><td>@Next()</td><td>next</td><td>下一个中间件函数</td></tr><tr><td>@Session()</td><td>req.session</td><td>与会话相关的数据</td></tr><tr><td><a href="/key" rel="nofollow">@Param(key)</a></td><td>req.params</td><td>路由参数中提取指定键的数据</td></tr><tr><td><a href="/key" rel="nofollow">@Body(key)</a></td><td>req.body</td><td>请求体中提取指定键的数据</td></tr><tr><td><a href="/key" rel="nofollow">@Query(key)</a></td><td>req.query</td><td>查询参数中提取指定键的数据</td></tr><tr><td><a href="/name" rel="nofollow">@Headers(name)</a></td><td>req.headers</td><td>请求头中提取指定名称的数据</td></tr><tr><td>@Ip()</td><td>req.ip</td><td>请求的 IP 地址</td></tr><tr><td>@HostParam()</td><td>req.hosts</td><td>主机名参数</td></tr></tbody></table>

路由装饰器（Route decorators）：

```
import { Controller, Get, Post, Delete, Patch } from '@nestjs/common';

@Controller('example')
export class ExampleController {
  @Get()
  findAll(): string {
    return 'Handle GET request';
  }

  @Post()
  create(): string {
    return 'Handle POST request';
  }

  @Delete()
  remove(): string {
    return 'Handle DELETE request';
  }

  @Patch()
  update(): string {
    return 'Handle PATCH request';
  }
}
```

请求体装饰器（Request body decorators）:

```
import { Controller, Post, Body } from '@nestjs/common';

@Controller('example')
export class ExampleController {
  @Post()
  create(@Body() data: any): string {
    // 处理来自请求体的数据
    console.log(data);
    return 'Handle POST request';
  }
}
```

使用 @Res() 注解时，可以访问响应对象的各种属性和方法。以下是一些常见的响应对象的方法和属性：

*   res.status(code: number)：设置响应的 HTTP 状态码。
*   res.header(key: string, value: string | string[])：设置响应头。
*   res.cookie(name: string, value: any, options?: cookie.CookieSerializeOptions)：设置 Cookie。
*   res.clearCookie(name: string, options?: cookie.CookieSerializeOptions)：清除指定的 Cookie。
*   res.send(body: any)：发送响应正文。
*   res.json(body: any)：发送 JSON 格式的响应正文。
*   res.redirect(url: string)：进行重定向。

```
import { Controller, Get, Query } from '@nestjs/common';

@Controller('example')
export class ExampleController {
  @Get()
  findAll(@Query() query: any): string {
    // 处理查询参数
    console.log(query);
    return 'Handle GET request';
  }
}
```

```
import { Controller, Get, Param } from '@nestjs/common';

@Controller('example')
export class ExampleController {
  @Get(':id')
  findOne(@Param('id') id: string): string {
    // 处理路由参数
    console.log(id);
    return 'Handle GET request';
  }
}
```

响应装饰器（Response decorators）：

```
import { Controller, Get, Res } from '@nestjs/common';
import { Response } from 'express';

@Controller('example')
export class ExampleController {
  @Get()
  findAll(@Res() res: Response): void {
    // 返回响应
    res.send('Handle GET request');
  }
}
```

状态码装饰器（Status code decorators）：

```
import { Controller, Get, HttpCode } from '@nestjs/common';

@Controller('example')
export class ExampleController {
  @Get()
  @HttpCode(201)
  findAll(): void {
    // 返回状态码为 201
  }
}
```

这些示例将帮助你理解如何使用这些装饰器来处理请求和响应，以及如何从请求中提取数据。记住，在使用这些装饰器之前，你需要安装并导入 `@nestjs/common` 模块中相应的装饰器和类。

```
@Get('world')
  getExample(@Req() request: Request): string {
    // 使用 request 对象执行任何必要的操作
    console.log(request.headers);
    console.log(request.query);
    console.log(request.body);
    return 'Hello World11!';
  }
```

```
@Controller('example')
export class ExampleController {
  @Get('example-path')
  getExampleData(
    @Query('param1') param1: string,
    @Query('param2') param2: number,
    @Headers('authorization') authorization: string,
  ): string {
    // 进行一些处理逻辑...
    return `Received query parameters: param1=${param1}, param2=${param2}, authorization header=${authorization}`;
  }
}
```

// controller -> busingessmodule --> module --> NestFactory

##### Nest JS 测试

在 NestJS 中，你可以使用 Jest 进行单元测试和集成测试。要执行测试文件，你可以按照以下步骤进行操作：

1.  安装 Jest：  
    首先，确保你已经在项目中安装了 Jest（通常作为开发依赖项）。如果没有安装，可以使用以下命令安装 Jest：

```
npm install --save-dev jest @types/jest
```

或者

```
yarn add --dev jest @types/jest
```

2.  创建测试文件：  
    创建一个与要测试的文件对应的测试文件。通常测试文件的命名规范是 `*.spec.ts` 或 `*.test.ts`。
3.  编写测试：  
    在测试文件中编写测试代码，包括测试用例、断言和期望的结果。你可以使用 Jest 提供的各种功能来编写测试代码，例如 Mock、Matchers 等。
4.  运行测试：  
    一旦编写了测试代码，你可以使用以下命令来运行测试：

```
npm run test
```

或者

```
yarn test
```

这将启动 Jest 并运行你的测试文件，然后显示测试结果。

在 NestJS 中，通常你的控制器、服务、拦截器等组件可以进行单元测试，你可以对它们的功能进行测试，确保其行为符合预期。

除了上述提到的命令之外，你也可以通过配置 `package.json` 中的 `scripts` 属性来进行更多自定义的测试命令。希望这些步骤可以帮助你在 NestJS 中执行测试文件。

#### NextJs 增删改查

##### 测试数据

```
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

##### 安装 所需依赖

*   安装 连接 MYSQL 需要 ORM 框架映射依赖

```
yarn add @nestjs/typeorm typeorm mysql
```

##### 实现 CURD

*   修改 app.module.ts

> 补充 数据库连接信息，共享模块

```
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { UsersModule } from './user/users.module';
import { TypeOrmModule } from '@nestjs/typeorm';

@Module({
  imports: [
    TypeOrmModule.forRoot({ // 连接数据库
      type: 'mysql', // 数据库类型
      host: 'localhost', // 数据库ip地址
      port: 3306, // 端口
      username: 'root', // 登录名
      password: 'root', // 密码
      database: 'auth', // 数据库名称
      entities: [__dirname + '/**/*.entity{.ts,.js}'], // 扫描本项目中.entity.ts或者.entity.js的文件
      synchronize: true, // 定义数据库表结构与实体类字段同步(这里一旦数据库少了字段就会自动加入,根据需要来使用)
    }),
    UsersModule // 加载子模块
  ],
  controllers: [AppController],
  providers: [AppService],
})
  export class AppModule {}
```

*   创建 实体 ORM 映射关系

```
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

*   创建业务 Module

> 创建业务 模块， 一个模块代表一个功能， 下面我们实现 模块的 请求 和业务

```
import { Module } from '@nestjs/common';
import { UsersController } from './users.controller';
import { UsersService } from './users.service';
import { TypeOrmModule } from '@nestjs/typeorm';
import { User } from './user.entity';
 
@Module({
  imports:[TypeOrmModule.forFeature([User])], // 导入并注册实体
  controllers: [UsersController],
  providers: [UsersService]
})
export class UsersModule {}
```

*   创建业务 Service

```
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository } from 'typeorm';
import { User } from './user.entity';
 
@Injectable()
export class UsersService {
    // 使用InjectRepository装饰器并引入Repository即可使用typeorm的操作
    constructor(@InjectRepository(User)private readonly usersRepository: Repository<User>,) { }

    // 获取所有用户数据列表(usersRepository.query()方法属于typeoram)
    async getList(): Promise<User[]> {
        return await this.usersRepository.find();
      }
    
    // 通过id查询用户
    async getUserById(id): Promise<User> {
        return await this.usersRepository.findOne({where:{id: id}});
    }
    // 新增用户
    async addUser(body): Promise<User> {
        return await this.usersRepository.save(body);
      }
    // 更新用户
    async updateUser(user): Promise<string> {
        await this.usersRepository.update({ id: user.id }, user);
        return '更新成功';
      }

    // 删除用户
    async deleteUser(params): Promise<object> {
        const res = await this.usersRepository.delete({ id: params.id });
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

*   创建 路由对应的控制器

```
import { Controller, Get, Post, Request, Query, Body, Param } from '@nestjs/common';
import { UsersService } from './users.service';
import { User } from './user.entity';
 
@Controller('user')
export class UsersController {
    // this.usersService = new UsersService() 等价于 constructor 方式
    constructor(private usersService: UsersService){}
    // 通过数据库查询用户list
    @Get('list')
    getList(): Promise<User[]> {
        return this.usersService.getList();
    }
     // 通过id查询用户
     @Get('getUserById')
     async getUserById(@Query('id') id: string): Promise<User> {
       const userId: number = parseInt(id);
       return this.usersService.getUserById(userId);
     }
     // 增加用户
     @Post('addUser')
     addUser(@Body() body): Promise<User> {
         return this.usersService.addUser(body);
     }
     // 更新用户
     @Post('updateUser')
     updateUser(@Body() body): Promise<string> {
         return this.usersService.updateUser(body);
     }
     // 删除用户
     @Post('deleteUser')
     delUser(@Body() body): Promise<object> {
         return this.usersService.deleteUser(body);
     }
    
}
```

##### 安装 VSCode 插件测试

*   使用 VsCode 插件 REST Client

![](https://img-blog.csdnimg.cn/img_convert/e4ce8976178f2f91c351de538a790d30.png)

项目根目录创建 RESTClient 目录，demo.http 文件

![](https://img-blog.csdnimg.cn/img_convert/8193bd5b35df1bf821d7c2eea5ff318f.png)

在项目目录下新建 http 文件

通过 # 区分不同请求

```
GET http://localhost:3000/user/list

###

GET www.baidu.com HTTP/1.1
```

![](https://img-blog.csdnimg.cn/img_convert/d56a703e2ad0fd2ccf0dfb0e6964282f.png)

##### 补充分页查询

*   user/users.controller.ts

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

*   user/users.service.ts

```
async findAll(page: number = 1, limit: number = 10): Promise<[User[], number]> {
        const [users, total] = await this.usersRepository.findAndCount({
          skip: (page - 1) * limit,
          take: limit,
        });
        return [users, total];
      }
```

##### 条件查询

```
@Get('findByConditions')
    async findByConditions(@Query('name') conditions): Promise<User[]> {
        return this.usersService.findByConditions(conditions);
}
```

在使用 TypeORM 中的 `FindConditions` 类型时，你可以按照以下方式进行操作：

1.  创建查询条件对象的实例，并指定条件：

```
const conditions: FindConditions<User> = {
  name: 'Alice',
  age: 25,
};
```

在这个示例中，`FindConditions` 被指定为 `User` 类型，意味着条件对象中的属性必须符合 `User` 实体类的字段。

2.  将条件对象传递给 `find` 方法来执行查询：

```
const users = await this.usersRepository.find(conditions);
```

在这个示例中，`conditions` 对象被传递给 TypeORM 的 `find` 方法，以根据指定的条件查询用户数据。

使用 `FindConditions` 类型可以使你能够更加类型安全地构建查询条件，并且在编译期间就能够发现潜在的错误。这有助于提高代码的可靠性和可维护性。

若你想要使用 Nest.js 和 TypeORM 完成条件查询，可以使用 TypeORM 提供的 Query Builder 和 Where 语句来构建复杂的查询条件。

下面是一个使用 Where 语句构建条件查询的示例：

```
import { Injectable } from '@nestjs/common';
import { InjectRepository } from '@nestjs/typeorm';
import { Repository, WhereExpression } from 'typeorm';
import { User } from './user.entity';

@Injectable()
export class UsersService {
  constructor(@InjectRepository(User) private readonly usersRepository: Repository<User>) {}

  async findByConditions(conditions: Partial<User>): Promise<User[]> {
    return this.usersRepository.find({
      where: (qb: WhereExpression) => {
        if (conditions.name) {
          qb.andWhere('user.name = :name', { name: conditions.name });
        }
        if (conditions.age) {
          qb.andWhere('user.age >= :age', { age: conditions.age });
        }
        // Add more conditions as needed
      },
    });
  }
}
```

在这个示例中，`findByConditions` 方法接收一个 `conditions` 参数，它是一个 `Partial<User>` 类型的对象，其中包含可能的查询条件。使用 `where` 方法来构建查询条件，根据传入的条件值动态地生成 SQL 查询语句。

你可以根据你的需求向 `where` 方法中添加更多的条件。例如，你可以使用 `andWhere` 方法来添加更多的 AND 条件，使用 `orWhere` 方法添加 OR 条件。

在查询中，`user` 是表的别名，是由 TypeORM 自动生成的，指向 `User` 实体。

这里的示例只是一个基本的条件查询示例，你可以根据具体需求添加更多的条件来构建复杂的查询逻辑。

##### GraphQL 接口开发实现

*   [https://baike.baidu.com/item/rest/6330506?fromtitle=RESTful&fromid=4406165&fr=aladdin](https://baike.baidu.com/item/rest/6330506?fromtitle=RESTful&fromid=4406165&fr=aladdin)

![](https://img-blog.csdnimg.cn/img_convert/c5e41a1098d45e92b1d6cd097e2a271f.png)

![](https://img-blog.csdnimg.cn/img_convert/84cee58606fd3140c5be7b23e174754c.png)

*   Restful API

![](https://img-blog.csdnimg.cn/img_convert/e0234f0212c99a9c1491e5a3ad11cbc3.png)

*   GraphQL

![](https://img-blog.csdnimg.cn/img_convert/74142ccf4e6eeecbab74d2d0642c0a2a.png)

REST API 构建在请求方法（method）和端点（endpoint）之间的连接上，而 GraphQL API 被设计为只通过一个端点，即 /graphql，始终使用 POST 请求进行查询，其集中的 API 如 [http://localhost:3000/graphql](http://localhost:3000/graphql)，所有的操作都通过这个接口来执行，这会在后面的操作中在展示到。

*   一句话理解

简单例子，后端使用了 GraphQL 之后，数据库查出来 A,B,C,D 四个字段，客户端需要数据的时候，你可以随意使用这四个字段的各种组合，只要 A，C 字段还是只要 A，C，D 字段等等，不再需要和服务端交流。

###### graphQL 介绍

GraphQL 是一种用于 API 的查询语言，是由 Facebook 公司于 2012 年开发的一种新型的 API 架构方式。GraphQL 旨在提高客户端应用程序的数据获取效率，通过定义数据的类型和结构使得 API 更加灵活和可扩展。与传统的 API 不同，GraphQL 允许客户端指定需要哪些数据，从而减少了不必要的数据传输和处理，提高了 API 的效率和可用性。  
GraphQL 的核心思想是用一个 API 来代替多个 API，通过 GraphQL API，客户端可以获取所需的所有数据，而不需要调用多个 API 或者进行多次请求。GraphQL 还支持实时数据查询和订阅，使得客户端可以实时获取数据更新，从而更好地支持实时应用程序。

> `Nest js 网址` ： [https://nestjs.bootcss.com/graphql/quick-start.html](https://nestjs.bootcss.com/graphql/quick-start.html)  
> `graphQL官方地址`： [https://graphql.org/](https://graphql.org/)

Graph” 指的是数据以类似图形的结构表示和连接。在 GraphQL 中，数据表示为具有节点和边的图形，允许不同数据实体之间的灵活关系。  
“QL” 代表 “查询语言”，因为 GraphQL 提供了一种精确和可控的查询或请求数据的语言。  
示例：书和作者的关系可以用图来表示，可以很容易地使用 GraphQL 进行查询：

![](https://img-blog.csdnimg.cn/img_convert/16314e063e918d04795721c13819efb5.png)

![](https://img-blog.csdnimg.cn/img_convert/83b51f5b673051fdabafd0d2787af686.png)

###### 何时使用 grphQL

GraphQL 适用于处理复杂或经常变化的数据需求，因为它可以将数据请求的控制权交给客户端，让客户端在任何时间请求任何数据。这让在每次 API 变更迭代或从这些 API 请求的数据发生变化时更容易进行更新。与 REST API 相比，GraphQL 允许客户端精确指定所需数据的结构和字段，从而避免了获取过度或获取不足的问题。因此，GraphQL 可以提高数据传输的精确性和效率，使应用程序更加灵活和可扩展。  
如果应用程序需要从多个来源聚合数据，GraphQL 可以帮助把这些来源统一到单个 API 中。它提供了一个抽象层，可从各种服务中获取和组合数据，使数据的获取和整合更加简单和高效。  
当应用程序需要实时更新和订阅时，GraphQL 提供内置功能。这些功能允许客户端订阅特定数据的变化，并在数据更改时实时推送通知，从而提高应用程序的实时性和响应性。  
总之，如果您需要更好地控制和定制 API 响应，并希望有效地处理复杂或不断变化的数据需求，那么 GraphQL 是一个非常有用的工具。

###### 操作实例

*   安装 grphQL

Apollo 是一个开源的 JavaScript 库，用于构建基于 GraphQL 的客户端应用程序。它提供了一组工具和功能，帮助开发人员在前端应用中轻松集成和管理 GraphQL API。  
主要功能包括：

1.  **查询和变更管理**：Apollo 提供了一套强大的工具，用于管理应用中的 GraphQL 查询、变更和订阅。
2.  **缓存管理**：Apollo 维护一个本地缓存，用于存储从 GraphQL API 中获取的数据。这样，当下次需要相同数据时，可以直接从缓存中获取，提高了应用的性能和响应速度。
3.  **数据更新和响应处理**：Apollo 可以自动更新 UI 组件中的数据，同时提供了一些功能来处理后端数据的变更和响应。
4.  **查询优化**：Apollo 的缓存机制和数据更新处理功能可以优化 GraphQL 查询，避免重复请求和传输不必要的数据。
5.  **错误处理和状态管理**：Apollo 提供了错误处理和状态管理的功能，帮助开发人员更好地处理和呈现 GraphQL API 返回的错误信息。

Apollo 提供了适用于不同 JavaScript 框架的客户端库，例如 React、Angular、Vue 等。它使开发人员能够轻松地在前端应用程序中使用 GraphQL，并提供了许多工具和便利功能，简化了与 GraphQL API 的交互和管理。  
总的来说，Apollo 是一个功能强大的 GraphQL 客户端库

```
npm i @nestjs/graphql @nestjs/apollo @apollo/server graphql
```

*   在根目录进行配置

```
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { GraphQLModule } from '@nestjs/graphql';
import { ApolloDriverConfig,ApolloDriver } from '@nestjs/apollo'
import { join } from 'path';
import { UsersModule } from './users/users.module';

@Module({
  imports: [
    GraphQLModule.forRoot<ApolloDriverConfig>({
      driver: ApolloDriver,
      autoSchemaFile: join(process.cwd(), 'src/schema.gql'),
    }),
    UsersModule,

  ],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

*   快速生成 CRUD

```
nest g res
```

*   修改测试请求

```
import { Resolver, Query, Mutation, Args, Int } from '@nestjs/graphql';
import { UsersService } from './users.service';
import { User } from './entities/user.entity';
import { CreateUserInput } from './dto/create-user.input';
import { UpdateUserInput } from './dto/update-user.input';

@Resolver(() => User)
export class UsersResolver {
  constructor(private readonly usersService: UsersService) {}

  @Mutation(() => User)
  createUser(@Args('createUserInput') createUserInput: CreateUserInput) {
    return createUserInput;
  }

  // 根据返回类型进行输入
  @Query(() => [User], { name: 'userList',description:'用户列表'})
  findAll() {
    return this.usersService.findAll();
  }

  @Query(() => User, { name: 'user' })
  findOne(@Args('id', { type: () => Int }) id: number) {
    return this.usersService.findOne(id);
  }

  @Mutation(() => User)
  updateUser(@Args('updateUserInput') updateUserInput: UpdateUserInput) {
    return updateUserInput;
  }

  @Mutation(() => Boolean)
  removeUser(@Args('id', { type: () => Int }) id: number) {
    return this.usersService.remove(id);
  }
}
```

*   业务层

```
import { Injectable } from '@nestjs/common';
import { CreateUserInput } from './dto/create-user.input';
import { UpdateUserInput } from './dto/update-user.input';
import { User } from './entities/user.entity';

@Injectable()
export class UsersService {
  create(createUserInput: CreateUserInput) {
    return new User;
  }

  findAll() {
    return [{exampleField:1},{exampleField:2},{exampleField:3}];
  }

  findOne(id: number) {
    return {
      exampleField:id
    };
  }

  update(id: number, updateUserInput: UpdateUserInput) {
    return `This action updates a #${id} user`;
  }

  remove(id: number) {
    return true
  }
}
```

*   测试 步骤：

```
query {
  findAllstudent {
    exampleField
  }
}
```

*   查询

```
# Write your query or mutation here
{
  
  
  #根据ID 查询  实际调用name函数名
  user(id:2){
    exampleField
  }
  
  #查询全部
  userList{
    exampleField
  }

  
}
```

*   新增和修改

```
mutation{
  # 删除
  removeUser(id:1)
  
  # 修改
  updateUser(updateUserInput: { exampleField: 1, id: 1 }) {
    exampleField
  }
  
  # 新增
   createUser(createUserInput: { exampleField: 1 }) {
    exampleField
  
}
  
}
```

```
mutation{
  
  
  # 增删改
  createStudent(
    # 参数对象的返回 
    createStudentInput:{exampleField:1}
  ){
    # 大括号是方法的返回
    exampleField
  },
  
  
updateStudent(
    # 参数对象的返回 
    updateStudentInput:{exampleField:1,id:1}
  ){
    # 大括号是方法的返回
    exampleField
  }
  
  
  
}
```

*   对应的 schema 结构

```
type User {
  # 示例属性
  exampleField: Int!
}

type Query {
  # 用户列表
  userList: [User!]!
  user(id: Int!): User!
}

type Mutation {
  createUser(createUserInput: CreateUserInput!): User!
  updateUser(updateUserInput: UpdateUserInput!): User!
  removeUser(id: Int!): Boolean!
}

input CreateUserInput {
  # Example field (placeholder)
  exampleField: Int!
}

input UpdateUserInput {
  # Example field (placeholder)
  exampleField: Int
  id: Int!
}
```

#### NestJs 中间件

![](https://img-blog.csdnimg.cn/img_convert/8ec9e106d69505faf027947f44b74531.png)

##### AOP 概念

在介绍 AOP 架构之前我们需要先了解一下 NestJS 对一个请求的处理过程。在 NestJS 中, 一个请求首先会先经过控制器（Controller）, 然后 Controller 调用服务 (Service)中的方法, 在 Service 中可能还会进行数据库的访问 (Repository) 等操作, 最后返回结果。但是如果我们想在这个过程中加入一些通用逻辑, 比如打印日志, 权限控制等该如何做呢? 这时候就需要用到 AOP(Aspect-Oriented Programming，面向切面编程)了, 它允许开发者通过定义切面（Aspects）来对应用程序的各个部分添加横切关注点（Cross-Cutting Concerns）。横切关注点是那些不属于应用程序核心业务逻辑，但在整个应用程序中多处重复出现的功能或行为。这样可以让我们在不侵入业务逻辑的情况下来加入一些通用逻辑。

##### Middleware(中间件)

Middleware is a function which is called **before** the route handler. Middleware functions have access to the [request](https://link.juejin.cn?target=https%3A%2F%2Fexpressjs.com%2Fen%2F4x%2Fapi.html%23req) and [response](https://link.juejin.cn?target=https%3A%2F%2Fexpressjs.com%2Fen%2F4x%2Fapi.html%23res) objects, and the next() middleware function in the application’s request-response cycle. The **next** middleware function is commonly denoted by a variable named next.  
![](https://img-blog.csdnimg.cn/img_convert/9e0b219548bd00ae983577f64fca4526.webp?x-oss-process=image/format,png)  
**中间件**，学过 Express 和 Koa 的同学，对中间件这个概念应该很熟悉了。看官方说明，中间件可以拿到 Request、Response 对象及 next 函数，其实 nest 默认和 express 的中间件是等效的  
再来回忆一下中间件的功能特性：

*   可以执行任意的代码
*   对 request 和 response 对象进行改造
*   结束 request-response 循环
*   通过 next() 调用下一个中间件
*   如果当前中间件没有结束当前 request-response 循环，必须调用 next() 函数，否则请求会处于挂起状态，阻塞整个应用

然后再生成一个中间件

```
nest g mi test --no-spec --flat
```

此时我们的根目录多了一个 test.middleware.ts 文件, 因为我们的 NestJS 是基于 Express 的, 所以可以将 req 和 res 的类型设置成 Express 中的类型

```
import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response } from 'express';
@Injectable()
export class TestMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: () => void) {
    console.log('请求进入前');
    next();
    console.log('请求离开后');
  }
}
```

其中 next() 就是执行下一个中间件, 而 next() 后面的代码则是请求结束后才会执行的。那么我们如何使用这个中间件呢?  
想要使用中间件需要到 app.module.ts 进行注册

```
import { MiddlewareConsumer, Module, NestModule } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';
import { TestMiddleware } from './test.middleware';
@Module({
  imports: [],
  controllers: [AppController],
  providers: [AppService],
})
  export class AppModule implements NestModule {
    configure(consumer: MiddlewareConsumer) {
      consumer.apply(TestMiddleware).forRoutes('*');
    }
  }
```

我们需要实现一个 NestModule 的类然后通过其中的 configure 方法进行使用。启动项目访问一下 http://localhost:3000 / 看一下控制台的打印![](https://img-blog.csdnimg.cn/img_convert/9c6fae0723a3f77b881bb2c3aec62350.png)

**注意，configure 方法可以是异步的，如果里面有需要异步处理的操作，可以使用 async/await 来等待操作完成再往下进行**

##### MiddlewareConsumer

*   实现链式调用
*   apply 可以放置多个 middleware
*   forRoutes 可以使用单个 string 路径，多个 string 路径，RouteInfo 对象，单个 Controller，多个 Controller

```
@Module({
  imports: [],
})
export class AppModule implements NestModule {
  configure(consumer: MiddlewareConsumer) {
    consumer
      .apply(LoggerMiddleware, xxxMiddleware,...)
      .forRoutes(CatsController,UserController,...);
  }
}
```

*   exclude 可以排除不使用中间件的路径

```
consumer
  .apply(LoggerMiddleware)
  .exclude(
    { path: 'cats', method: RequestMethod.GET },
    { path: 'cats', method: RequestMethod.POST },
    'cats/(.*)',
  )
  .forRoutes(CatsController);
```

在 Nest.js 中，你可以使用全局中间件和局部中间件来处理请求和响应。全局中间件将对应用程序中的每个路由生效，而局部中间件只对特定的路由或模块生效。

以下是全局中间件和局部中间件的使用示例：

1.  ** 全局中间件：  
    ** 全局中间件会在应用程序的每个请求处理之前执行，可以使用`app.use()`方法在根模块中注册全局中间件。

```
// logger.middleware.ts

import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response } from 'express';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: Function) {
    console.log('Request...');
    next();
  }
}
```

```
// main.ts

import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { LoggerMiddleware } from './logger.middleware';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  
  app.use(LoggerMiddleware);
  
  await app.listen(3000);
}
bootstrap();
```

2.  **局部中间件：**  
    局部中间件只对特定的路由或模块生效，可以通过在路由处理程序上使用`@UseMiddleware()`装饰器或在模块中使用`configure()`方法来注册局部中间件。

```
// logger.middleware.ts

import { Injectable, NestMiddleware } from '@nestjs/common';
import { Request, Response } from 'express';

@Injectable()
export class LoggerMiddleware implements NestMiddleware {
  use(req: Request, res: Response, next: Function) {
    console.log('Request...');
    next();
  }
}
```

```
// cats.controller.ts

import { Controller, Get } from '@nestjs/common';
import { UseMiddleware } from '@nestjs/common';
import { LoggerMiddleware } from './logger.middleware';

@Controller('cats')
@UseMiddleware(LoggerMiddleware)
export class CatsController {
  @Get()
  findAll(): string[] {
    return ['Cat 1', 'Cat 2'];
  }
}
```

@UseGuards 或 @UseFilters 等装饰器来应用中间件。

```
// app.module.ts

import { Module } from '@nestjs/common';
import { CatsModule } from './cats/cats.module';

@Module({
  imports: [CatsModule]
})
export class AppModule {}
```

在上面的示例中，`LoggerMiddleware`被用作局部中间件，它只会应用于`CatsController`的路由处理程序。这意味着每次访问`/cats`路径时，都会执行`LoggerMiddleware`中间件的逻辑。

全局中间件和局部中间件的使用场景取决于具体的需求。全局中间件通常用于实现通用的请求处理逻辑，如日志记录和身份验证。而局部中间件则可以更精确地定义中间件应用的位置和范围，适用于特定的路由或模块。

通过选择合适的中间件注册方式，可以更加灵活地处理请求和响应，并增强 Nest.js 应用程序的功能和性能。请根据你的实际需求选择适合的中间件注册方式。

3.  **第三方中间件**

在 Nest.js 中，你可以轻松地使用第三方中间件来处理请求和响应。以下是一个使用第三方中间件的示例，以及如何在 Nest.js 中使用它：

1.  **安装第三方中间件：  
    在使用第三方中间件之前，需要使用 npm 或 yarn 等包管理工具安装它。以**`**helmet**`**中间件为例，可以运行以下命令安装它：**

`helmet`是一个安全中间件，用于增强 Express 或 Connect 应用程序的安全性。它帮助解决了许多常见的 Web 应用程序安全漏洞，如跨站点脚本攻击 (XSS)、点击劫持、HTTP 头部设置不当等。

`helmet`中间件提供了一组对安全性有益的 HTTP 头部设置，例如适当的内容安全策略、XSS 过滤、CSRF 保护等。通过将这些头部设置在服务器响应中发送给客户端，可以提供一定程度的保护，防止常见的攻击。

在 Nest.js 中，可以使用第三方中间件库`nest-middlewares`提供的`HelmetMiddleware`来使用`helmet`中间件。在应用程序中将`HelmetMiddleware`应用到所有路由时，会自动添加并设置`helmet`中间件所需的安全头部。

`helmet`中间件可以大大简化安全性的处理，并提供一些默认的安全设置。然而，对于更严格的安全需求，你可能需要更深入地了解和配置具体的安全措施。

请注意，虽然`helmet`中间件能够提供一定程度的安全保护，但应该将其视为安全加固措施的一部分，而不是唯一的安全措施。仍然建议结合其他安全措施和最佳实践来确保应用程序的安全性。

**在上面的示例中，我们使用了**`**nest-middlewares**`**库中的**`**HelmetMiddleware**`**中间件。通过导入**`**HelmetMiddleware**`**模块并将其应用到**`**forRoutes('*')**`**，我们可以将**`**helmet**`**中间件应用于所有的路由。**

**请注意，不同的第三方中间件可能需要不同的配置选项。你可以查看相应中间件的文档以获取更多详细信息，并根据需要进行适当的配置。**

**通过使用第三方中间件，你可以轻松地增强你的 Nest.js 应用程序的功能和安全性。可以根据你的需求选择适合的第三方中间件，并按照上述示例进行使用和配置。同时，确保在使用第三方中间件之前阅读它们的文档以获取更多详细信息。**

很抱歉，我的回答中提到了错误的库。在 Nest.js 中使用 Helmet 中间件时，你可以直接安装和使用 `helmet` 库而不是 `@nest-middlewares/helmet`。

**可以使用以下命令来安装 **`**helmet**`**：**

```
npm install helmet
```

**然后在你的 Nest.js 应用程序中使用 **`**helmet**`** 中间件的代码示例如下：**

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  app.use(helmet());
  await app.listen(3000);
}
bootstrap();
```

**在这个示例中，我们首先通过 **`**import helmet from 'helmet';**`** 导入 **`**helmet**`** 中间件。然后，我们在应用程序实例上使用 **`**app.use(helmet());**`** 将 **`**helmet**`** 中间件应用到所有路由上。**

**请注意，如果你使用的是 TypeScript，需要确保 **`**esModuleInterop**`** 设置为 **`**true**`**，并确保你的项目中已经正确配置了 TypeScript。**

很抱歉，我的回答中提到了错误的库。在 Nest.js 中使用 Helmet 中间件时，你可以直接安装和使用 `helmet` 库而不是 `@nest-middlewares/helmet`。

*   全局使用示例

然后在你的 Nest.js 应用程序中使用 `helmet` 中间件的代码示例如下：

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import helmet from 'helmet';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  app.use(helmet());
  await app.listen(3000);
}
bootstrap();
```

在这个示例中，我们首先通过 `import helmet from 'helmet';` 导入 `helmet` 中间件。然后，我们在应用程序实例上使用 `app.use(helmet());` 将 `helmet` 中间件应用到所有路由上。

请注意，如果你使用的是 TypeScript，需要确保 `esModuleInterop` 设置为 `true`，并确保你的项目中已经正确配置了 TypeScript。

#### NestJs 异常处理

![](https://img-blog.csdnimg.cn/img_convert/7578b145d7e9787ac1794e15253eb418.png)

##### 异常过滤器

[Nest](https://so.csdn.net/so/search?q=Nest&spm=1001.2101.3001.7020) 带有一个内置的**异常层**，负责处理应用程序中所有未处理的异常。当应用程序代码未处理异常时，该层会捕获该异常，然后自动发送适当的用户友好响应。

```
nest g f http-exception --no-spec --flat
```

通过使用 Nest CLI 提供的快捷命令，你可以方便地生成异常类，并快速开始在你的应用程序中使用它们。这样，你可以避免手动创建异常类的过程，并节省时间。

在 Nest.js 中，异常过滤器是一种处理应用程序中抛出的异常的机制。异常过滤器允许我们捕获并处理应用程序中的异步代码中出现的异常。使用异常过滤器，我们可以自定义如何处理异常，例如向客户端返回特定的错误响应。

要使用异常过滤器，可以按照以下步骤操作：

1.  创建一个自定义的异常过滤器类。这个类应该实现 `ExceptionFilter` 接口。

```
import { Catch, ArgumentsHost } from '@nestjs/common';
import { BaseExceptionFilter } from '@nestjs/core';

@Catch()
export class CustomExceptionFilter extends BaseExceptionFilter {
  catch(exception: any, host: ArgumentsHost) {
    // 自定义异常处理逻辑
    console.error('发生异常', exception);
    super.catch(exception, host);
  }
}
```

在上面的例子中，我们创建了一个名为 `CustomExceptionFilter` 的自定义异常过滤器类。我们覆盖了 `catch` 方法，可以在其中定义我们自己的异常处理逻辑。

2.  假设你想通过 Nest.js 提供的内置的 HTTPException 类捕获 HTTP 异常。你可以在 `catch` 方法中添加逻辑来处理 HTTP 异常。

```
import { Catch, ArgumentsHost } from '@nestjs/common';
import { BaseExceptionFilter, HttpException } from '@nestjs/core';
import { Response } from 'express';

@Catch(HttpException)
export class HttpExceptionFilter extends BaseExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const context = host.switchToHttp();
    const response = context.getResponse<Response>();
    const status = exception.getStatus();

    response.status(status).json({
      statusCode: status,
      message: exception.message,
    });
  }
}
```

*   最佳实践

```
nest g f http-exception --no-spec --flat
```

并将这个过滤器 http-exception.filter.ts 修改如下

```
import { ExceptionFilter, Catch, ArgumentsHost } from '@nestjs/common';
import { HttpException } from '@nestjs/common';

@Catch(HttpException)
  export class HttpExceptionFilter implements ExceptionFilter {
    catch(exception: HttpException, host: ArgumentsHost) {
      const ctx = host.switchToHttp(); // 获取请求上下文
      const response = ctx.getResponse(); // 获取 response 对象
      const request = ctx.getRequest(); // 获取 request 对象
      const status = exception.getStatus(); // 获取异常的状态码

      response.status(status).json({
        statusCode: status,
        timestamp: new Date().toISOString(),
        path: request.url,
      });
    }
  }
```

如果想要全局使用, 可以在 main.ts 中使用 app.useGlobalFilters 进行注册

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

import { HttpExceptionFilter } from './http-exception.filter';
async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  app.useGlobalFilters(new HttpExceptionFilter());
  await app.listen(3000);
}
bootstrap();
```

或者在 app.module 注入

```
import { Module } from '@nestjs/common';
import { APP_FILTER } from '@nestjs/core';
import { HttpExceptionFilter } from './http-exception.filter';
@Module({
  providers: [
    {
      provide: APP_FILTER,
      useClass: HttpExceptionFilter,
    },
  ],
})
  export class AppModule {}
```

这种方式适合在过滤器需要依赖注入的时候使用  
如果只想在单个控制器中使用, 可以使用 @UseFilters 装饰器

```
@Get('aa')
  @UseFilters(HttpExceptionFilter)
  aa(): string {
    throw new HttpException('这是一个400异常', 400);
    return 'aa';
  }
```

这里我们采用全局注册, 此时我们在抛出 HttpException 异常看下请求结果![](https://img-blog.csdnimg.cn/img_convert/903e0d58bb2a8d19d9fa65347ed64ff9.png)

可以看到已经是我们异常过滤器中 response.status(status).json 中传入的数据及格式了  
除了 http 异常状态码之外, 通常在开发中还会返回一些业务的异常, 对于这些异常的处理我们可以新建一个 custom.exception.ts, 当然命名大家可以随意

```
import { HttpException, HttpStatus } from '@nestjs/common';

export enum CustomErrorCode {
  USER_NOTEXIST = 10002, // 用户不存在
  USER_EXIST = 10003, //用户已存在
}
export class CustomException extends HttpException {
  private errorMessage: string;
  private errorCode: CustomErrorCode;

  constructor(
    errorMessage: string,
    errorCode: CustomErrorCode,
    statusCode: HttpStatus = HttpStatus.OK,
  ) {
    super(errorMessage, statusCode);
    this.errorMessage = errorMessage;
    this.errorCode = errorCode;
  }

  getErrorCode(): CustomErrorCode {
    return this.errorCode;
  }

  getErrorMessage(): string {
    return this.errorMessage;
  }
}
```

这里实现了一个 CustomException 类继承 HttpException 类, 接收三个参数: 错误信息, 业务异常码以及 http 错误码 (默认为 200, 一般业务异常 http 请求通常是正常的)。同时提供了获取错误码及错误信息的函数。同时导出了一个自定义错误码的枚举  
然后我们来到异常过滤器中 http-exception.filter.ts 做一些逻辑处理

```
import { ArgumentsHost, Catch, ExceptionFilter,HttpException,NotFoundException } from '@nestjs/common';
import { CustomException } from './custom.exception';

@Catch(HttpException)
export class HttpExceptionFilter<T> implements ExceptionFilter {
  catch(exception: HttpException, host: ArgumentsHost) {
    const ctx = host.switchToHttp(); // 获取请求上下文
    const response = ctx.getResponse(); // 获取 response 对象
    const request = ctx.getRequest(); // 获取 request 对象
    const status = exception.getStatus(); // 获取异常的状态码


      //判断是否为自定义类
      if (exception instanceof CustomException) {
        response.status(status).json({
          statusCode: status,
          message: exception.getErrorMessage(),
          timestamp: new Date().toISOString(),
          path: request.url,
          test:'自定义异常'
        });
        return;
      }


    response.status(status).json({
      statusCode: status,
      timestamp: new Date().toISOString(),
      path: request.url,
      message:'我是你自定义的异常'
    });
    
  }
}
```

这里通过判断是否是通过自定义异常抛出的错误来返回不同的结果, 然后我们在控制层抛出一个自定义错误看一下

```
import { Controller, Get, HttpException, UseFilters } from '@nestjs/common';
import { AppService } from './app.service';
import { CustomException, CustomErrorCode } from './custom.exception';
import { HttpExceptionFilter } from './http-exception.filter';
@Controller()
  export class AppController {
    constructor(private readonly appService: AppService) {}
    @Get('aa')
    @UseFilters(HttpExceptionFilter)
    aa(): string {
      throw new CustomException('姓名已存在', CustomErrorCode.USER_EXIST);
      return 'aa';
    }
  }
```

然后访问 / aa 接口会发现请求是成功的, 并且 statusCode 变成了我们期望的 10003

![](https://img-blog.csdnimg.cn/img_convert/b2bd0968a38d0f8ae5f03f7fce53ef9f.png)

#### Nestjs 拦截器

在 Nest.js 中，拦截器（Interceptors）是一种可用于在处理请求之前、之后或处理过程中干预和转换数据的强大机制。它们允许你在执行路由处理程序之前和之后，以及在异常抛出时对请求和响应对象进行操作。拦截器有以下几种作用

** 日志记录: ** 拦截器可以用于记录请求和响应数据，以便跟踪应用程序的活动、调试问题或分析性能。

** 验证和转换数据: ** 通过拦截器，你可以验证请求的有效性，转换请求数据或响应数据的格式，以适应特定的需求。

权限控制: 拦截器可以用于检查用户的权限、角色或其他访问控制要求，以确保只有有权限的用户可以访问特定的路由或资源。

异常处理: 拦截器可以用于捕获和处理异常，通过统一处理异常情况，你可以避免重复的错误处理逻辑，并提供一致的错误响应。

缓存: 拦截器可以用于实现缓存机制，将某些请求的响应缓存起来，提高系统的性能和响应时间。

使用拦截器，可以在整个请求 - 响应生命周期中执行各种操作, 例如:

在请求到达路由处理程序之前，对请求进行预处理或验证。  
在路由处理程序执行之前或之后，对请求和响应进行操作。  
在异常发生时，捕获并统一处理异常。

通过命令, 创建一个拦截器, 在 nestjs 中拦截器依赖于 rxjs 实现对数据的转换，处理

Interceptor 要实现 Nest Interceptor 接口，实现 intercept 方法，调用 next.handle() 就会调用目标 Controller，可以在之前和之后加入一些处理逻辑。

```
nest g itc data
```

*   拦截器代码

```
import { CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { Observable } from 'rxjs';

@Injectable()
export class DataInterceptor implements NestInterceptor {
  // 在这里进行拦截，在请求到达之前
  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {

    console.log('拦截到达之前')

    return next.handle();
  }
}
```

在 controller 中使用，用法同 pipe,guard，也可以全局使用

*   局部使用

```
import { DataInterceptor } from 'src/data/data.interceptor';
@UseInterceptors(DataInterceptor)
```

*   全局使用

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { LoginMiddleware } from './login.middleware';
import { HttpExceptionFilter } from './http-exception.filter';
import { DataInterceptor } from 'src/data/data.interceptor';
import helmet from 'helmet';
async function bootstrap() {
  // main.ts ---> Factory --> Module
  const app = await NestFactory.create(AppModule);
  app.use(helmet());
  // 所有的请求，所有控制器，全部使用
  app.useGlobalInterceptors(new DataInterceptor())
  app.useGlobalFilters(new HttpExceptionFilter());
  app.use(new LoginMiddleware().use);
  await app.listen(3000);
}
bootstrap();
```

##### 案例使用

> 在前后端交互的过程中，很常见的一个应用场景，后端返回的数据的格式，比如返回的 json 数据外面再包一层 data，当然，这个要看个人和公司开发习惯, 这样我们可以用拦截器对响应后的数据进行处理

*   嵌套使用

```
import { CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { Observable, map } from 'rxjs';

@Injectable()
export class DataInterceptor implements NestInterceptor {
  // 在这里进行拦截，在请求到达之前
  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {

    console.log('拦截到达之前')

    return next.handle().pipe(map(data=>({data})))
  }
}
```

![](https://img-blog.csdnimg.cn/img_convert/c28bd0567b6e942b63590ffce11bd2c7.png)

*   判断使用

```
import { BadRequestException, CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { Observable, map } from 'rxjs';
import { CustomException } from 'src/custom.exception';

@Injectable()
export class DataInterceptor implements NestInterceptor {
  // 在这里进行拦截，在请求到达之前
  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {

    const req= context.switchToHttp().getRequest()
    if(req.body.password!=='XXX'){
      throw new BadRequestException()
    }
    

    return next.handle().pipe(map(data=>({data})))
  }
}
```

*   **日志打印使用**

我们首先从 中获取请求对象，并提取出请求的方法和 URL，并打印请求接收的日志。然后，调用 方法获取被拦截路由处理后的结果，并通过 操作符添加一个回调函数。在回调函数中，我们打印响应发送的日志。

```
import { BadRequestException, CallHandler, ExecutionContext, Injectable, NestInterceptor } from '@nestjs/common';
import { Observable, map, tap } from 'rxjs';
import { CustomException } from 'src/custom.exception';

@Injectable()
export class DataInterceptor implements NestInterceptor {
  // 在这里进行拦截，在请求到达之前
  intercept(context: ExecutionContext, next: CallHandler): Observable<any> {

    const request =context.switchToHttp().getRequest()

    const {method,url} =request;
    console.log(`[${method}] ${url} - Request received`)

    return next.handle().pipe(
      tap(()=>{
        console.log(`[${method}] ${url} - Request sent`)
      })
    )


   
  }
}
```

#### NestJs Swagger 接口文档

首先，您必须安装所需的包：

```
$ npm install --save @nestjs/swagger swagger-ui-express
```

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { LoginMiddleware } from './login.middleware';
import { HttpExceptionFilter } from './http-exception.filter';
import { DataInterceptor } from './data/data.interceptor';
import  helmet from 'helmet';
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const config = new DocumentBuilder()
    .setTitle('This is a title')
    .setDescription('This is a description')
    .setVersion('1.0')
    .addTag('cat')
    .addTag('dog')
    .build();

  const document = SwaggerModule.createDocument(app, config);
  SwaggerModule.setup('api', app, document);

  app.use(helmet());
  app.useGlobalInterceptors(new DataInterceptor());
  app.useGlobalFilters(new HttpExceptionFilter());
  app.use(new LoginMiddleware().use);
  await app.listen(3000);
}

bootstrap();
```

DocumentBuilder 有助于构建符合 OpenAPI 规范的基础文档。它提供了几种允许设置诸如标题，描述，版本等属性的方法。为了创建一个完整的文档（使用已定义的 HTTP 路由），我们使用 SwaggerModule 类的 createDocument() 方法。 此方法接收两个参数，即应用程序实例和 Swagger 选项对象。  
一旦创建完文档，我们就可以调用 setup() 方法。 它接收：

1.  Swagger UI 的挂载路径
2.  应用程序实例
3.  上面已经实例化的文档对象

现在，您可以运行以下命令来启动 HTTP 服务器：

```
$ npm run start
```

应用程序运行时，打开浏览器并导航到 http://localhost:3000/api 。 你应该可以看到 Swagger UI

![](https://img-blog.csdnimg.cn/img_convert/1bc757a56e666acc92c70a20203eaf37.png)

*   通过装饰器对接口更详细地说明

```
import { Controller, Get, Param } from '@nestjs/common';
import { ApiTags, ApiParam } from '@nestjs/swagger';

@ApiTags('dog')
@Controller('dog')
export class DogController {
  @Get('/onedog/:name')
  // 通过ApiParam装饰器，来描述接口需要哪些参数
  @ApiParam({ name: 'name', type: String, description: '姓名' })
  @ApiParam({ name: 'gender', type: String, description: '性别' })
  aGetRequest(
    @Param('name') name: string, 
    @Param('gender') gender: string
  ): string { 
    return `a ${gender} named ${name} has lunched a get request`
  }
}
```

![](https://img-blog.csdnimg.cn/img_convert/f77896de24f29c19da57174c3bee428a.png)

#### Nest js 整合 **Knife4j**

官方地址 ： [https://www.npmjs.com/package/nestjs-knife4j?activeTab=readme](https://www.npmjs.com/package/nestjs-knife4j?activeTab=readme)  
平台官方 [https://doc.xiaominfo.com/demo/doc.html#/SwaggerModels/Knife4j%E7%A4%BA%E4%BE%8B](https://doc.xiaominfo.com/demo/doc.html#/SwaggerModels/Knife4j%E7%A4%BA%E4%BE%8B)  
[https://github.com/xiaoymin/knife4j/wiki](https://github.com/xiaoymin/knife4j/wiki)

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { LoginMiddleware } from './login.middleware';
import { HttpExceptionFilter } from './http-exception.filter';
import { DataInterceptor } from './data/data.interceptor';
import  helmet from 'helmet';
import { knife4jSetup } from 'nestjs-knife4j'
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger/dist';


async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  const options = new DocumentBuilder()
  .setTitle('Cats example')
  .setDescription('The cats API description')
  .setVersion('1.0')
  .addTag('cats')
  .build()
  const document = SwaggerModule.createDocument(app, options)
  SwaggerModule.setup('api', app, document)
  knife4jSetup(app, {
    urls: [
      {
        name: '2.X版本',
        url: `/api-json`,
        swaggerVersion: '3.0',
        location: `/api-json`,
      },
    ],
  })
  app.use(helmet());
  app.useGlobalInterceptors(new DataInterceptor());
  app.useGlobalFilters(new HttpExceptionFilter());
  app.use(new LoginMiddleware().use);
  await app.listen(3000);
}

bootstrap();
```

访问地址 ： [http://localhost:3000/doc.html](http://localhost:3000/doc.html#/2.X%E7%89%88%E6%9C%AC/default/UsersController_findAll)  
![](https://img-blog.csdnimg.cn/img_convert/e1ddbcdc09b61d98cb36dbf03cdcffe3.png)

#### NestJs 文件上传

##### 本地文件上传与下载

*   安装库

```
yarn add multer @types/multer
```

*   快速创建

```
nest g res upload
```

![](https://img-blog.csdnimg.cn/img_convert/90abf0f09f038b46a7df61f96d5bfb16.png)

*   注册文件上传的库

```
import { Module } from '@nestjs/common';
import { UploadService } from './upload.service';
import { UploadController } from './upload.controller';

//文件上传需要的包
import { MulterModule } from '@nestjs/platform-express';
import { diskStorage } from 'multer';
import { join, extname } from 'path';

@Module({
  //里面有register 和 registerAsync 两个方法，前者是同步的，后者是异步的
  imports: [MulterModule.register({
    //图片上传完要存放的位置
    storage: diskStorage({
      destination: join(__dirname, '../images'),//存放的文件路径
      filename: (req, file, callback) => {
        //重新定义文件名，file.originalname 文件的原始名称
        // extname 获取文件后缀
        const fileName = `${new Date().getTime() + extname(file.originalname)}`;
        //返回新的名称，参数1是错误，这里用null就好
        return callback(null, fileName)
      }
    }),
  }
  )],
  controllers: [UploadController],
  providers: [UploadService]
})
export class UploadModule { }
```

*   具体使用文件上传的库 ，使用文件上传的拦截器

```
import { Controller, Post,UseInterceptors,UploadedFile,Get,Res,Query} from '@nestjs/common';
import { UploadService } from './upload.service';
// FileInterceptor用于单文件上传，FilesInterceptor用于多文件上传
import {FileInterceptor,FilesInterceptor} from '@nestjs/platform-express'
import {join} from 'path';
import type { Response } from 'express'
@Controller('upload')
export class UploadController {
  constructor(private readonly uploadService: UploadService) {}
  @Post('test')
  // UseInterceptors 处理文件的中间件，file是一个标识名
  @UseInterceptors(FileInterceptor('file'))
  // UploadedFile装饰器是用于读取文件的
  upload (@UploadedFile() file) {
    console.log("file：",file)
    return true
  }

   // 文件下载
   @Get('export')
   download(@Res() res: Response, @Query('filename') filename: string) {
     // 正常应该是从数据库里获取地址
     const url = join(__dirname, `../images/${filename}`);
     res.download(url);
   }

}
```

*   配置文件静态资源访问

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';
import { LoginMiddleware } from './login.middleware';
import { HttpExceptionFilter } from './http-exception.filter';
import { DataInterceptor } from './data/data.interceptor';
import  helmet from 'helmet';
import { knife4jSetup } from 'nestjs-knife4j'
import { DocumentBuilder, SwaggerModule } from '@nestjs/swagger/dist';

//用于配置静态文件访问
import { NestExpressApplication } from '@nestjs/platform-express';
import {join} from 'path';

async function bootstrap() {
    const app= await NestFactory.create<NestExpressApplication>(AppModule)


   //配置静态文件访问目录
 //配置静态文件访问目录
  app.useStaticAssets(join(__dirname,'images'),{
    prefix:"/files/"
  })
  
  app.useStaticAssets(join(__dirname,'..','public'),{
    // 配置虚拟路径
    prefix:"/files/"
  })
 



  const options = new DocumentBuilder()
  .setTitle('Cats example')
  .setDescription('The cats API description')
  .setVersion('1.0')
  .addTag('cats')
  .build()

  const document = SwaggerModule.createDocument(app, options)
  SwaggerModule.setup('api', app, document)

  //  knife4j的配置 
  knife4jSetup(app, {
    urls: [
      {
        name: '测试平台2.X版本',
        url: `/api-json`,
        swaggerVersion: '3.0',
        location: `/api-json`,
      },
    ],
  })

  // 注册全局守卫
  app.use(helmet());
  // app.useGlobalGuards
  app.useGlobalInterceptors(new DataInterceptor());
  // app.useGlobalFilters(new HttpExceptionFilter());
  app.use(new LoginMiddleware().use);
  //app.use(AuthGuard)
  await app.listen(3000);
}

bootstrap();
```

*   多文件下载

```
@Get('export')
  async download(@Res() res: Response, @Query('filenames') filenames: string) {
    const fileNamesArray = filenames.split(',');
    const zip = new JSZip();
    const promises = [];

    fileNamesArray.forEach((filename) => {
      const file = fs.readFileSync(join(__dirname, `../images/${filename}`));
      zip.file(filename, file);
      promises.push(zip.generateAsync({ type: 'nodebuffer' }));
    });

    const buffers = await Promise.all(promises);

    const zipFilename = 'multifiles.zip';
    const fullZipPath = path.join(__dirname, '../zip', zipFilename);

    fs.writeFileSync(fullZipPath, Buffer.concat(buffers));

    res.download(fullZipPath, zipFilename, (err) => {
      if (err) {
        console.log(err);
      } else {
        fs.unlinkSync(fullZipPath);
      }
    });
  }
```

*   测试

![](https://img-blog.csdnimg.cn/img_convert/619d3899a1a96735a11456f4f5a23e1f.png)

##### OSS 文件上传

要在 Nest.js 中实现文件上传到阿里云 OSS 的功能，你可以按照以下步骤进行操作：

步骤 1: 安装依赖  
首先，确保你已经在项目中安装了 `@nestjs/oss` 和 `ali-oss` 这两个依赖。你可以使用以下命令进行安装：

```
npm install --save @nestjs/oss ali-oss
```

步骤 2: 配置 OSS 模块  
在你的 Nest.js 项目中，找到 `app.module.ts` 文件，并在 `imports` 数组中引入 `OssModule`。同时，在 `providers` 数组中配置 `OSS_OPTIONS`，如下所示：

```
import { Module } from '@nestjs/common';
import { OssModule, OSS_OPTIONS } from '@nestjs/oss';

@Module({
  imports: [
    OssModule.registerAsync({
      useFactory: () => ({
        accessKeyId: 'your-access-key',
        accessKeySecret: 'your-access-secret',
        bucket: 'your-bucket-name',
        endpoint: 'your-oss-endpoint'
      }),
      inject: [OSS_OPTIONS]
    })
  ],
  providers: [
    {
      provide: OSS_OPTIONS,
      useFactory: () => ({
        accessKeyId: 'your-access-key',
        accessKeySecret: 'your-access-secret',
        bucket: 'your-bucket-name',
        endpoint: 'your-oss-endpoint'
      })
    }
  ]
})
export class AppModule {}
```

请将上述代码中的 `'your-access-key'`、`'your-access-secret'`、`'your-bucket-name'` 和 `'your-oss-endpoint'` 替换为实际的阿里云 OSS 配置。

步骤 3: 创建文件上传控制器  
在你的 Nest.js 项目中创建一个文件上传的控制器。你可以使用 `nestjs/oss` 依赖提供的 `@UploadFile()` 装饰器来处理上传的文件。

```
import { Controller, Post, UploadedFile, UseInterceptors } from '@nestjs/common';
import { OssService } from '@nestjs/oss';
import { FileInterceptor } from '@nestjs/platform-express';

@Controller('upload')
export class UploadController {
  constructor(private readonly ossService: OssService) {}

  @Post()
  @UseInterceptors(FileInterceptor('file'))
  async uploadFile(@UploadedFile() file) {
    const result = await this.ossService.uploadFile(file.originalname, file.buffer);
    return result;
  }
}
```

步骤 4: 创建路由  
在你的 Nest.js 项目中创建一个路由，将该路由绑定到文件上传的控制器上。

```
import { Module } from '@nestjs/common';
import { UploadController } from './upload.controller';

@Module({
  controllers: [UploadController]
})
export class UploadModule {}
```

步骤 5: 启动应用程序  
最后，你可以启动你的 Nest.js 应用程序，并使用 POST 请求发送文件到 `http://localhost:3000/upload` 上传文件。

以上是一个基本的文件上传到阿里云 OSS 的功能实现的示例代码。请根据你的需求和项目配置进行相应的修改和调整。记得在实际项目中保护你的敏感信息，如 accessKeyId 和 accessKeySecret。

非常抱歉，我在之前的回答中犯了一个错误。实际上，`@nestjs/oss` 是一个不存在的模块，我给出的代码示例是错误的。

要在 Nest.js 中实现文件上传到阿里云 OSS 的功能，你可以按照以下步骤进行操作：

步骤 1: 安装依赖  
首先，确保你已经在项目中安装了 `ali-oss` 这个依赖。你可以使用以下命令进行安装：

```
npm install --save ali-oss
```

步骤 2: 创建文件上传服务  
在你的 Nest.js 项目中创建一个文件上传的服务。你可以创建一个名为 `OssService` 的服务类，并使用 `ali-oss` 库来处理文件上传。

```
import { Injectable } from '@nestjs/common';
import OSS from 'ali-oss';

@Injectable()
export class OssService {
  private client: OSS;

  constructor() {
    this.client = new OSS({
      accessKeyId: 'your-access-key',
      accessKeySecret: 'your-access-secret',
      bucket: 'your-bucket-name',
      endpoint: 'your-oss-endpoint'
    });
  }

  async uploadFile(fileName: string, fileContent: Buffer): Promise<string> {
    try {
      const result = await this.client.put(fileName, fileContent);
      return result.url;
    } catch (error) {
      console.error('Failed to upload file:', error);
      throw error;
    }
  }
}
```

请将上述代码中的 `'your-access-key'`、`'your-access-secret'`、`'your-bucket-name'` 和 `'your-oss-endpoint'` 替换为实际的阿里云 OSS 配置。

步骤 3: 创建文件上传控制器  
在你的 Nest.js 项目中创建一个文件上传的控制器。你可以使用 `@Post()` 装饰器绑定到上传文件的路由，并在上传文件的方法中调用 `OssService` 中的 `uploadFile` 方法。

```
import { Controller, Post, UploadedFile, UseInterceptors } from '@nestjs/common';
import { FileInterceptor } from '@nestjs/platform-express';
import { OssService } from './oss.service';

@Controller('upload')
export class UploadController {
  constructor(private readonly ossService: OssService) {}

  @Post()
  @UseInterceptors(FileInterceptor('file'))
  async uploadFile(@UploadedFile() file) {
    const result = await this.ossService.uploadFile(file.originalname, file.buffer);
    return { url: result };
  }
}
```

步骤 4: 创建路由  
在你的 Nest.js 项目中创建一个路由，将该路由绑定到文件上传的控制器上。

```
import { Module } from '@nestjs/common';
import { UploadController } from './upload.controller';
import { OssService } from './oss.service';

@Module({
  controllers: [UploadController],
  providers: [OssService]
})
export class UploadModule {}
```

步骤 5: 启动应用程序  
最后，你可以启动你的 Nest.js 应用程序，并使用 POST 请求发送文件到 `http://localhost:3000/upload` 上传文件。

以上是一个修正后的文件上传到阿里云 OSS 的功能实现的示例代码。请根据你的需求和项目配置进行相应的修改和调整。记得在实际项目中保护你的敏感信息，如 accessKeyId 和 accessKeySecret。

#### Nest Js 项目实战

// TODO

#### 参考

*   [https://www.yuque.com/zhaocchen/fbyzbp/dh3cf5colgt3amvr](https://www.yuque.com/zhaocchen/fbyzbp/dh3cf5colgt3amvr)