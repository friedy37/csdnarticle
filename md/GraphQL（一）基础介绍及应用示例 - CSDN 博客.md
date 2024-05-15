> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/why_still_confused/article/details/123754633?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171574139916800226536173%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171574139916800226536173&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_click~default-2-123754633-null-null.142^v100^pc_search_result_base3&utm_term=GraphQL&spm=1018.2226.3001.4187)

[GraphQL](https://so.csdn.net/so/search?q=GraphQL&spm=1001.2101.3001.7020) 是一个用于 API 的查询语言，是一个使用基于类型系统来执行查询的服务端运行时（类型系统由你的数据定义）。GraphQL 并没有和任何特定数据库或者存储引擎绑定，而是依靠你现有的代码和数据支撑。

### 应用场景及优缺点

> 引自译文 [GraphQL：它的优点、缺点和备选方案](https://zhuanlan.zhihu.com/p/39293150)，原文为 [Why GraphQL: Advantages and Disadvantages](https://www.robinwieruch.de/why-graphql-advantages-disadvantages-alternatives/)

#### 应用场景

`GraphQL`是由`Facebook`在 2012 年创立的一门开源查询语言。在它开源之前，`Facebook`就已经在内部移动端应用中使用过。`GraphQL`作为通用的`REST`架构的替代方案而被开发出来，它允许客户端只请求其需要的数据——不多也不少，一切在客户端的主导下。

> 在一个`RESTful`架构下，因为[后端开发](https://so.csdn.net/so/search?q=%E5%90%8E%E7%AB%AF%E5%BC%80%E5%8F%91&spm=1001.2101.3001.7020)人员定义在各个 URL 的资源上返回的数据，而不是前端开发人员来提出数据需求，使得按需获取数据会非常困难。经常前端需要请求一个资源中所有的信息，即便只需要其中的一部分数据。这个问题被称之为过度获取（overfetching）。最恶劣的场景下，一个客户端应用不得不请求多个而不是一个资源，这通常会发起多个网络请求。这不仅会造成过度获取的问题，也会造成瀑布式的网络请求（waterfall network requests）。那么将像 GraphQL 之类的查询语言，不仅在服务端程使用，也应用到客户端的话，客户端来决定需要什么数据，这样只需要发送一个请求到服务端。在 Facebook 的 GraphQL 移动端开发场景下，这极大地减少了忘了请求，因为 GraphQL 一次只需要发起一个请求，并且传输中数据数量也减少了。

#### 优点

##### 声明式地数据获取

GraphQL 在使用查询语句式，使用声明式的方式获取数据。客户端在一个查询请求中，选择需要的数据和相关的字段实体。客户端根据其 UI 来决定需要的字段。你可以说这是 UI 驱动地数据获取。毕竟，GraphQL 提供了极佳的关注点分离方式：客户端知道它需要什么数据，服务端知道数据的结构，以及如何从一些数据源（比如数据库、微服务、第三方 API）中拉取数据。

> 比方说，Airbnb 使用 GraphQL 的例子，在 Airbnb 中的一个搜索界面，经常需要搜索房屋的住房体验和其他相关的一些信息，为了能在一个请求中检索所有的数据，一个 GraphQL 查询会根据 UI 选择数据中的一部分达到完美的匹配。

##### 单一数据源（Single Source of Truth）

在 GraphQL 应用中存在者单一数据源：GraphQL schema。它提供了一个所有可用数据检索的源头。鉴于 GraphQL 的 schema 通常会在服务端定义，客户端可以基于 schema 读取（query）和写入（mutation）数据。因此，服务端提供了所有可用的信息，客户端只需要执行 GraphQL 查询获取部分数据，或者通过 GraphQL 修改变更部分数据。

##### 拼接 GraphQL Schema

拼接 Schema 使得多个 schema 可以聚合成一个。什么时候你需要考虑这个？考虑一下后端的微服务架构。每个微服务处理特定域的业务逻辑和数据。因此，每个微服务都可以定义自己的 GraphQL 架构。之后，使用 Schema 拼接将所有 Schema 聚合到一个可以被客户端访问的 Schema 中。最终，每个微服务都可以拥有自己的 GraphQL 端点，而一个 GraphQL API 网关将所有 schema 合并到一个全局 schema 中，以便使得客户端可以使用。

##### GraphQL 自省（Introspection）

GraphQL 自省允许通过 GraphQL API 检索 GraphQL schema。因为 schema 包含了包含了 GraphQL API 可以获得的所有数据信息，本身就是一份完美的自动生成的 API 文档。不仅仅是 API 的文档，也允许客户端通过 mock GraphQL 的 schema 达到测试的目的，或者使用 schema 拼接的接口检索多个微服务的 schema。

#### 缺点

> [N+1 问题](https://juejin.cn/post/6844903565350158343#heading-13)，解决方案：`DataLoader`

##### GraphQL 查询的复杂性

当一个客户端需要一次查询很多嵌套字段时，前端开发通常不能很清楚他正在通过服务端访问不同的数据库获取过多的数据。这需要一种机制（比如最深查询深度、查询复杂度权重、避免递归、持久化查询）来制止来自客户端的（性能）昂贵的查询。

##### 查询频率限制

另一个问题是频率限制，在 REST 中，可以简单的声明” 一天之中，我们只允许请求这么多资源 “，在一个独立的 GraphQL 操作中很难做到这一点，因为任何操作的开销都可以是廉价的或者昂贵的。这就是那些有着公共 GraphQL API 的公司提出的特定速率限制计算，通常可以归结为前面提到的最大查询深度和查询复杂度权重问题。

##### GraphQL 缓存

一个简单缓存，相比 REST，在 GraphQL 中实现会变得极其复杂。在 REST 中你通过 URL 访问资源，因此你可以在资源级别实现缓存，因为资源使用 URL 作为其标识符。在 GraphQL 中就复杂了，因为即便它操作的是同一个实体，每个查询都各不相同。比如，一个查询中，你可能只会请求一个作者的名字，但是在另外一次查询中你可能也想知道他的电子邮箱地址。这就需要你有一个更加健全的机制中来确保字段级别的缓存，实现起来并不简单。不过，多数基于 GraphQL 构建的类库都提供了开箱即用的缓存机制。

### 对象类型和字段

GraphQL 默认标量类型

*   `Int`：有符号 32 位整数。
*   `Float`：有符号双精度浮点值。
*   `String`：UTF‐8 字符序列。
*   `Boolean`：true 或者 false。
*   `ID`：ID 标量类型表示一个唯一标识符，通常用以重新获取对象或者作为缓存中的键。ID 类型使用和 String 一样的方式序列化；然而将其定义为 ID 意味着并不需要人类可读型。

```
type Starship {
  id: ID!
  nick: [String!]!
  length(unit: LengthUnit = METER): Float
}
```

*   `Starship`为 GraphQL 对象类型
*   `id`/`nick`/`length`为`Starship`类型上的字段
*   `nick`为非空数组，其数组元素为`String`且非空

> 对象类型和字段详细定义见 https://graphql.cn/learn/schema/#type-language

### 查询和变更类型

`schema`内有两个特殊类型，定义了每一个`GraphQL`查询的入口

> 每一个 GraphQL 服务都有一个`query`类型，可能有一个`mutation`类型

```
schema {
  "查询"
  query: Query
  "变更"
  mutation: Mutation
}
```

示例：

```
# 定义查询接口
type Query {
    # 无参, 返回字符串
    hello: String
    # 字段参数且不能为空, 返回普通对象
    bookById(id: ID!): Book
    # 对象参数, 返回列表
    books(book: BookInput): [Book]
}

# 定义修改接口
type Mutation {
    hello: String
}
```

### 应用示例

一个 GraphQL 查询在被验证后，GraphQL 服务器会将之执行，并返回与请求的结构相对应的结果，该结果通常会是 JSON 的格式。

**schema**

```
type Query {
  human(id: ID!): Human
}
 
type Human {
  name: String
  appearsIn: [Episode]
  starships: [Starship]
}
 
enum Episode {
  NEWHOPE
  EMPIRE
  JEDI
}
 
type Starship {
  name: String
}
```

**请求参数**

```
{
  human(id: 1002) {
    name
    appearsIn
    starships {
      name
    }
  }
}
```

**响应结果**

```
{
  "data": {
    "human": {
      "name": "Han Solo",
      "appearsIn": [
        "NEWHOPE",
        "EMPIRE",
        "JEDI"
      ],
      "starships": [
        {
          "name": "Millenium Falcon"
        },
        {
          "name": "Imperial shuttle"
        }
      ]
    }
  }
}
```

参考资料：

1.  [graphql](https://graphql.cn/learn/)
2.  [graphql-java-tools](https://github.com/graphql-java-kickstart/graphql-java-tools)
3.  [[译] 为什么选用 GraphQL：它的优点、缺点和备选方案](https://zhuanlan.zhihu.com/p/39293150)