> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_41882147/article/details/82966783?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171574139916800226536173%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171574139916800226536173&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-82966783-null-null.142^v100^pc_search_result_base3&utm_term=GraphQL&spm=1018.2226.3001.4187)

> 本文将从 [GraphQL](https://so.csdn.net/so/search?q=GraphQL&spm=1001.2101.3001.7020) 是什么，为什么要使用 GraphQL，使用 GraphQL 创建简单例子，以及 GraphQL 实战，四个方面对 GraphQL 进行阐述。说得不对的地方，希望大家指出斧正。
> 
> [github](https://so.csdn.net/so/search?q=github&spm=1001.2101.3001.7020) 项目地址：https://github.com/Charming2015/graphql-todolist

###### 一、GraphQL 是什么?

关于 GraphQL 是什么，网上一搜一大堆。根据官网的解释就是**一种用于 API 的查询语言**。

一看到用于 API 的查询语言，我也是一脸懵逼的。博主你在开玩笑吧？你的翻译水平不过关？API 还能查吗？API 不是后端写好，前端调用的吗？

**的确可以，这就是 GraphQL 强大的地方。**  
引用官方文档的一句话：

> ask exactly what you want.

###### 二、为什么要使用 GraphQL?

在实际工作中往往会有这种情景出现：比如说我需要展示一个游戏名的列表，可接口却会把游戏的详细玩法，更新时间，创建者等各种各样的 _（无用的）_ 信息都一同返回。

问了后端，原因大概如下：

> *   原来是为了兼容 PC 端和移动端用同一套接口
> *   或者在整个页面，这里需要显示游戏的标题，可是别的地方需要显示游戏玩法啊，避免多次请求我就全部返回咯
> *   或者是因为有时候项目经理想要显示 “标题 + 更新时间”，有时候想要点击标题展开游戏玩法等等需求，所以把游戏相关的信息都一同返回

简单说就是：

> *   兼容多平台导致字段冗余
> *   一个页面需要多次调用 API 聚合数据
> *   需求经常改动导致接口很难为单一接口精简逻辑

有同学可能会说那也不一定要用 GraphQL 啊，比方说第一个问题，不同平台不同接口不就好了嘛

```
http://api.xxx.com/web/getGameInfo/:gameID
http://api.xxx.com/app/getGameInfo/:gameID
http://api.xxx.com/mobile/getGameInfo/:gameID
```

或者加个参数也行

```
http://api.xxx.com/getGameInfo/:gameID?platfrom=web
```

这样处理的确可以解决问题，但是无疑加大了后端的处理逻辑。你真的不怕后端程序员打你？

这个时候我们会想，接口能不能不写死，把静态变成动态？

**回答是可以的，这就是 GraphQL 所做的!**

###### 三、GraphQL 尝尝鲜——(GraphQL 简单例子)

下面是用`GraphQL.js`和`express-graphql`搭建一个的普通 GraphQL 查询（query）的例子，包括讲解 GraphQL 的部分类型和参数，已经掌握了的同学可以跳过。

###### 1. 先跑个 hello world

1.  新建一个 graphql 文件夹，然后在该目录下打开终端，执行`npm init --y`初始化一个 packjson 文件。
2.  安装依赖包：`npm install --save -D express express-graphql graphql`
3.  新建 schema.js 文件，填上下面的代码

```
//schema.js
const {
      GraphQLSchema,
      GraphQLObjectType,
      GraphQLString,
    } = require('graphql');
const queryObj = new GraphQLObjectType({
    name: 'myFirstQuery',
    description: 'a hello world demo',
    fields: {
        hello: {
            name: 'a hello world query',
            description: 'a hello world demo',
            type: GraphQLString,
            resolve(parentValue, args, request) {
                return 'hello world !';
            }
        }
    }
});
module.exports = new GraphQLSchema({
  query: queryObj
});
```

这里的意思是新建一个简单的查询，查询名字叫`hello`，会返回字段`hello world !`，其他的是定义名字和查询结果类型的意思。

1.  同级目录下新建 server.js 文件，填上下面的代码

```
// server.js
const express = require('express');
const expressGraphql = require('express-graphql');
const app = express();

const schema = require('./schema');
app.use('/graphql', expressGraphql({
	schema,
	graphiql: true
}));

app.get('/', (req, res) => res.end('index'));

app.listen(8000, (err) => {
  if(err) {throw new Error(err);}
  console.log('*** server started ***');
});
```

这部分代码是用`express`跑起来一个服务器，并通过`express-graphql`把`graphql`挂载到服务器上。

1.  运行一下`node server`，并打开`http://localhost:8000/`

![](https://img-blog.csdn.net/20180904171310179?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

如图，说明服务器已经跑起来了  
打开`http://localhost:8000/graphql`，是类似下面这种界面说明已经 graphql 服务已经跑起来了！  
![](https://img-blog.csdn.net/20180905133757579?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
在左侧输入 _(graphql 的查询语法这里不做说明)_

```
{
  hello
}
```

点击头部的三角形的运行按钮，右侧就会显示你查询的结果了  
![](https://img-blog.csdn.net/20180904171834413?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 2. 不仅仅是 hello world

先简单讲解一下代码：

```
const queryObj = new GraphQLObjectType({
    name: 'myFirstQuery',
    description: 'a hello world demo',
    fields: {}
});
```

GraphQLObjectType 是 GraphQL.js 定义的对象类型，包括`name`、`description` 和`fields`三个属性，其中`name`和`description` 是非必填的。`fields`是解析函数，在这里可以理解为查询方法

```
hello: {
            name: 'a hello world query',
            description: 'a hello world demo',
            type: GraphQLString,
            resolve(parentValue, args, request) {
                return 'hello world !';
            }
        }
```

对于每个 fields，又有 name，description，type，resolve 参数，这里的 type 可以理解为 hello 方法返回的数据类型，resolve 就是具体的处理方法。

说到这里有些同学可能还不满足，如果我想每次查询都想带上一个**参数**该怎么办，如果我想查询结果有**多条数据**又怎么处理？

下面修改`schema.js`文件，来一个加强版的查询（当然，你可以整理一下代码，我这样写是为了方便阅读）

```
const {
      GraphQLSchema,
      GraphQLObjectType,
      GraphQLString,
      GraphQLInt,
      GraphQLBoolean
    } = require('graphql');

const queryObj = new GraphQLObjectType({
    name: 'myFirstQuery',
    description: 'a hello world demo',
    fields: {
        hello: {
            name: 'a hello world query',
            description: 'a hello world demo',
            type: GraphQLString,
            args: {
                name: {  // 这里定义参数，包括参数类型和默认值
                    type: GraphQLString,
                    defaultValue: 'Brian'
                }
            },
            resolve(parentValue, args, request) { // 这里演示如何获取参数，以及处理
                return 'hello world ' + args.name + '!';
            }
        },
        person: {
            name: 'personQuery',
            description: 'query a person',
            type: new GraphQLObjectType({ // 这里定义查询结果包含name,age,sex三个字段，并且都是不同的类型。
                name: 'person',
                fields: {
                  name: {
                    type: GraphQLString
                  },
                  age: {
                    type: GraphQLInt
                  },
                  sex: {
                    type: GraphQLBoolean
                  }
                }
            }),
            args: {
                name: {
                    type: GraphQLString,
                    defaultValue: 'Charming'
                }
            },
            resolve(parentValue, args, request) {
                return {
                    name: args.name,
                    age: args.name.length,
                    sex: Math.random() > 0.5
                };
            }
        }
    }
});

module.exports = new GraphQLSchema({
  query: queryObj 
});
```

重启服务后，继续打开`http://localhost:8000/graphql`，在左侧输入

```
{
  hello(name:"charming"),
  person(name:"charming"){
    name,
    sex,
    age
  }
}
```

右侧就会显示出：  
![](https://img-blog.csdn.net/20180904175443716?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

你可以在左侧仅输入`person`方法的`sex`和`age`两个字段，这样就会只返回`sex`和`age`的信息。**动手试一试吧!**

```
{
  person(name:"charming"){
    sex,
    age
  }
}
```

当然，结果的顺序也是按照你输入的顺序排序的。

**定制化的数据，完全根据你查什么返回什么结果。这就是 GraphQL 被称作 API 查询语言的原因。**

###### 四、GraphQL 实战

下面我将搭配`koa`实现一个`GraphQL`查询的例子，逐步从简单`koa`服务到`mongodb`的数据插入查询，再到`GraphQL`的使用，最终实现用`GraphQL`对数据库进行增删查改。

项目效果大概如下：  
![](https://img-blog.csdn.net/20180905142957816?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**有点意思吧？那就开始吧~**  
先把文件目录建构建好

**1. 初始化项目**

*   初始化项目，在根目录下运行`npm init --y`，
*   然后安装一些包：`npm install koa koa-static koa-router koa-bodyparser --save -D`
*   新建`config`、`controllers`、`graphql`、`mongodb`、`public`、`router`这几个文件夹。装逼的操作是在终端输入`mkdir config controllers graphql mongodb public router`回车，ok~

**2. 跑一个 koa 服务器**  
新建一个`server.js`文件，写入以下代码

```
// server.js
import Koa from 'koa'
import Router from 'koa-router'
import bodyParser from 'koa-bodyparser'

const app = new Koa()
const router = new Router();
const port = 4000

app.use(bodyParser());

router.get('/hello', (ctx, next) => {
  ctx.body="hello world"
});


app.use(router.routes())
   .use(router.allowedMethods());

app.listen(port);

console.log('server listen port: ' + port)
```

执行`node server`跑起来服务器，发现报错了：  
![](https://img-blog.csdn.net/20180905145257816?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

这是正常的，这是因为现在的 node 版本并没有支持 es6 的模块引入方式。

百度一下就会有解决方案了，比较通用的做法是用`babel-polyfill`进行转译。

详细的可以看这一个参考操作：[How To Enable ES6 Imports in Node.JS](https://timonweb.com/posts/how-to-enable-es6-imports-in-nodejs/)

具体操作是：新建一个`start.js`文件，写入：

```
// start.js
require('babel-register')({
    presets: [ 'env' ]
})
require('babel-polyfill')
require('./server.js')
```

安装相关包：`npm install --save -D babel-preset-env babel-polyfill babel-register`

修改`package.json`文件，把`"start": "start http://localhost:4000 && node start.js"`这句代码加到下面这个位置：  
![](https://img-blog.csdn.net/20180905144017984?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

运行一下`npm run start`，打开`http://localhost:4000/hello`，结果如图：  
![](https://img-blog.csdn.net/20180905145804768?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
说明 koa 服务器已经跑起来了。

**那么前端页面呢？**

> （由于本文内容不是讲解前端，所以前端代码自行去 github 复制）

*   在 public 下新建`index.html`文件和`js`文件夹，代码直接查看我的项目`public`目录下的 **index.html** 和 **index-s1.js** 文件
*   修改`server.js`，引入`koa-static`模块。`koa-static`会把路由的根目录指向自己定义的路径（也就是本项目的 public 路径）

```
//server.js
import Koa from 'koa'
import Router from 'koa-router'
import KoaStatic from 'koa-static'
import bodyParser from 'koa-bodyparser'

const app = new Koa()
const router = new Router();
const port = 4000

app.use(bodyParser());

router.get('/hello', (ctx, next) => {
  ctx.body="hello world"
});


app.use(KoaStatic(__dirname + '/public'));
app.use(router.routes())
   .use(router.allowedMethods());

app.listen(port);

console.log('server listen port: ' + port)
```

打开`http://localhost:4000/`，发现是类似下面的页面：  
![](https://img-blog.csdn.net/20180905151821932?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

这时候页面已经可以进行简单的交互，但是还没有和后端进行数据交互，所以是个静态页面。

**3. 搭一个 mongodb 数据库，实现数据增删改查**

> **注意：** 请先自行下载好 mongodb 并启动 mongodb。

**a. 写好链接数据库的基本配置和表设定**

在`config`文件夹下面建立一个`index.js`，这个文件主要是放一下链接数据库的配置代码。

```
//  config/index.js
export default {
  dbPath: 'mongodb://localhost/todolist'
}
```

在`mongodb`文件夹新建一个`index.js`和 `schema`文件夹， 在 `schema`文件夹文件夹下面新建`list.js`

在`mongodb/index.js`下写上链接数据库的代码，这里的代码作用是链接上数据库

```
// mongodb/index.js
import mongoose from 'mongoose'
import config from '../config'

require('./schema/list')

export const database = () => {
  mongoose.set('debug', true)

  mongoose.connect(config.dbPath)

  mongoose.connection.on('disconnected', () => {
    mongoose.connect(config.dbPath)
  })
  mongoose.connection.on('error', err => {
    console.error(err)
  })

  mongoose.connection.on('open', async () => {
    console.log('Connected to MongoDB ', config.dbPath)
  })
}
```

在`mongodb/schema/list.js`定义表和字段：

```
//mongodb/schema/list.js
import mongoose from 'mongoose'

const Schema = mongoose.Schema
const ObjectId = Schema.Types.ObjectId

const ListSchema = new Schema({
  title: String,
  desc: String,
  date: String,
  id: String,
  checked: Boolean,
  meta: {
    createdAt: {
      type: Date,
      default: Date.now()
    },
    updatedAt: {
      type: Date,
      default: Date.now()
    }
  }
})

ListSchema.pre('save', function (next) {// 每次保存之前都插入更新时间，创建时插入创建时间
  if (this.isNew) {
    this.meta.createdAt = this.meta.updatedAt = Date.now()
  } else {
    this.meta.updatedAt = Date.now()
  }
  next()
})
mongoose.model('List', ListSchema)
```

**b. 实现数据库增删查改的控制器**

> 建好表，也链接好数据库之后，我们就要写一些方法来操作数据库，这些方法都写在控制器 (controllers) 里面。

在`controllers`里面新建`list.js`，这个文件对应操作 list 数据的控制器，单独拿出来写是为了方便后续项目复杂化的模块化管理。

```
// controllers/list.js
import mongoose from 'mongoose'
const List = mongoose.model('List')
// 获取所有数据
export const getAllList = async (ctx, next) => {
  const Lists = await List.find({}).sort({date:-1}) // 数据查询
  if (Lists.length) {
    ctx.body = {
      success: true,
      list: Lists
    }
  } else {
    ctx.body = {
      success: false
    }
  }
}
// 新增
export const addOne = async (ctx, next) => {
  // 获取请求的数据
  const opts = ctx.request.body
  
  const list = new List(opts)
  const saveList = await list.save() // 保存数据
  console.log(saveList)
  if (saveList) {
    ctx.body = {
      success: true,
      id: opts.id
    }
  } else {
    ctx.body = {
      success: false,
      id: opts.id
    }
  }
}
// 编辑
export const editOne = async (ctx, next) => {
  const obj = ctx.request.body
  let hasError = false
  let error = null
  List.findOne({id: obj.id}, (err, doc) => {
  	if(err) {
  		hasError = true
  		error = err
  	} else {
  		doc.title = obj.title;
  		doc.desc = obj.desc;
  		doc.date = obj.date;
  		doc.save();
  	}
  })
  if (hasError) {
  	ctx.body = {
      success: false,
      id: obj.id
    }
  } else {
  	ctx.body = {
	  success: true,
    id: obj.id
	}
  }
}

// 更新完成状态
export const tickOne = async (ctx, next) => {
  const obj = ctx.request.body
  let hasError = false
  let error = null
  List.findOne({id: obj.id}, (err, doc) => {
  	if(err) {
  		hasError = true
  		error = err
  	} else {
  		doc.checked = obj.checked;
  		doc.save();
  	}
  })
  if (hasError) {
  	ctx.body = {
      success: false,
      id: obj.id
    }
  } else {
  	ctx.body = {
	  success: true,
    id: obj.id
	}
  }
}

// 删除
export const delOne = async (ctx, next) => {
  const obj = ctx.request.body
  let hasError = false
  let msg = null
  List.remove({id: obj.id}, (err, doc) => {
  	if(err) {
  		hasError = true
  		msg = err
  	} else {
  		msg = doc
  	}
  })
  if (hasError) {
  	ctx.body = {
      success: false,
      id: obj.id
    }
  } else {
  	ctx.body = {
  	  success: true,
      id: obj.id
  	}
  }
}
```

**c. 实现路由，给前端提供 API 接口**

> 数据模型和控制器都已经设计好了，下面就利用 koa-router 路由中间件，来实现请求的接口。

我们回到 server.js，在上面添加一些代码。如下：

```
// server.js
import Koa from 'koa'
import Router from 'koa-router'
import KoaStatic from 'koa-static'
import bodyParser from 'koa-bodyparser'
import {database} from './mongodb' 
import {addOne, getAllList, editOne, tickOne, delOne} from './controllers/list' 

database() // 链接数据库并且初始化数据模型

const app = new Koa()
const router = new Router();
const port = 4000

app.use(bodyParser());

router.get('/hello', (ctx, next) => {
  ctx.body = "hello world"
});

// 把对请求的处理交给处理器。
router.post('/addOne', addOne)
      .post('/editOne', editOne)
      .post('/tickOne', tickOne)
      .post('/delOne', delOne)
      .get('/getAllList', getAllList)

app.use(KoaStatic(__dirname + '/public'));
app.use(router.routes())
   .use(router.allowedMethods());

app.listen(port);

console.log('server listen port: ' + port)
```

上面的代码，就是做了：

```
1. 引入mongodb设置、list控制器，
2. 链接数据库
3. 设置每一个设置每一个路由对应的我们定义的的控制器。
```

安装一下 mongoose：`npm install --save -D mongoose`

运行一下`npm run start`，待我们的服务器启动之后，就可以对数据库进行操作了。我们可以通过 postman 来模拟请求，先插几条数据：  
![](https://img-blog.csdn.net/20180905154920796?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
查询全部数据：  
![](https://img-blog.csdn.net/20180905154929644?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

**d. 前端对接接口**

> 前端直接用 ajax 发起请求就好了，平时工作中都是用 axios 的，但是我懒得弄，所以直接用最简单的方法就好了。

引入了 JQuery 之后，改写`public/js/index.js`文件：略（项目里的`public/index-s2.js`的代码）

> 项目跑起来，发现已经基本上实现了前端发起请求对数据库进行操作了。  
> 至此你已经成功打通了前端后台数据库，可以不要脸地称自己是一个小全栈了！

不过我们的目的还没有达到——**用 grapql 实现对数据的操作！**

**4. 用 grapql 实现对数据的操作**

> GraphQL 的大部分讨论集中在数据获取（query），但是任何完整的数据平台也都需要一个改变服务端数据的方法。  
> REST 中，任何请求都可能最后导致一些服务端副作用，但是约定上建议不要使用 GET 请求来修改数据。GraphQL 也是类似 —— 技术上而言，任何查询都可以被实现为导致数据写入。然而，建一个约定来规范任何导致写入的操作都应该显式通过变更（mutation）来发送。

> 简单说就是，GraphQL 用 mutation 来实现数据的修改，虽然 mutation 能做的 query 也能做，但还是要区分开这连个方法，就如同 REST 中约定用 GET 来请求数据，用其他方法来更新数据一样。

**a. 实现查询**  
查询的话比较简单，只需要在接口响应时，获取数据库的数据，然后返回;

```
const objType = new GraphQLObjectType({
  name: 'meta',
  fields: {
    createdAt: {
      type: GraphQLString
    },
    updatedAt: {
      type: GraphQLString
    }
  }
})
let ListType = new GraphQLObjectType({
  name: 'List',
  fields: {
    _id: {
      type: GraphQLID
    },
    id: {
      type: GraphQLString
    },
    title: {
      type: GraphQLString
    },
    desc: {
      type: GraphQLString
    },
    date: {
      type: GraphQLString
    },
    checked: {
      type: GraphQLBoolean
    },
    meta: {
      type: objType
    }
  }
})
const listFields = {
  type: new GraphQLList(ListType),
  args: {},
  resolve (root, params, options) {
    return List.find({}).exec() // 数据库查询
  }
}
let queryType = new GraphQLObjectType({
    name: 'getAllList',
    fields: {
      lists: listFields,
    }
})

export default new GraphQLSchema({
  query: queryType
})
```

_把增删查改都讲完再更改代码~_  
**b. 实现增删查改**

> 一开始说了，其实`mutation`和`query`用法上没什么区别，这只是一种约定。  
> 具体的 mutation 实现方式如下：

```
const outputType = new GraphQLObjectType({
  name: 'output',
  fields: () => ({
    id:     { type: GraphQLString},
    success:   { type: GraphQLBoolean },
  })
});

const inputType = new GraphQLInputObjectType({
  name: 'input',
  fields: () => ({
    id:          { type: GraphQLString },
    desc:        { type: GraphQLString },
    title:       { type: GraphQLString },
    date:        { type: GraphQLString },
    checked:        { type: GraphQLBoolean }
  })
});
let MutationType = new GraphQLObjectType({
  name: 'Mutations',
  fields: () => ({
    delOne: {
      type: outputType,
      description: 'del',
      args: {
        id: { type: GraphQLString }
      },
      resolve: (value, args) => {
      	console.log(args)
      	let result = delOne(args)
        return result
      }
    },
    editOne: {
      type: outputType,
      description: 'edit',
      args: {
        listObj: { type: inputType }
      },
      resolve: (value, args) => {
      	console.log(args)
      	let result = editOne(args.listObj)
        return result
      }
    },
    addOne: {
      type: outputType,
      description: 'add',
      args: {
        listObj: { type: inputType }
      },
      resolve: (value, args) => {
      	console.log(args.listObj)
      	let result = addOne(args.listObj)
        return result
      }
    },
    tickOne: {
      type: outputType,
      description: 'tick',
      args: {
        id: { type: GraphQLString },
        checked: { type: GraphQLBoolean },
      },
      resolve: (value, args) => {
      	console.log(args)
      	let result = tickOne(args)
        return result
      }
    },

  }),
});

export default new GraphQLSchema({
  query: queryType,
  mutation: MutationType
})
```

**c. 完善其余代码**

> 在实现前端请求 Graphql 服务器时，最困扰我的就是参数以什么样的格式进行传递。后来在 Graphql 界面玩 Graphql 的 query 请求时发现了其中的诀窍…

关于前端请求格式进行一下说明：  
![](https://img-blog.csdn.net/20180904171834413?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
如上图，在玩 Graphql 的请求时，我们就可以直接在控制台`network`查看请求的格式了。这里我们只需要模仿这种格式，当做参数发送给 Graphql 服务器即可。

记得用反引号： **``** ，来拼接参数格式。然后用 data: {query: params} 的格式传递参数，代码如下：

```
let data = {
            query: `mutation{
                      addOne(listObj:{
                        id: "${that.getUid()}",
                        desc: "${that.params.desc}",
                        title: "${that.params.title}",
                        date: "${that.getTime(that.params.date)}",
                        checked: false
                      }){
                        id,
                        success
                      }
                    }`
          }
          $.post('/graphql', data).done((res) => {
            console.log(res)
            // do something
          })
```

最后更改`server.js`，`router/index.js`，`controllers/list.js`，`public/index.js`改成 github 项目对应目录的文件代码即可。

完整项目的目录如下：  
![](https://img-blog.csdn.net/20180920144929313?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxODgyMTQ3/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 五、后记

对于 Vue 开发者，可以使用 [vue-apollo](https://www.apollographql.com/docs/react/integrations.html#vue) 使得前端传参更加优雅~

##### 六、参考文献

*   [graphql 官网教程](http://graphql.cn/learn/)
*   [GraphQL.js](https://github.com/graphql/graphql-js)
*   [30 分钟理解 GraphQL 核心概念](https://segmentfault.com/a/1190000014131950)
*   [我的前端故事 ---- 我为什么用 GraphQL](https://www.cnblogs.com/fuhuixiang/p/7479276.html)
*   [GraphQL 搭配 Koa 最佳入门实践](https://juejin.im/post/5a49e5ccf265da430d585cfd)