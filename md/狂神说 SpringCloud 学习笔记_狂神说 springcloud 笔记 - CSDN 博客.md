> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_42665745/article/details/115620140?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171784214316800182132020%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171784214316800182132020&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-4-115620140-null-null.142^v100^pc_search_result_base3&utm_term=%E7%8B%82%E7%A5%9Espringcloud%E7%AC%94%E8%AE%B0&spm=1018.2226.3001.4187)

#### 文章目录

*   *   [1. 微服务架构概述](#1_1)
    *   *   [1. 什么是微服务架构？](#1_3)
        *   [2.2 微服务与微服务架构](#22__13)
        *   [2.3 常见的微服务生态](#23__22)
        *   [2.4 现在的互联网架构](#24__48)
    *   [2. SpringCloud 入门概述](#2_SpringCloud_51)
    *   *   [2.1 SpringCloud 是什么？](#21_SpringCloud_53)
        *   [2.2 SpringCloud 和 SpringBoot 的关系](#22_SpringCloudSpringBoot_56)
    *   [3. SpringCloud Rest 学习环境搭建: 服务提供者与消费者](#3_SpringCloud_Rest_62)
    *   [4.Eureka 服务发现框架](#4Eureka_431)
    *   *   [4.1 工作原理](#41__434)
        *   [4.2 工作流程](#42__443)
        *   [4.3 springcloud 中使用](#43_springcloud_464)
        *   [4.4 Eureka 集群](#44_Eureka_646)
        *   [4.5 Eureka 和 Zookeeper 对比](#45_EurekaZookeeper_711)
    *   [5.Ribbon：负载均衡 (基于客户端)](#5Ribbon_752)
    *   *   [5.1 Ribbon 简介及负载均衡](#51_Ribbon_753)
        *   [5.2 Ribbon 集成](#52_Ribbon_768)
        *   [5.3 使用 Ribbon 实现负载均衡](#53_Ribbon_827)
        *   [5.4 自定义 Ribbon 负载均衡算法](#54_Ribbon_865)
    *   [6.Feign：负载均衡 (基于客户端)](#6Feign_985)
    *   *   [6.1 Feign 简介](#61_Feign_988)
        *   [6.2 Feign 使用](#62_Feign_999)
        *   [6.3 Feign 和 Ribbon 选择](#63_FeignRibbon_1114)
    *   [7.Hystrix：断路器](#7Hystrix_1119)
    *   *   [7.1 雪崩效应](#71__1120)
        *   [7.2 Hystrix](#72_Hystrix_1147)
        *   [7.3 服务熔断](#73__1154)
        *   [7.4 服务降级](#74__1266)
        *   [7.5 服务熔断和降级的区别](#75__1363)
        *   [7.6 Dashboard 流监控](#76_Dashboard__1405)
    *   [8.Zuul 路由网关](#8Zuul_1505)
    *   [9. Spring Cloud Config 分布式配置](#9_Spring_Cloud_Config__1613)
    *   *   [9.1 服务端与 git 整合](#91_git_1639)
        *   [9.2 客户端与 git 整合](#92_git_1728)
        *   [9.3 案例](#93__1840)
    *   [10. 所有代码](#10_1899)
    *   [11. 总结](#11_1901)

### 1. [微服务](https://so.csdn.net/so/search?q=%E5%BE%AE%E6%9C%8D%E5%8A%A1&spm=1001.2101.3001.7020)架构概述

#### 1. 什么是微服务架构？

究竟什么是微服务架构呢？我们在此引用 ThoughtWorks 公司的首席科学家 Martin Fowler 于 2014 年提出的一段话：

*   微服务架构是一种**架构模式**，或者说是一种架构风格，它将**单一的应用程序划分成一组小的服务**，每个服务运行在其独立的自己的进程内，服务之间互相协调，互相配置，为用户提供最终价值，服务之间采用轻量级的**通信机制** (**HTTP**) 互相沟通，每个服务都围绕着**具体的业务**进行构建，并且能够被独立的部署到生产环境中，另外，应尽量避免统一的，集中式的服务管理机制，对具体的一个服务而言，应该根据业务上下文，选择合适的语言，**工具** (**Maven**) 对其进行构建，可以有一个非常轻量级的集中式管理来协调这些服务，可以使用**不同的语言**来编写服务，也可以使用**不同的数据库**存储。
*   原文：[https://martinfowler.com/articles/microservices.html](https://martinfowler.com/articles/microservices.html)
*   汉化：[https://www.cnblogs.com/liuning8023/p/4493156.html](https://www.cnblogs.com/liuning8023/p/4493156.html)

总结一句话：`微服务架构是一种架构模式，将单体式应用拆分成不同的模块（服务），每个模块服务于具体的业务，根据需要使用不同的语言、数据库，相互之间使用Http等进行通信`。

#### 2.2 微服务与微服务架构

**微服务**：

强调的是服务的大小，它关注的是某一个点，是具体解决某一个问题 / 提供落地对应服务的一个服务应用，狭义的看，可以看作是 IDEA 中的 Maven 项目的一个个 Moudel。

**微服务架构**：

微服务架构是一种架构模式，将单体式应用拆分成不同的模块（服务），每个模块服务于具体的业务，根据需要使用不同的语言、数据库，相互之间使用 Http 等进行通信

#### 2.3 常见的微服务生态

微服务架构的 4 个核心问题：

1.  服务很多，客户端如何访问？（API）
2.  服务间如何通信？（Http，RPC）
3.  服务如何治理？（注册与发现）
4.  服务崩了怎么办？（熔断机制）

常见的解决方案：

```
1.Spring Cloud NetFlix 一站式解决方案！
API网关：zuul
通信：Feign---Http通信，同步，阻塞
服务注册发现：Eureka
熔断机制：Hystrix
......

2.Apache Dubbo Zookeeper 半自动！
API网关：没有
通信：Dubbo---RPC
服务注册发现：Zookeeper
熔断机制：没有，借助其他组件

3.Spring Cloud Alibaba 一站式解决方案！
```

#### 2.4 现在的互联网架构

![](https://img-blog.csdnimg.cn/20210412142304232.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

### 2. SpringCloud 入门概述

#### 2.1 SpringCloud 是什么？

**Spring Cloud 是一系列框架的有序集合**。它**利用 Spring Boot** 的开发便利性巧妙地**简化了分布式系统基础设施的开发**，如**服务发现注册、配置中心、消息总线、负载均衡、断路器、数据监控等**，都可以用 Spring Boot 的开发风格做到一键启动和部署。Spring Cloud 并没有重复制造轮子，它只是将各家公司开发的比较成熟、经得起实际考验的服务框架组合起来，通过 Spring Boot 风格进行再封装屏蔽掉了复杂的配置和实现原理，最终给开发者留出了一套简单易懂、易部署和易维护的分布式系统开发工具包。

#### 2.2 SpringCloud 和 SpringBoot 的关系

*   SpringBoot 专注于方便的开发单个个体微服务；
*   SpringCloud 是关注全局的微服务协调整理治理框架，它将 SpringBoot 开发的一个个单体微服务，整合并管理起来，为各个微服务之间提供：配置管理、服务发现、断路器、路由、为代理、事件总栈、全局锁、决策竞选、分布式会话等等集成服务；
*   SpringBoot 可以离开 SpringCloud 独立使用，开发项目，但 SpringCloud 离不开 SpringBoot，属于依赖关系；

总结：SpringBoot 专注于快速、方便的开发单个个体微服务，SpringCloud 关注全局的服务治理框架；

### 3. SpringCloud Rest 学习环境搭建: 服务提供者与消费者

1. 新建一个空的 maven 项目，管理依赖  
pom.xml

```
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>springcloud</artifactId>
    <version>1.0-SNAPSHOT</version>
    <modules>
        <module>springcloud-api</module>
        <module>springcloud-provider-dept-8001</module>
        <module>springcloud-consumer-dept-80</module>
    </modules>

    <!--打包方式-->
    <packaging>pom</packaging>

    <!--管理版本号-->
    <properties>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
        <junit.version>4.12</junit.version>
        <log4j.version>1.2.17</log4j.version>
        <lombok.version>1.16.18</lombok.version>
    </properties>

    <dependencyManagement>
        <dependencies>
            <!--springCloud的依赖-->
            <dependency>
                <groupId>org.springframework.cloud</groupId>
                <artifactId>spring-cloud-dependencies</artifactId>
                <version>Greenwich.SR1</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--SpringBoot-->
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>2.1.4.RELEASE</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            <!--数据库-->
            <dependency>
                <groupId>mysql</groupId>
                <artifactId>mysql-connector-java</artifactId>
                <version>5.1.47</version>
            </dependency>
            <dependency>
                <groupId>com.alibaba</groupId>
                <artifactId>druid</artifactId>
                <version>1.1.10</version>
            </dependency>
            <!--SpringBoot 启动器-->
            <dependency>
                <groupId>org.mybatis.spring.boot</groupId>
                <artifactId>mybatis-spring-boot-starter</artifactId>
                <version>1.3.2</version>
            </dependency>
            <!--日志测试-->
            <dependency>
                <groupId>ch.qos.logback</groupId>
                <artifactId>logback-core</artifactId>
                <version>1.2.3</version>
            </dependency>
            <dependency>
                <groupId>log4j</groupId>
                <artifactId>log4j</artifactId>
                <version>${log4j.version}</version>
            </dependency>
            <!--单元测试~-->
            <dependency>
                <groupId>junit</groupId>
                <artifactId>junit</artifactId>
                <version>${junit.version}</version>
            </dependency>
            <dependency>
                <groupId>org.projectlombok</groupId>
                <artifactId>lombok</artifactId>
                <version>${lombok.version}</version>
            </dependency>
        </dependencies>
    </dependencyManagement>
</project>
```

2. 新建一个 moudle（springcloud-api），主要负责实体类  
pom.xml

```
<!--当前moudle自己需要的依赖，如果父依赖中有，则不需要写版本号，直接使用父依赖中的-->
<dependencies>
    <dependency>
        <groupId>org.projectlombok</groupId>
        <artifactId>lombok</artifactId>
    </dependency>
</dependencies>
```

Dept .java

```
package com.kuang.pojo;

import lombok.Data;
import lombok.NoArgsConstructor;
import lombok.experimental.Accessors;

import java.io.Serializable;

//必须实现序列化接口！
@Data
@NoArgsConstructor
@Accessors(chain = true) //链式写法
public class Dept implements Serializable {
    private Long deptno;
    private String dname;
    private String db_source;
}
```

3. 新建一个 module（springcloud-provider-dept-8001），作为服务提供者  
pom.xml

```
<dependencies>
    <!--需要实体类，导入pom-->
    <dependency>
        <groupId>org.example</groupId>
        <artifactId>springcloud-api</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
    <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
    </dependency>
    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
    </dependency>
    <dependency>
        <groupId>com.alibaba</groupId>
        <artifactId>druid</artifactId>
    </dependency>
    <dependency>
        <groupId>ch.qos.logback</groupId>
        <artifactId>logback-core</artifactId>
    </dependency>
    <dependency>
        <groupId>org.mybatis.spring.boot</groupId>
        <artifactId>mybatis-spring-boot-starter</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <!--热部署-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>
</dependencies>
```

application.yml

```
server:
  port: 8001

mybatis:
  type-aliases-package: com.kuang.pojo
  mapper-locations: classpath:mybatis/mapper/*.xml
  config-location: classpath:mybatis/mybatis-config.xml


spring:
  application:
    name: springcloud-provider-dept
  datasource:
    type: com.alibaba.druid.pool.DruidDataSource
    driver-class-name: org.gjt.mm.mysql.Driver
    url: jdbc:mysql://localhost:3306/db_01?useUnicode=true&characterEncoding=utf-8
    username: root
    password: 123456
```

DeptDao 接口

```
package com.kuang.springcloud.dao;

import com.kuang.pojo.Dept;
import org.apache.ibatis.annotations.Mapper;
import org.springframework.stereotype.Repository;

import java.util.List;

@Mapper
@Repository
public interface DeptDao {

    public boolean addDept(Dept dept);

    public Dept queryById(Long id);

    public List<Dept> queryAll();
}
```

DeptMapper.xml

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.kuang.springcloud.dao.DeptDao">

    <select id="queryById" parameterType="long" resultType="dept">
        select * from dept where deptno=#{deptno};
    </select>

    <select id="queryAll" resultType="dept">
        select * from dept;
    </select>

    <insert id="addDept" parameterType="dept">
        insert into dept(dname,db_source) values (#{dname},database());
    </insert>
</mapper>
```

service 层略

DeptController

```
package com.kuang.springcloud.controller;

import com.kuang.pojo.Dept;
import com.kuang.springcloud.service.DeptService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.*;

import java.util.List;

@RestController
public class DeptController {

    @Autowired
    private DeptService deptService;

    @PostMapping("/dept/add")
    public boolean addDept(Dept dept){
        return  deptService.addDept(dept);
    }

    @GetMapping("/dept/get/{id}")
    public Dept queryById(@PathVariable("id") Long id){
        return deptService.queryById(id);
    }

    @GetMapping("/dept/list")
    public List<Dept> queryAll(){
        return deptService.queryAll();
    }
}
```

最后创建启动类，测试  
4. 新建一个 module（springcloud-consumer-dept-80），作为服务消费者  
pom.xml

```
<dependencies>
    <dependency>
        <groupId>org.example</groupId>
        <artifactId>springcloud-api</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>
</dependencies>
```

application.yml

```
server:
  port: 80
```

ConfigBean

```
package com.kuang.springcloud.config;

import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.web.client.RestTemplate;

@Configuration
public class ConfigBean {

    @Bean
    public RestTemplate getRestTemplate(){
        return new RestTemplate();
    }
}
```

DeptConsumerController

```
package com.kuang.springcloud.controller;

import com.kuang.pojo.Dept;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.client.RestTemplate;

import java.util.List;

@RestController
public class DeptConsumerController {

    /**
     * 理解：消费者，不应该有service层,而应该通过url调提供者的控制器
     * RestTemplate .... 源码中未注册到容器中，需要手动注入
     * (地址：url, 实体：Map ,Class<T> responseType)
     * <p>
     * 提供多种便捷访问远程http服务的方法，简单的Restful服务模板~
     */
    @Autowired
    RestTemplate restTemplate;

    private static final String REST_URL_PREFIX ="http://localhost:8001";

    @RequestMapping("/consumer/dept/add")
    public boolean add(Dept dept){
        // postForObject(服务提供方地址(接口),参数实体,返回类型.class)
        return restTemplate.postForObject(REST_URL_PREFIX+"/dept/add",dept,Boolean.class);
    }

    @RequestMapping("/consumer/dept/get/{id}")
    public Dept queryById(@PathVariable("id") Long id){
        // getForObject(服务提供方地址(接口),返回类型.class)
        return  restTemplate.getForObject(REST_URL_PREFIX+"/dept/get/"+id,Dept.class);
    }

    @RequestMapping("/consumer/dept/list")
    public List<Dept> list(){
        return restTemplate.getForObject(REST_URL_PREFIX+"/dept/list",List.class);
    }
}
```

编写启动类  
5. 测试  
项目结构图  
![](https://img-blog.csdnimg.cn/20210412214643906.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
源码：[https://gitee.com/Filwaod/springcloud](https://gitee.com/Filwaod/springcloud)

### 4.Eureka 服务发现框架

`Eureka`是`Netflix`开发的`服务发现`框架，本身是一个`基于REST的服务`，主要用于定位运行在 AWS 域中的中间层服务，以达到服务发现和中间层服务故障转移的目的。功能类似于 Zookeeper。

#### 4.1 工作原理

![](https://img-blog.csdnimg.cn/20210421134508128.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
Eureka 采用了`C-S的架构设计`，`EurekaServer`是服务端，`Service Provider`和`Service Consumer`都是客户端。

Eureka Server 提供服务注册，各个节点启动后，会在 EurekaServer 中进行注册，这样 Eureka Server 中的服务注册表中将会储存所有课用服务节点的信息，服务节点的信息可以在界面中直观的看到。

Eureka Client 是一个 Java 客户端，用于简化 EurekaServer 的交互，客户端同时也具备一个内置的，使用轮询算法的负载均衡器。在应用启动后，将会向 EurekaServer 发送心跳 (默认周期为 30 秒) 。如果 Eureka Server 在多个心跳周期内没有接收到某个节点的心跳，EurekaServer 将会从服务注册表中把这个服务节点移除掉 (默认周期为 90s)。

**详细的 Eureka 可查看**：[https://blog.csdn.net/qwe86314/article/details/94552801](https://blog.csdn.net/qwe86314/article/details/94552801)

#### 4.2 工作流程

1、`Eureka Server` 启动成功，等待服务端注册。在启动过程中如果配置了集群，集群之间定时通过 `Replicate`同步注册表，每个`Eureka Server` 都存在独立完整的服务注册表信息

2、`Eureka Client`启动时根据配置的`Eureka Server` 地址去注册中心注册服务

3、`Eureka Client` 会每 `30s` 向 `Eureka Server` 发送一次心跳请求，证明客户端服务正常

4、当 `Eureka Server 90s`内没有收到 `Eureka Client` 的心跳，注册中心则认为该节点失效，会注销该实例

5、单位时间内 `Eureka Server` 统计到有大量的 `Eureka Client`没有上送心跳，则认为可能为网络异常，进入自我保护机制，不再剔除没有送上心跳的客户端

6、当 `Eureka Client`心跳请求恢复正常之后，`Eureka Server` 自动退出自我保护模式

7、`Eureka Client`定时全量或者增量从注册中心获取服务注册表，并且将获取到的信息缓存到本地

8、服务调用时，`Eureka Client` 会先从本地缓存找寻调取的服务。如果获取不到，先从注册中心刷新注册表，再同步到本地缓存

9、`Eureka Client`获取到目标服务器信息，发起服务调用

10、`Eureka Client` 程序关闭时向 `Eureka Server` 发送取消请求，`Eureka Server` 将实例从注册表中删除

#### 4.3 springcloud 中使用

**1. 创建 Eureka Server（springcloud-eureka-7001）**

pox.xml 中导入依赖

```
<dependencies>
    <!--导入Eureka Server依赖-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-eureka-server</artifactId>
        <version>1.4.6.RELEASE</version>
    </dependency>
    <!--热部署工具-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>
</dependencies>
```

配置文件中配置，application.yml

```
server:
  port: 7001

# Eureka配置
eureka:
  instance:
    # Eureka服务端的实例名字（localhost，ip，域名）
    hostname: 127.0.0.1
  client:
    # 表示是否向 Eureka 注册中心注册自己，自己就是服务端，所有false
    register-with-eureka: false
    # fetch-registry如果为false,则表示自己为注册中心,客户端为 ture
    fetch-registry: false
    # Eureka监控页面
    service-url:
      defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
```

主启动类加注解开启 Eureka Server

```
@SpringBootApplication
// @EnableEurekaServer 开启EurekaServer，可以注册了
@EnableEurekaServer
public class EurekaServer_7001 {
    public static void main(String[] args) {
        SpringApplication.run(EurekaServer_7001.class,args);
    }
}
```

启动成功后访问 http://localhost:7001/ 得到以下页面  
![](https://img-blog.csdnimg.cn/20210421140248188.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
**2. 创建 Eureka Client，修改之前的服务提供模块（springlouc-provider-dept-8001）**  
pom.xml 导入 Eureka Client 依赖

```
<!--Eureka依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-eureka</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
```

配置文件中配置

```
# Eureka配置：配置服务注册中心地址
eureka:
  client:
    service-url:
      defaultZone: http://localhost:7001/eureka/
```

为主启动类添加注解，开启 Eureka Client

```
@SpringBootApplication
// @EnableEurekaClient 开启Eureka客户端注解，在服务启动后自动向注册中心注册服务
@EnableEurekaClient
public class DeptProvider_8001 {
    public static void main(String[] args) {
        SpringApplication.run(DeptProvider_8001.class,args);
    }
}
```

启动服务端和客户端，访问 http://localhost:7001/ ，可以看到服务已经注册进来了。  
![](https://img-blog.csdnimg.cn/20210421190632749.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70#pic_left)

修改 Eureka 上的默认描述信息

```
# Eureka配置：配置服务注册中心地址
eureka:
  client:
    service-url:
      defaultZone: http://localhost:7001/eureka/
  instance:
    instance-id: springcloud-provider-dept-8001 #修改Eureka上的默认描述信息
```

![](https://img-blog.csdnimg.cn/20210421190649639.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70#pic_left)

配置关于服务加载的监控信息

```
<!--actuator完善监控信息-->
<dependency>
 <groupId>org.springframework.boot</groupId>
 <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

```
# info配置
info:
  # 项目名
  app.name: kuang-springcloud
  #公司名
  company.name: 阿里巴巴有限公司
```

刷新监控页，点击  
![](https://img-blog.csdnimg.cn/20210421141016208.png)  
会显示刚才配置的信息  
![](https://img-blog.csdnimg.cn/20210425203044266.png)

**自我保护机制**

默认情况下，如果 Eureka Server 在一定的 90s 内没有接收到某个微服务实例的心跳，会注销该实例。

但是，如果`短时间内丢失大量的实例心跳，便会触发eureka server的自我保护机制`，比如在开发测试时，需要频繁地重启微服务实例，但是我们很少会把 eureka server 一起重启（因为在开发过程中不会修改 eureka 注册中心），当一分钟内收到的心跳数大量减少时，会触发该保护机制。可以在 eureka 管理界面看到 Renews threshold 和 Renews(last min)，当后者（最后一分钟收到的心跳数）小于前者（心跳阈值）的时候，触发保护机制，会出现红色的警告：`EMERGENCY!EUREKA MAY BE INCORRECTLY CLAIMING INSTANCES ARE UP WHEN THEY'RE NOT.RENEWALS ARE LESSER THAN THRESHOLD AND HENCE THE INSTANCES ARE NOT BEGING EXPIRED JUST TO BE SAFE.`从警告中可以看到，eureka 认为虽然收不到实例的心跳，但它认为实例还是健康的，eureka 会保护这些实例，不会把它们从注册表中删掉。

Eureka 自我保护机制是为了防止误杀服务而提供的一个机制。当个别客户端出现心跳失联时，则认为是客户端的问题，剔除掉客户端；当 Eureka 捕获到大量的心跳失败时，则认为可能是网络问题，进入自我保护机制；当客户端心跳恢复时，Eureka 会自动退出自我保护机制。

如果在保护期内刚好这个服务提供者非正常下线了，此时服务消费者就会拿到一个无效的服务实例，即会调用失败。对于这个问题需要服务消费者端要有一些容错机制，如重试，断路器等。

开发环境下建议关闭

```
eureka.server.enable-self-preservation=false
```

![](https://img-blog.csdnimg.cn/20210421190721179.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70#pic_left)

**注册进来的微服务，获取一些消息（团队开发会用到）**

DeptController.java 新增一个方法

```
/**
 * DiscoveryClient 可以用来获取一些配置的信息，得到具体的微服务！
 */
@Autowired
private DiscoveryClient client;

/**
 * 获取一些注册进来的微服务的信息~，
 *
 * @return
 */
@GetMapping("/dept/discovery")
public Object discovery() {
    // 获取微服务列表的清单
    List<String> services = client.getServices();
    System.out.println("discovery=>services:" + services);
    // 得到一个具体的微服务信息,通过具体的微服务id，applicaioinName；
    List<ServiceInstance> instances = client.getInstances("SPRINGCLOUD-PROVIDER-DEPT");
    for (ServiceInstance instance : instances) {
        System.out.println(
                instance.getHost() + "\t" + // 主机名称
                        instance.getPort() + "\t" + // 端口号
                        instance.getUri() + "\t" + // uri
                        instance.getServiceId() // 服务id
        );
    }
    return this.client;
}
```

![](https://img-blog.csdnimg.cn/20210421141827108.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
主启动类中加上 @EnableDiscoveryClient 注解开启

结果：  
![](https://img-blog.csdnimg.cn/202104211419103.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20210421141914833.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

#### 4.4 Eureka 集群

![](https://img-blog.csdnimg.cn/20210421142003414.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
新建两个 moudle（springcloud-eureka-7002、springcloud-eureka-7003），导入和 7001 相同依赖

由于本机使用的全是 localhost 或 127.0.0.1，修改`C:\Windows\System32\drivers\etc`的 hosts 文件

```
127.0.0.1 eureka7001.com
127.0.0.1 eureka7002.com
127.0.0.1 eureka7003.com
```

`访问eureka7001.com的时候，会解析成127.0.0.1，也就是本机，只是模拟成3台服务器。`

修改 3 个模块的配置文件，7001 的 application.yml

```
server:
  port: 7001

#Eureka配置
eureka:
  instance:
    hostname: eureka7001.com #这里改成域名
  client:
    register-with-eureka: false #表示是否向 Eureka 注册中心注册自己(这个模块本身是服务器,所以不需要)
    fetch-registry: false #fetch-registry如果为false,则表示自己为注册中心
    service-url: #监控页面~
      #重写Eureka的默认端口以及访问路径 --->http://localhost:7001/eureka/
      # 单机： defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
      # 集群（关联）：7001关联7002、7003
      defaultZone: http://eureka7002.com:7002/eureka/,http://eureka7003.com:7003/eureka/
```

7002 的 application.yml

```
server:
  port: 7002

#Eureka配置
eureka:
  instance:
    hostname: eureka7002.com #Eureka服务端的实例名字
  client:
    register-with-eureka: false #表示是否向 Eureka 注册中心注册自己(这个模块本身是服务器,所以不需要)
    fetch-registry: false #fetch-registry如果为false,则表示自己为注册中心
    service-url: #监控页面~
      #重写Eureka的默认端口以及访问路径 --->http://localhost:7001/eureka/
      # 单机： defaultZone: http://${eureka.instance.hostname}:${server.port}/eureka/
      # 集群（关联）：7002关联7001、7003
      defaultZone: http://eureka7001.com:7001/eureka/,http://eureka7003.com:7003/eureka/
```

由于使用了集群，也就相当于现在有 3 个 Eureka Server 了，所以需要修改服务提供者 8001 的注册地址

```
# Eureka配置：配置服务注册中心地址
eureka:
  client:
    service-url:
      # 注册中心地址7001-7003，把所以Eureka Server都写进来，会向3个服务端注册此服务
      defaultZone: http://eureka7001.com:7001/eureka/,http://eureka7002.com:7002/eureka/,http://eureka7003.com:7003/eureka/
  instance:
    instance-id: springcloud-provider-dept-8001 #修改Eureka上的默认描述信息
```

启动监控画面  
![](https://img-blog.csdnimg.cn/20210421142933850.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

#### 4.5 Eureka 和 Zookeeper 对比

RDBMS (MySQL\Oracle\sqlServer) ===> ACID

*   A (Atomicity) 原子性
*   C (Consistency) 一致性
*   I (Isolation) 隔离性
*   D (Durability) 持久性

NoSQL (Redis\MongoDB) ===> CAP

*   C (Consistency) 强一致性
*   A (Availability) 可用性
*   P (Partition tolerance) 分区容错性

**CAP 只能三选二，做不到三个都保证：CA、AP、CP**

*   一个分布式系统不可能同时很好的满足一致性，可用性和分区容错性这三个需求
*   根据 CAP 原理，将 NoSQL 数据库分成了满足 CA 原则，满足 CP 原则和满足 AP 原则三大类
*   CA：单点集群，满足一致性，可用性的系统，通常可扩展性较差
*   CP：满足一致性，分区容错的系统，通常性能不是特别高
*   AP：满足可用性，分区容错的系统，通常可能对一致性要求低一些

**作为分布式服务注册中心，Eureka 比 Zookeeper 好在哪里？**

*   `Zookeeper 保证的是 CP` —> 满足一致性，分区容错的系统，通常性能不是特别高
*   `Eureka 保证的是 AP` —> 满足可用性，分区容错的系统，通常可能对一致性要求低一些

**Zookeeper 保证的是 CP**

​ 当向注册中心查询服务列表时，我们可以容忍注册中心返回的是几分钟以前的注册信息，但不能接收服务直接 down 掉不可用。也就是说，`服务注册功能对可用性的要求要高于一致性`。但 zookeeper 会出现这样一种情况，当 master 节点因为网络故障与其他节点失去联系时，剩余节点会重新进行 leader 选举。问题在于，选举 leader 的时间太长，30-120s，且选举期间整个 zookeeper 集群是不可用的，这就导致在选举期间注册服务瘫痪。在云部署的环境下，因为网络问题使得 zookeeper 集群失去 master 节点是较大概率发生的事件，虽然服务最终能够恢复，但是，漫长的选举时间导致注册长期不可用，是不可容忍的。

**Eureka 保证的是 AP**

​ Eureka 看明白了这一点，因此在设计时就`优先保证可用性`。Eureka 各个节点都是平等的，几个节点挂掉不会影响正常节点的工作，剩余的节点依然可以提供注册和查询服务。而 Eureka 的客户端在向某个 Eureka 注册时，如果发现连接失败，则会自动切换至其他节点，只要有一台 Eureka 还在，就能保住注册服务的可用性，只不过查到的信息可能不是最新的，除此之外，Eureka 还有之中自我保护机制，如果在 15 分钟内超过 85% 的节点都没有正常的心跳，那么 Eureka 就认为客户端与注册中心出现了网络故障，此时会出现以下几种情况：

*   Eureka 不在从注册列表中移除因为长时间没收到心跳而应该过期的服务
*   Eureka 仍然能够接受新服务的注册和查询请求，但是不会被同步到其他节点上 (即保证当前节点依然可用)
*   当网络稳定时，当前实例新的注册信息会被同步到其他节点中

因此，Eureka 可以很好的应对因网络故障导致部分节点失去联系的情况，而不会像 zookeeper 那样使整个注册服务瘫痪

### 5.Ribbon：负载均衡 (基于客户端)

#### 5.1 Ribbon 简介及负载均衡

Spring Cloud Ribbon 是一个基于 HTTP 和 TCP 的客户端负载均衡工具，它基于 Netflix Ribbon 实现。

简单的说，Ribbon 是 Netflix 发布的开源项目，主要功能是提供客户端的软件负载均衡算法，将 Netflix 的中间层服务连接在一起。Ribbon 的客户端组件提供一系列完整的配置项，如：连接超时、重试等。简单的说，就是在配置文件中列出 LoadBalancer (简称 LB：负载均衡) 后面所有的及其，Ribbon 会自动的帮助你基于某种规则 (如简单轮询，随机连接等等) 去连接这些机器。我们也容易使用 Ribbon 实现自定义的负载均衡算法！  
![](https://img-blog.csdnimg.cn/20210425201056964.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

*   LB，即负载均衡 (LoadBalancer) ，在微服务或分布式集群中经常用的一种应用。
*   负载均衡简单的说就是将用户的请求平摊的分配到多个服务上，从而达到系统的 HA (高用)。
*   常见的负载均衡软件有 Nginx、Lvs 等等。
*   Dubbo、SpringCloud 中均给我们提供了负载均衡，SpringCloud 的负载均衡算法可以自定义。
*   负载均衡简单分类：
    *   集中式 LB
        *   即在服务的提供方和消费方之间使用独立的 LB 设施，如 Nginx(反向代理服务器)，由该设施负责把访问请求通过某种策略转发至服务的提供方！
    *   进程式 LB
        *   将 LB 逻辑集成到消费方，消费方从服务注册中心获知有哪些地址可用，然后自己再从这些地址中选出一个合适的服务器。
        *   Ribbon 就属于进程内 LB，它只是一个类库，集成于消费方进程，消费方通过它来获取到服务提供方的地址！

#### 5.2 Ribbon 集成

springcloud-consumer-dept-80 向 pom.xml 中添加 Ribbon 和 Eureka 依赖

```
<!--Ribbon-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-ribbon</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
<!--Eureka: Ribbon需要从Eureka服务中心获取要拿什么-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-eureka</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
```

配置文件中配置 Eureka

```
# Eureka配置
eureka:
  client:
    register-with-eureka: false # 不向 Eureka注册自己
    service-url: # 从三个注册中心中随机取一个去访问
      defaultZone: http://eureka7001.com:7001/eureka/,http://eureka7002.com:7002/eureka/,http://eureka7003.com:7003/eureka/
```

主启动类加注解开启 Eureka

```
//Ribbon 和 Eureka 整合以后，客户端可以直接调用，不用关心IP地址和端口号
@SpringBootApplication
@EnableEurekaClient //开启Eureka 客户端
public class DeptConsumer_80 {
    public static void main(String[] args) {
        SpringApplication.run(DeptConsumer_80.class, args);
    }
}
```

自定义 Spring 配置类：ConfigBean.java 配置负载均衡实现 RestTemplate

```
@Configuration
public class ConfigBean {

    @LoadBalanced //配置负载均衡实现RestTemplate
    @Bean
    public RestTemplate getRestTemplate() {
        return new RestTemplate();
    }
}
```

修改 conroller：DeptConsumerController.java

```
//Ribbon:我们这里的地址，应该是一个变量，通过服务名来访问
//private static final String REST_URL_PREFIX = "http://localhost:8001";
private static final String REST_URL_PREFIX = "http://SPRINGCLOUD-PROVIDER-DEPT";
```

#### 5.3 使用 Ribbon 实现负载均衡

流程图：  
![](https://img-blog.csdnimg.cn/20210425201437455.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
图中黑色实线就是 Ribbon 做的事

1. 新建两个服务提供者 Moudle：springcloud-provider-dept-8003、springcloud-provider-dept-8002

2. 参照 springcloud-provider-dept-8001 依次为另外两个 Moudle 添加 pom.xml 依赖 、resourece 下的 mybatis 和 application.yml 配置，Java 代码

3. 启动所有服务测试 (根据自身电脑配置决定启动服务的个数)，访问 http://eureka7001.com:7002 / 查看结果  
第一次访问  
![](https://img-blog.csdnimg.cn/20210425201938952.png)  
第二次访问  
![](https://img-blog.csdnimg.cn/20210425202026557.png)  
默认使用的轮询算法

在 springcloud-provider-dept-80 模块下的 ConfigBean 中进行配置，切换使用不同的算法

```
@Configuration
public class ConfigBean {

    /**
     * IRule:
     * RoundRobinRule 轮询策略
     * RandomRule 随机策略
     * AvailabilityFilteringRule ： 会先过滤掉，跳闸，访问故障的服务~，对剩下的进行轮询~
     * RetryRule ： 会先按照轮询获取服务~，如果服务获取失败，则会在指定的时间内进行，重试
     */
    @Bean
    public IRule myRule() {
        return new RandomRule();//使用随机策略
        //return new RoundRobinRule();//使用轮询策略
        //return new AvailabilityFilteringRule();//使用轮询策略
        //return new RetryRule();//使用轮询策略
    }
}
```

#### 5.4 自定义 Ribbon 负载均衡算法

在 myRule 包下自定义一个配置类 MyRule.java，注意：该包不要和主启动类所在的包同级，要跟启动类所在包同级  
![](https://img-blog.csdnimg.cn/20210425202305543.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
MyRule.java

```
@Configuration
public class MyRule {

    @Bean
    public IRule myRule(){
        return new MyRandomRule();//默认是轮询RandomRule,现在自定义为自己的
    }
}
```

MyRandomRule.java

```
public class MyRandomRule extends AbstractLoadBalancerRule {

    /**
     * 每个服务访问5次则换下一个服务(总共3个服务)
     * <p>
     * total=0,默认=0,如果=5,指向下一个服务节点
     * index=0,默认=0,如果total=5,index+1
     */
    private int total = 0;//被调用的次数
    private int currentIndex = 0;//当前是谁在提供服务

    //@edu.umd.cs.findbugs.annotations.SuppressWarnings(value = "RCN_REDUNDANT_NULLCHECK_OF_NULL_VALUE")
    public Server choose(ILoadBalancer lb, Object key) {
        if (lb == null) {
            return null;
        }
        Server server = null;

        while (server == null) {
            if (Thread.interrupted()) {
                return null;
            }
            List<Server> upList = lb.getReachableServers();//获得当前活着的服务
            List<Server> allList = lb.getAllServers();//获取所有的服务

            int serverCount = allList.size();
            if (serverCount == 0) {
                /*
                 * No servers. End regardless of pass, because subsequent passes
                 * only get more restrictive.
                 */
                return null;
            }

            //int index = chooseRandomInt(serverCount);//生成区间随机数
            //server = upList.get(index);//从或活着的服务中,随机获取一个

            //=====================自定义代码=========================

            if (total < 5) {
                server = upList.get(currentIndex);
                total++;
            } else {
                total = 1;
                currentIndex++;
                if (currentIndex >= upList.size()) {
                    currentIndex = 0;
                }
                server = upList.get(currentIndex);//从活着的服务中,获取指定的服务来进行操作
            }
            
            //======================================================
            
            if (server == null) {
                /*
                 * The only time this should happen is if the server list were
                 * somehow trimmed. This is a transient condition. Retry after
                 * yielding.
                 */
                Thread.yield();
                continue;
            }
            if (server.isAlive()) {
                return (server);
            }
            // Shouldn't actually happen.. but must be transient or a bug.
            server = null;
            Thread.yield();
        }
        return server;
    }

    protected int chooseRandomInt(int serverCount) {
        return ThreadLocalRandom.current().nextInt(serverCount);
    }

    @Override
    public Server choose(Object key) {
        return choose(getLoadBalancer(), key);
    }

    @Override
    public void initWithNiwsConfig(IClientConfig clientConfig) {
        // TODO Auto-generated method stub
    }
}
```

主启动类开启负载均衡并指定自定义的 MyRule 配置类

```
//Ribbon 和 Eureka 整合以后，客户端可以直接调用，不用关心IP地址和端口号
@SpringBootApplication
@EnableEurekaClient
//在微服务启动的时候就能加载自定义的Ribbon类(自定义的规则会覆盖原有默认的规则)
@RibbonClient(name = "SPRINGCLOUD-PROVIDER-DEPT",configuration = MyRule.class)//开启负载均衡,并指定自定义的规则
public class DeptConsumer_80 {
    public static void main(String[] args) {
        SpringApplication.run(DeptConsumer_80.class, args);
    }
}
```

### 6.Feign：负载均衡 (基于客户端)

#### 6.1 Feign 简介

Feign 是声明式 Web Service 客户端，它让微服务之间的调用变得更简单，类似 controller 调用 service。SpringCloud 集成了 Ribbon 和 Eureka，可以使用 Feigin 提供负载均衡的 http 客户端

Feign，主要是社区版，大家都习惯面向接口编程。这个是很多开发人员的规范。调用微服务访问两种方法

*   微服务名字 【ribbon】
*   接口和注解 【feign】

feign 和 ribbon 是 Spring Cloud 的 Netflix 中提供的两个实现软负载均衡的组件，Ribbon 和 Feign 都是用于调用其他服务的，方式不同。**Feign 则是在 Ribbon 的基础上进行了一次改进**，采用接口的方式，将需要调用的其他服务的方法定义成抽象方法即可，不需要自己构建 http 请求。不过要注意的是抽象方法的注解、方法签名要和提供服务的方法完全一致。

#### 6.2 Feign 使用

1. 改造 springcloud-api 模块代码  
添加依赖

```
<!--Feign的依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-feign</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
```

新建 service 包，并新建 DeptClientService.java 接口

```
@Component
// @FeignClient:微服务客户端注解,value:指定微服务的名字,这样就可以使Feign客户端直接找到对应的微服务
@FeignClient(value = "SPRINGCLOUD-PROVIDER-DEPT")
public interface DeptClientService {

    @GetMapping("/dept/get/{id}")
    public Dept queryById(@PathVariable("id") Long id);

    @GetMapping("/dept/list")
    public Dept queryAll();

    @GetMapping("/dept/add")
    public Dept addDept(Dept dept);
}
```

2. 创建 springcloud-consumer-dept-feign 模块  
![](https://img-blog.csdnimg.cn/20210425195900292.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
拷贝 springcloud-consumer-dept-80 模块下的 pom.xml，resource，以及 java 代码到 springcloud-consumer-feign 模块，并添加 feign 依赖。

```
<!--Feign的依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-feign</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
```

启动类上添加注解开启 Feign

```
@SpringBootApplication
@EnableEurekaClient
// feign客户端注解,并指定要扫描的包以及配置接口DeptClientService
@EnableFeignClients(basePackages = {"com.kuang.springcloud"})
// 切记不要加这个注解，不然会出现404访问不到
//@ComponentScan("com.kuang.springcloud")
public class FeignConsumer_80 {
    public static void main(String[] args) {
        SpringApplication.run(FeignConsumer_80.class,args);
    }
}
```

**Feign**：修改 controller

```
@RestController
public class DeptConsumerController {

    @Autowired
    private DeptClientService deptClientService;

    @PostMapping("/consumer/dept/add")
    public boolean add(Dept dept){
        return deptClientService.addDept(dept);
    }

    @GetMapping("/dept/get/{id}")
    public Dept getById(@PathVariable("id") Long id){
        return deptClientService.queryById(id);
    }

    @RequestMapping("/consumer/dept/list")
    public List<Dept> list() {
        return deptClientService.queryAll();
    }
}
```

**Ribbon**

```
@RestController
public class DeptConsumerController {

    @Autowired
    private RestTemplate restTemplate;

    private static final String REST_URL_PREFIX = "http://SPRINGCLOUD-PROVIDER-DEPT";

    @RequestMapping("/consumer/dept/add")
    public boolean add(Dept dept) {
        // postForObject(服务提供方地址(接口),参数实体,返回类型.class)
        return restTemplate.postForObject(REST_URL_PREFIX + "/dept/add", dept, Boolean.class);
    }

    @RequestMapping("/consumer/dept/get/{id}")
    public Dept get(@PathVariable("id") Long id) {
        // getForObject(服务提供方地址(接口),返回类型.class)
        return restTemplate.getForObject(REST_URL_PREFIX + "/dept/get/" + id, Dept.class);
    }

    @RequestMapping("/consumer/dept/list")
    public List<Dept> list() {
        return restTemplate.getForObject(REST_URL_PREFIX + "/dept/list", List.class);
    }
}
```

**Feign 和 Ribbon 二者对比，前者显现出面向接口编程特点，代码看起来更清爽，而且 Feign 调用方式更符合我们之前在做 SSM 或者 SprngBoot 项目时，Controller 层调用 Service 层的编程习惯！**

#### 6.3 Feign 和 Ribbon 选择

**根据个人习惯而定，如果喜欢 REST 风格使用 Ribbon；如果喜欢社区版的面向接口风格使用 Feign。**

Feign 本质上也是实现了 Ribbon，只不过后者是在调用方式上，为了满足一些开发者习惯的接口调用习惯！

### 7.Hystrix：断路器

#### 7.1 雪崩效应

分布式系统环境下，服务间类似依赖非常常见，一个业务调用通常依赖多个基础服务。

多个微服务之间调用的时候，假设微服务 A 调用微服务 B 和微服务 C，微服务 B 和微服务 C 又调用其他的微服务，这就是所谓的 “扇出”，**如果扇出的链路上某个微服务的调用响应时间过长，或者不可用，而此时有大批量请求服务 A 时，最终可能导致整个服务资源耗尽，无法继续对外提供服务**，这就是所谓的 “**雪崩效应**”。

![](https://img-blog.csdnimg.cn/20210425211534172.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
**雪崩效应常见场景**

*   硬件故障：如服务器宕机，机房断电，光纤被挖断等。
*   流量激增：如异常流量，重试加大流量等。
*   缓存穿透：一般发生在应用重启，所有缓存失效时，以及短时间内大量缓存失效时。大量的缓存不命中，使请求直击后端服务，造成服务提供者超负荷运行，引起服务不可用。
*   程序 BUG：如程序逻辑导致内存泄漏，JVM 长时间 FullGC 等。
*   同步等待：服务间采用同步调用模式，同步等待造成的资源耗尽。

**雪崩效应应对策略**

针对造成雪崩效应的不同场景，可以使用不同的应对策略，没有一种通用所有场景的策略，参考如下：

*   硬件故障：多机房容灾、异地多活等。
*   流量激增：服务自动扩容、流量控制（限流、关闭重试）等。
*   缓存穿透：缓存预加载、缓存异步加载等。
*   程序 BUG：修改程序 bug、及时释放资源等。
*   同步等待：资源隔离、MQ 解耦、不可用服务调用快速失败等。资源隔离通常指不同服务调用采用不同的线程池；不可用服务调用快速失败一般通过熔断器模式结合超时机制实现。

综上所述，如果一个应用不能对来自依赖的故障进行隔离，那该应用本身就处在被拖垮的风险中。 因此，**为了构建稳定、可靠的分布式系统，我们的服务应当具有自我保护能力，当依赖服务不可用时，当前服务启动自我保护功能，必要时进行弃车保帅，从而避免发生雪崩效应。**

#### 7.2 Hystrix

Hystrix [hɪst’rɪks]，中文含义是豪猪，因其背上长满棘刺，从而拥有了自我保护的能力。

​ Hystrix 是一个应用于处理分布式系统的延迟和容错的开源库，在分布式系统里，许多依赖不可避免的会调用失败，比如超时，异常等，**Hystrix 能够保证在一个依赖出问题的情况下，不会导致整个体系服务失败，避免级联故障，以提高分布式系统的弹性。**

**​ “断路器”** 本身是一种开关装置，当某个服务单元发生故障之后，通过断路器的故障监控 (类似熔断保险丝) ，**向调用方返回一个服务预期的，可处理的备选响应 (FallBack) ，而不是长时间的等待或者抛出调用方法无法处理的异常，这样就可以保证了服务调用方的线程不会被长时间，不必要的占用**，从而避免了故障在分布式系统中的蔓延，乃至雪崩。  
![](https://img-blog.csdnimg.cn/20210425212716819.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

#### 7.3 服务熔断

**当扇出链路的某个微服务不可用或者响应时间太长时，会进行服务的熔断**，熔断该节点微服务的调用，快速返回错误的响应信息。检测到该节点微服务调用响应正常后恢复调用链路。在 SpringCloud 框架里熔断机制通过 Hystrix 实现。Hystrix 会监控微服务间调用的状况，当失败的调用到一定阀值缺省是 5 秒内 20 次调用失败，就会启动熔断机制。熔断机制的注解是：@HystrixCommand。

案例：  
新建 springcloud-provider-dept-hystrix-8001 模块并拷贝 springcloud-provider-dept–8001 内的 pom.xml、resource 和 Java 代码进行初始化并调整。

导入 hystrix 依赖

```
<!--导入Hystrix依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-hystrix</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
```

调整 yml 配置文件

```
server:
  port: 8001

# mybatis配置
mybatis:
  # springcloud-api 模块下的pojo包
  type-aliases-package: com.haust.springcloud.pojo
  # 本模块下的mybatis-config.xml核心配置文件类路径
  config-location: classpath:mybatis/mybatis-config.xml
  # 本模块下的mapper配置文件类路径
  mapper-locations: classpath:mybatis/mapper/*.xml

# spring配置
spring:
  application:
    #项目名
    name: springcloud-provider-dept
  datasource:
    # 德鲁伊数据源
    type: com.alibaba.druid.pool.DruidDataSource
    driver-class-name: com.mysql.jdbc.Driver
    url: jdbc:mysql://localhost:3306/db01?useUnicode=true&characterEncoding=utf-8
    username: root
    password: 123456

# Eureka配置：配置服务注册中心地址
eureka:
  client:
    service-url:
      # 注册中心地址7001-7003
      defaultZone: http://eureka7001.com:7001/eureka/,http://eureka7002.com:7002/eureka/,http://eureka7003.com:7003/eureka/
  instance:
    instance-id: springcloud-provider-dept-hystrix-8001 #修改Eureka上的默认描述信息
    prefer-ip-address: true #改为true后默认显示的是ip地址而不再是localhost

#info配置
info:
  app.name: kuang-springcloud #项目的名称
  company.name: com.haust #阿里巴巴有限公司
```

修改 controller

```
@RestController
public class DeptController {

    @Autowired
    private DeptService deptService;

    /**
     * 根据id查询部门信息
     * 如果根据id查询出现异常,则走hystrixGet这段备选代码
     * @param id
     * @return
     */
    @HystrixCommand(fallbackMethod = "hystrixGet")
    @RequestMapping("/dept/get/{id}")//根据id查询
    public Dept get(@PathVariable("id") Long id){
        Dept dept = deptService.queryById(id);
        if (dept==null){
            throw new RuntimeException("这个id=>"+id+",不存在该用户，或信息无法找到~");
        }
        return dept;
    }

    /**
     * 根据id查询备选方案(熔断)
     * @param id
     * @return
     */
    public Dept hystrixGet(@PathVariable("id") Long id){
        return new Dept().setDeptno(id)
                .setDname("这个id=>"+id+",没有对应的信息,null---@Hystrix~")
                .setDb_source("在MySQL中没有这个数据库");
    }
}
```

为主启动类添加对熔断的支持注解 @EnableCircuitBreaker

```
@SpringBootApplication
@EnableEurekaClient // EnableEurekaClient 客户端的启动类，在服务启动后自动向注册中心注册服务
@EnableDiscoveryClient // 服务发现~
@EnableCircuitBreaker // 添加对熔断的支持注解
public class HystrixDeptProvider_8001 {
    public static void main(String[] args) {
        SpringApplication.run(HystrixDeptProvider_8001.class,args);
    }
}
```

测试：访问一个不存在的 id  
![](https://img-blog.csdnimg.cn/20210425215433563.png)

#### 7.4 服务降级

服务降级是指 当服务器压力剧增的情况下，根据实际业务情况及流量，对一些服务和页面有策略的不处理，或换种简单的方式处理，从而释放服务器资源以保证核心业务正常运作或高效运作。说白了，**就是尽可能的把系统资源让给优先级高的服务。**

资源有限，而请求是无限的。如果在并发高峰期，不做服务降级处理，一方面肯定会影响整体服务的性能，严重的话可能会导致宕机某些重要的服务不可用。所以，一般在高峰期，为了保证核心功能服务的可用性，都要对某些服务降级处理。比如当双 11 活动时，把交易无关的服务统统降级，如查看蚂蚁深林，查看历史订单等等。

服务降级主要用于什么场景呢？当整个微服务架构整体的负载超出了预设的上限阈值或即将到来的流量预计将会超过预设的阈值时，为了保证重要或基本的服务能正常运行，可以将一些 不重要 或 不紧急 的服务或任务进行服务的 延迟使用 或 暂停使用。

降级的方式可以根据业务来，可以延迟服务，比如延迟给用户增加积分，只是放到一个缓存中，等服务平稳之后再执行 ；或者在粒度范围内关闭服务，比如关闭相关文章的推荐。  
![](https://img-blog.csdnimg.cn/20210425220847694.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

由上图可得，**当某一时间内服务 A 的访问量暴增，而 B 和 C 的访问量较少，为了缓解 A 服务的压力，这时候需要 B 和 C 暂时关闭一些服务功能，去承担 A 的部分服务，从而为 A 分担压力，叫做服务降级。**

**服务降级需要考虑的问题**

*   1）那些服务是核心服务，哪些服务是非核心服务
*   2）那些服务可以支持降级，那些服务不能支持降级，降级策略是什么
*   3）除服务降级之外是否存在更复杂的业务放通场景，策略是什么？

**自动降级分类**  
1）超时降级：主要配置好超时时间和超时重试次数和机制，并使用异步机制探测回复情况

2）失败次数降级：主要是一些不稳定的 api，当失败调用次数达到一定阀值自动降级，同样要使用异步机制探测回复情况

3）故障降级：比如要调用的远程服务挂掉了（网络故障、DNS 故障、http 服务返回错误的状态码、rpc 服务抛出异常），则可以直接降级。降级后的处理方案有：默认值（比如库存服务挂了，返回默认现货）、兜底数据（比如广告挂了，返回提前准备好的一些静态页面）、缓存（之前暂存的一些缓存数据）

4）限流降级：秒杀或者抢购一些限购商品时，此时可能会因为访问量太大而导致系统崩溃，此时会使用限流来进行限制访问量，当达到限流阀值，后续请求会被降级；降级后的处理方案可以是：排队页面（将用户导流到排队页面等一会重试）、无货（直接告知用户没货了）、错误页（如活动太火爆了，稍后重试）。

案例：  
在 springcloud-api 模块下的 service 包中新建降级配置类 DeptClientServiceFallBackFactory.java

```
@Component
public class DeptClientServiceFallBackFactory implements FallbackFactory {

    @Override
    public DeptClientService create(Throwable cause) {
        return new DeptClientService() {
            @Override
            public Dept queryById(Long id) {
                return new Dept()
                        .setDeptno(id)
                        .setDname("id=>" + id + "没有对应的信息，客户端提供了降级的信息，这个服务现在已经被关闭")
                        .setDb_source("没有数据~");
            }
            @Override
            public List<Dept> queryAll() {
                return null;
            }

            @Override
            public Boolean addDept(Dept dept) {
                return false;
            }
        };
    }
}
```

在 DeptClientService 中指定降级配置类 DeptClientServiceFallBackFactory

```
@Component //注册到spring容器中
//@FeignClient:微服务客户端注解,value:指定微服务的名字,这样就可以使Feign客户端直接找到对应的微服务
@FeignClient(value = "SPRINGCLOUD-PROVIDER-DEPT",fallbackFactory = DeptClientServiceFallBackFactory.class)//fallbackFactory指定降级配置类
public interface DeptClientService {

    @GetMapping("/dept/get/{id}")
    public Dept queryById(@PathVariable("id") Long id);

    @GetMapping("/dept/list")
    public List<Dept> queryAll();

    @GetMapping("/dept/add")
    public Boolean addDept(Dept dept);
}
```

在 springcloud-consumer-dept-feign 模块中开启降级：

```
server:
  port: 80

# Eureka配置
eureka:
  client:
    register-with-eureka: false # 不向 Eureka注册自己
    service-url: # 从三个注册中心中随机取一个去访问
      defaultZone: http://eureka7001.com:7001/eureka/,http://eureka7002.com:7002/eureka/,http://eureka7003.com:7003/eureka/

# 开启降级feign.hystrix
feign:
  hystrix:
    enabled: true
```

测试：打开注册中心，1 个服务提供者，1 个服务消费者  
正常访问是没问题的，现在模拟关闭服务提供者，看结果  
![](https://img-blog.csdnimg.cn/20210425221159310.png)

#### 7.5 服务熔断和降级的区别

<table><tbody><tr><th width="50px">不同点</th><th width="100px">服务熔断</th><th width="100px">服务降级</th></tr><tr><td>概念</td><td>某个服务超时或异常，引起熔断，类似于保险丝 (自我熔断)</td><td>从整体网站请求负载考虑，当某个服务熔断或者关闭之后，服务将不再被调用，此时在客户端，我们可以准备一个 FallBackFactory ，返回一个默认的值 (缺省值)。会导致整体的服务下降，但是好歹能用，比直接挂掉强</td></tr><tr><td>触发原因</td><td>服务熔断一般是某个服务（下游服务）故障引起</td><td>服务降级一般是从整体负荷考虑</td></tr><tr><td>管理目标的层次</td><td>熔断其实是一个框架级的处理，每个微服务都需要（无层级之分）</td><td>降级一般需要对业务有层级之分（比如降级一般是从最外围服务开始）</td></tr><tr><td>实现方式</td><td>熔断一般称为自我熔断</td><td>服务降级具有代码侵入性 (由控制器完成 / 或自动降级)</td></tr></tbody></table>

**熔断，降级，限流：**

限流：限制并发的请求访问量，超过阈值则拒绝；

降级：服务分优先级，牺牲非核心服务（不可用），保证核心服务稳定；从整体负荷考虑；

熔断：依赖的下游服务故障触发熔断，避免引发本系统崩溃；系统自动执行和恢复

#### 7.6 Dashboard 流监控

新建 springcloud-consumer-hystrix-dashboard 模块

```
<!--Hystrix依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-hystrix</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
<!--dashboard依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-hystrix-dashboard</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
<!--Ribbon-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-ribbon</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
<!--Eureka-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-eureka</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
<!--实体类+web-->
<dependency>
    <groupId>com.haust</groupId>
    <artifactId>springcloud-api</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
<!--热部署-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
</dependency>
```

主启动类

```
@SpringBootApplication
// 开启Dashboard
@EnableHystrixDashboard
public class DeptConsumerDashboard_9001 {
    public static void main(String[] args) {
        SpringApplication.run(DeptConsumerDashboard_9001.class,args);
    }
}
```

给 springcloud-provider-dept-hystrix-8001 模块下的主启动类添加如下代码, 添加监控

```
@SpringBootApplication
@EnableEurekaClient //EnableEurekaClient 客户端的启动类，在服务启动后自动向注册中心注册服务
public class DeptProvider_8001 {
    public static void main(String[] args) {
        SpringApplication.run(DeptProvider_8001.class,args);
    }

    //增加一个 Servlet
    @Bean
    public ServletRegistrationBean hystrixMetricsStreamServlet(){
        ServletRegistrationBean registrationBean = new ServletRegistrationBean(new HystrixMetricsStreamServlet());
        //访问该页面就是监控页面
        registrationBean.addUrlMappings("/actuator/hystrix.stream");
       
        return registrationBean;
    }
}
```

访问：http://localhost:9001/hystrix  
![](https://img-blog.csdnimg.cn/20210425230159342.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
消费者模块，导入依赖

```
<!--Feign的依赖-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-feign</artifactId>
    <version>1.4.6.RELEASE</version>
</dependency>
<!--监控的依赖-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

访问：http://localhost:8001/actuator/hystrix.stream  
![](https://img-blog.csdnimg.cn/20210425230511534.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
然后进入监控画面  
![](https://img-blog.csdnimg.cn/20210425230532568.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20210425230541624.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

### 8.Zuul 路由网关

Zull 包含了对请求的路由 (用来跳转的) 和过滤两个最主要功能：

​ 其中路由功能负责将外部请求转发到具体的微服务实例上，是实现外部访问统一入口的基础，而过滤器功能则负责对请求的处理过程进行干预，是实现请求校验，服务聚合等功能的基础。Zuul 和 Eureka 进行整合，将 Zuul 自身注册为 Eureka 服务治理下的应用，同时从 Eureka 中获得其他服务的消息，也即以后的访问微服务都是通过 Zuul 跳转后获得。  
![](https://img-blog.csdnimg.cn/20210426203355449.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
案例：  
新建 springcloud-zuul-9527 模块，并导入依赖

```
<dependencies>
    <!--导入zuul依赖-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-zuul</artifactId>
        <version>1.4.6.RELEASE</version>
    </dependency>
    <!--Hystrix依赖-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-hystrix</artifactId>
        <version>1.4.6.RELEASE</version>
    </dependency>
    <!--dashboard依赖-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-hystrix-dashboar</artifactId>
        <version>1.4.6.RELEASE</version>
    </dependency>
    <!--Ribbon-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-ribbon</artifactId>
        <version>1.4.6.RELEASE</version>
    </dependency>
    <!--Eureka-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-eureka</artifactId>
        <version>1.4.6.RELEASE</version>
    </dependency>
    <!--实体类+web-->
    <dependency>
        <groupId>com.haust</groupId>
        <artifactId>springcloud-api</artifactId>
        <version>1.0-SNAPSHOT</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <!--热部署-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-devtools</artifactId>
    </dependency>
</dependencies>
```

application.yml

```
server:
  port: 9527

spring:
  application:
    name: springcloud-zuul #微服务名字

eureka:
  client:
    service-url:
      defaultZone: http://eureka7004.com:7004/eureka/,http://eureka7002.com:7002/eureka/,http://eureka7003.com:7003/eureka/
  instance:
    instance-id: zuul9527.com
    prefer-ip-address: true

info:
 app.name: kuang-springcloud
 company.name: 阿里巴巴有限公司

# zuul 路由网关配置
zuul:
  # 路由相关配置
  # 原来访问路由 eg:http://localhost:9527/springcloud-provider-dept/dept/get/1
  # zuul路由配置后访问路由 eg:http://localhost:9527/kuang/mydept/dept/get/1
  routes:
    mydept.serviceId: springcloud-provider-dept # 服务ID
    mydept.path: /mydept/** # 给原来的服务ID设置另一个路径
  ignored-services: "*" # 忽略所有服务ID，服务ID不能直接访问了
  prefix: /kuang # 前缀
```

主启动类

```
@SpringBootApplication
@EnableZuulProxy //开启zuul
public class Zuul_9527 {

    public static void main(String[] args) {
        SpringApplication.run(Zuul_9527.class,args);
    }
}
```

测试：  
未配置路由网关，访问方式：可以通过服务名访问，暴露服务名不安全  
![](https://img-blog.csdnimg.cn/20210426203737885.png)  
增加 zuul 配置后，不可以通过服务名访问了  
![](https://img-blog.csdnimg.cn/20210426204027371.png)

### 9. Spring Cloud Config 分布式配置

Spring Cloud Config 为分布式系统中的外部配置提供服务器和客户端支持。使用 Config Server，您可以在所有环境中管理应用程序的外部属性。客户端和服务器上的概念映射与 Spring Environment 和 PropertySource 抽象相同，因此它们与 Spring 应用程序非常契合，但可以与任何以任何语言运行的应用程序一起使用。随着应用程序通过从开发人员到测试和生产的部署流程，您可以管理这些环境之间的配置，并确定应用程序具有迁移时需要运行的一切。服务器存储后端的默认实现使用 git，因此它轻松支持标签版本的配置环境，以及可以访问用于管理内容的各种工具。很容易添加替代实现，并使用 Spring 配置将其插入。

**概述  
分布式系统面临的–配置文件问题**

微服务意味着要将单体应用中的业务拆分成一个个子服务，每个服务的粒度相对较小，因此系统中会出现大量的服务，由于每个服务都需要必要的配置信息才能运行，所以一套集中式的，动态的配置管理设施是必不可少的。spring cloud 提供了 configServer 来解决这个问题，我们每一个微服务自己带着一个 application.yml，那上百个的配置文件修改起来，令人头疼！

**什么是 SpringCloud config 分布式配置中心？**  
![](https://img-blog.csdnimg.cn/20210426212947119.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
​ spring cloud config 为微服务架构中的微服务提供集中化的外部支持，配置服务器为各个不同微服务应用的所有环节提供了一个**中心化的外部配置**。

​ spring cloud config 分为**服务端**和**客户端**两部分。

​ 服务端也称为 **分布式配置中心**，它是一个独立的微服务应用，用来连接配置服务器并为客户端提供获取配置信息，加密，解密信息等访问接口。

​ 客户端则是**通过指定的配置中心来管理应用资源，以及与业务相关的配置内容，并在启动的时候从配置中心获取和加载配置信息**。配置服务器默认采用 git 来存储配置信息，这样就有助于对环境配置进行版本管理。并且可用通过 git 客户端工具来方便的管理和访问配置内容。

**spring cloud config 分布式配置中心能干嘛？**

*   集中式管理配置文件
*   不同环境，不同配置，动态化的配置更新，分环境部署，比如 /dev /test /prod /beta /release
*   运行期间动态调整配置，不再需要在每个服务部署的机器上编写配置文件，服务会向配置中心统一拉取配置自己的信息
*   当配置发生变动时，服务不需要重启，即可感知到配置的变化，并应用新的配置
*   将配置信息以 REST 接口的形式暴露

#### 9.1 服务端与 git 整合

**spring cloud config 分布式配置中心与 GitHub 整合**

​ 由于 spring cloud config 默认使用 git 来存储配置文件 (也有其他方式，比如自持 SVN 和本地文件)，但是最推荐的还是 git ，而且使用的是 http / https 访问的形式。

案例：  
新建 springcloud-config-server-3344 模块导入 pom.xml 依赖

```
<dependencies>
    <!--web-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <!--config-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-config-server</artifactId>
        <version>2.1.1.RELEASE</version>
    </dependency>
    <!--actuator完善监控信息-->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
</dependencies>
```

resource 下创建 application.yml 配置文件，Spring Cloud Config 服务器从 git 存储库（必须提供）为远程客户端提供配置：

```
server:
  port: 3344

spring:
  application:
    name: springcloud-config-server
  cloud: #连接码云远程仓库
    config:
      server:
        git:
          uri: https://gitee.com/Filwaod/springcloud-config.git # https的url
```

主启动类

```
@EnableConfigServer // 开启spring cloud config server服务
@SpringBootApplication
public class Config_server_3344 {
    public static void main(String[] args) {
        SpringApplication.run(Config_server_3344.class,args);
    }
}
```

上传一个配置文件到远程仓库，内容如下

```
spring:
  profiles:
    active: dev

---
spring:
  profiles: dev
  application:
    name: springcloud-config-dev

---
spring:
  profiles: test
  application:
    name: springcloud-config-test
```

HTTP 服务具有以下格式的资源：

```
/{application}/{profile}[/{label}]
/{application}-{profile}.yml
/{label}/{application}-{profile}.yml
/{application}-{profile}.properties
/{label}/{application}-{profile}.properties
```

开启 3344 服务，测试能不能访问到  
![](https://img-blog.csdnimg.cn/2021042621353480.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
![](https://img-blog.csdnimg.cn/20210426213608161.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)  
服务端是 ok 的

#### 9.2 客户端与 git 整合

新建一个 springcloud-config-client-3355 模块，并导入依赖

```
<dependencies>
    <!--config-->
    <dependency>
        <groupId>org.springframework.cloud</groupId>
        <artifactId>spring-cloud-starter-config</artifactId>
        <version>2.1.1.RELEASE</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
</dependencies>
```

resources 下创建 application.yml 和 bootstrap.yml 配置文件，bootstrap 比 application 级别更高，属于系统配置，而 application 属于用户配置

bootstrap.yml

```
spring:
  cloud:
    config:
      name: config-client # 从git上要读取的文件名，不要后缀
      profile: dev # 读取什么环境的配置
      label: master # 哪个分支
      uri: http://localhost:3344 # 客户端url
```

application.yml

```
spring:
  application:
    name: springcloud-config-server-3355
```

创建 controller 包下的 ConfigClientController.java 用于测试

```
@RestController
public class ConfigClientController {

    @Value("${spring.application.name}")
    private String applicationName;

    @Value("${eureka.client.service-url.defaultZone}")
    private String eurekaServer;

    @Value("${server.port}")
    private String port;

    @RequestMapping("/config")
    public String getConfig(){
        return "applicationName: "+applicationName +"\n"
                +"eurekaServer: "+eurekaServer+"\n"
                +"port: "+port;
    }
}
```

主启动类

```
@SpringBootApplication
public class ConfigClient {
    public static void main(String[] args) {
        SpringApplication.run(ConfigClient.class,args);
    }
}
```

上传一个 springcloud-config 到远程仓库

```
spring:
  profiles:
    active: dev

---

server:
  port: 9090

spring:
  profiles: dev
  application:
    name: springcloud-config-dev
    
eureka:
  client:
    service-url:
      defaultZone: http://eureka7004.com:7004/eureka/
      
---

server:
  port: 7070

spring:
  profiles: test
  application:
    name: springcloud-config-test

eureka:
  client:
    service-url:
      defaultZone: http://eureka7004.com:7004/eureka/
```

访问：http://localhost:9090/config/，端口号看启动信息  
![](https://img-blog.csdnimg.cn/20210427200752309.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)

#### 9.3 案例

新建 springcloud-config-eureka-7002 模块，并将原来的 springcloud-eureka-7002 模块下的内容拷贝的该模块。  
导入依赖

```
<!--config-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-config</artifactId>
    <version>2.1.1.RELEASE</version>
</dependency>
```

清空该模块的 application.yml 配置，并新建 bootstrap.yml 连

```
spring:
  cloud:
    config:
      name: config-eureka # 仓库中的配置文件名称
      label: master
      profile: dev
      uri: http://localhost:3344
```

修改启动类

```
@EnableEurekaServer
@SpringBootApplication
public class ConfigEurekaServer_7002 {
    public static void main(String[] args) {
        SpringApplication.run(ConfigEurekaServer_7002.class,args);
    }
}
```

启动 Config_Server_3344，并访问 http://localhost:3344/config-eureka-dev.yml 测试

新建 springcloud-config-provider-dept-8001 模块并拷贝 springcloud-provider-dept-8001 的内容  
导入依赖

```
<!--config-->
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-config</artifactId>
    <version>2.1.1.RELEASE</version>
</dependency>
```

清空 application.yml 、新建 bootstrap.yml 配置文件并配置

```
spring:
  cloud:
    config:
      name: config-dept
      label: master
      profile: dev
      uri: http://localhost:3344
```

修改主启动类，测试

### 10. 所有代码

**完整代码：**[https://gitee.com/Filwaod/springcloud](https://gitee.com/Filwaod/springcloud)

### 11. 总结

**使用所有组件的四步：**

1. 导入依赖  
2. 编写配置文件  
3. 开启这个功能  
@EnableXXX  
4. 配置这个类

**学习完 Spring Cloud NetFlix 总结图**  
![](https://img-blog.csdnimg.cn/20210513143542447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQyNjY1NzQ1,size_16,color_FFFFFF,t_70)