> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/qq_48556886/article/details/123956167?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171784207416800180635107%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171784207416800180635107&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-123956167-null-null.142^v100^pc_search_result_base3&utm_term=%E7%8B%82%E7%A5%9Espringboot%E7%AC%94%E8%AE%B0&spm=1018.2226.3001.4187)

#### 目录

*   [P1、Hello,World！](#P1HelloWorld_8)
*   *   [1.1、回顾什么是 Spring](#11Spring_12)
    *   [1.2、Spring 是如何简化 Java 开发的](#12SpringJava_20)
    *   [1.3、什么是 SpringBoot](#13SpringBoot_29)
    *   [1.4、准备工作](#14_58)
    *   [1.5、创建基础项目说明](#15_72)
    *   [1.6、pom.xml 分析](#16pomxml__108)
    *   [1.7、编写一个 http 接口](#17http_153)
    *   [1.8、将项目打成 jar 包，点击 maven 的 package](#18jar_maven_package_177)
*   [P2、运行原理初探](#P2_216)
*   *   [2.1、父依赖](#21_222)
    *   [2.2、启动器 spring-boot-starter](#22_springbootstarter_250)
    *   [2.3、默认的主启动类](#23_269)
    *   [2.4、@SpringBootApplication](#24SpringBootApplication_287)
    *   [2.5、@ComponentScan](#25ComponentScan_310)
    *   [2.6、@SpringBootConfiguration](#26SpringBootConfiguration_316)
    *   [2.7、@EnableAutoConfiguration](#27EnableAutoConfiguration_337)
    *   [2.8、spring.factories](#28springfactories_431)
    *   [2.9、不简单的方法](#29_459)
    *   [2.10、SpringApplication](#210SpringApplication_476)
    *   [2.11、run 方法流程分析](#211run_500)
*   [P3、yaml 配置注入](#P3yaml_505)
*   *   [3.1、配置文件](#31_509)
    *   [3.2、yaml 概述](#32yaml_525)
    *   [3.3、yaml 基础语法](#33yaml_548)
    *   [3.4、yaml 注入配置文件](#34yaml_629)
    *   [3.5、加载指定的配置文件](#35_781)
    *   [3.6、配置文件占位符](#36_811)
    *   [3.7、回顾 properties 配置](#37properties_831)
    *   [3.8、对比小结](#38_889)
*   [P4、JSR303 数据校验及多环境切换](#P4JSR303_911)
*   *   [4.1、先看看如何使用](#41_915)
    *   [4.2、常见参数](#42_936)
    *   [4.3、多配置文件](#43_973)
    *   [4.4、yaml 的多文档块](#44yaml_993)
    *   [4.5、配置文件加载位置](#45_1022)
    *   [4.6、拓展，运维小技巧](#46_1050)
*   [P5、自动配置原理](#P5_1058)
*   *   [5.1、分析自动配置原理](#51_1068)
    *   [5.2、精髓](#52_1143)
    *   [5.3、了解：@Conditional](#53Conditional_1157)
*   [P6、自定义 starter](#P6starter_1188)
*   *   [6.1、说明](#61_1192)
    *   [6.2、编写启动器](#62_1208)
    *   [6.3、新建项目测试我们自己写的启动器](#63_1339)
*   [P7、SpringBoot 整合 JDBC](#P7SpringBootJDBC_1383)
*   *   [7.1、SpringData 简介](#71SpringData_1385)
    *   [7.2、创建测试项目测试数据源](#72_1398)
    *   [7.3、JDBCTemplate](#73JDBCTemplate_1475)
    *   [7.4、测试](#74_1490)
    
    *   [7.5、原理探究 ：](#75__1574)
*   [P8、SpringBoot 整合 Druid](#P8SpringBootDruid_1604)
*   *   [8.1、Druid 简介](#81Druid_1606)
    *   [8.2、配置数据源](#82_1650)
    *   [8.3、配置 Druid 数据源监控](#83Druid_1787)
*   [P9、SpringBoot 整合 mybatis](#P9SpringBoot_mybatis_1850)
*   *   [9.1、导入 mybatis 所需要的依赖](#91mybatis_1852)
    *   [9.2、配置数据库连接信息](#92_1863)
    *   [9.3、我们这里就是用默认的数据源了；先去测试一下连接是否成功！](#93_1872)
    *   [9.4、创建实体类](#94_1898)
    *   [9.5、配置 Mapper 接口类](#95Mapper_1954)
    *   [9.6、对应 Mapper 映射文件](#96Mapper_1984)
    *   [9.7、maven 配置资源过滤问题](#97maven_2016)
    *   [9.8、SpringBoot 整合！](#98SpringBoot__2030)
    *   [9.9、编写 controller](#99controller_2075)
    *   [9.10、启动项目访问进行测试！](#910_2134)
    *   [注：配置数据库连接信息（不变）](#_2154)
*   [P10、Web 开发静态资源处理](#P10Web_2189)
*   *   [10.1、简介](#101_2193)
    *   [10.2、静态资源映射规则](#102_2220)
    *   [10.3、什么是 webjars 呢？](#103webjars__2265)
    *   [10.4、第二种静态资源映射规则](#104_2291)
    *   [10.5、自定义静态资源路径](#105_2328)
*   [P11、Thymeleaf 模板引擎](#P11Thymeleaf_2394)
*   *   [11.1、模板引擎](#111_2396)
    *   [11.2、引入 Thymeleaf](#112Thymeleaf_2414)
    *   [11.3、Thymeleaf 分析](#113Thymeleaf_2440)
    *   [11.4、Thymeleaf 语法学习](#114Thymeleaf__2506)
*   [P12、MVC 自动配置原理](#P12MVC_2679)
*   *   [12.1、官网阅读](#121_2681)
    *   [12.2、ContentNegotiatingViewResolver 内容协商视图解析器](#122ContentNegotiatingViewResolver__2733)
    *   [12.3、转换器和格式化器](#123_2839)
    *   [12.4、修改 SpringBoot 的默认配置](#124SpringBoot_2876)
    *   [12.5、全面接管 SpringMVC](#125SpringMVC_2961)
*   [P13、页面国际化](#P13_3024)
*   *   [13.1、准备工作](#131_3028)
    *   [13.2、配置文件编写](#132_3036)
    *   [13.3、配置文件生效探究](#133_3106)
    *   [13.4、配置页面国际化值](#134_3143)
    *   [13.5、配置国际化解析](#135_3157)
*   [P14、集成 Swagger 终极版](#P14Swagger_3262)
*   *   [14.1、Swagger 简介](#141Swagger_3271)
    *   [14.2、SpringBoot 集成 Swagger](#142SpringBootSwagger_3296)
    *   [14.3、配置 Swagger](#143Swagger_3343)
    *   [14.4、配置扫描接口](#144_3384)
    *   [14.5、配置 Swagger 开关](#145Swagger_3438)
    *   [14.6、配置 API 分组](#146API_3482)
    *   [14.7、实体配置](#147_3518)
    *   [14.8、常用注解](#148_3551)
    *   [14.9、拓展：其他皮肤](#149_3582)
*   [P15、异步、定时、邮件任务](#P15_3637)
*   *   [15.1、异步任务](#151_3644)
    *   [15.2、定时任务](#152_3726)
    *   [15.3、邮件任务](#153_3812)
*   [P16、富文本编辑器](#P16_3924)
*   *   [16.1、简介](#161_3926)
    *   [16.2、Editor.md](#162Editormd_3964)
    *   [16.3、基础工程搭建](#163_3976)
    *   [16.4、文章编辑整合（重点）](#164_4072)
    *   [16.5、文章展示](#165_4285)
*   [P17、Dubbo 和 Zookeeper 集成](#P17DubboZookeeper_4356)
*   *   [17.1、什么是分布式系统？](#171_4360)
    *   [17.2、Dubbo 文档](#172Dubbo_4370)
    *   *   [单一应用架构](#_4378)
        *   [垂直应用架构](#_4394)
        *   [分布式服务架构](#_4404)
        *   [流动计算架构](#_4410)
        *   [Dubbo](#Dubbo_4436)
        *   [Dubbo 环境搭建](#Dubbo_4472)
        *   [Window 下安装 zookeeper](#Windowzookeeper_4478)
        *   [window 下安装 dubbo-admin](#windowdubboadmin_4526)
    *   [17.3、SpringBoot + Dubbo + zookeeper](#173SpringBoot__Dubbo__zookeeper_4572)
    *   *   [框架搭建](#_4574)
        *   [服务提供者](#_4623)
        *   [服务消费者](#_4706)
        *   [启动测试](#_4806)
*   [P18、集成 SpringSecurity](#P18SpringSecurity_4824)
*   *   [18.1、安全简介](#181_4826)
    *   [18.2、实战测试](#182_4852)
    *   *   [18.2.1、实验环境搭建](#1821_4854)
        *   [18.2.2、认识 SpringSecurity](#1822SpringSecurity_4920)
        *   [18.2.3、认证和授权](#1823_4944)
        *   [18.2.4、权限控制和注销](#1824_5062)
        *   [18.2.5、记住我](#1825_5211)
        *   [18.2.6、定制登录页](#1826_5240)
    *   [18.3、完整配置代码](#183_5309)

本篇学习链接：  
[【狂神说 Java】SpringBoot 最新教程 IDEA 版通俗易懂](https://www.bilibili.com/video/BV1PE411i7CV?spm_id_from=333.999.0.0)

“本文章摘抄于狂神的学习视频，并结合了微信公众号狂神说的文档，只用于自身学习使用！”

P1、Hello,World！
---------------

SpringBoot 简介

### 1.1、回顾什么是 Spring

Spring 是一个开源框架，2003 年兴起的一个轻量级的 Java 开发框架，作者：Rod Johnson 。

**Spring 是为了解决企业级应用开发的复杂性而创建的，简化开发。**

### 1.2、Spring 是如何简化 Java 开发的

为了降低 Java 开发的复杂性，Spring 采用了以下 4 种关键策略：

1.  基于 POJO 的轻量级和最小侵入性编程，所有东西都是 bean；
2.  通过 IOC，依赖注入（DI）和面向接口实现松耦合；
3.  基于切面（AOP）和惯例进行声明式编程；
4.  通过切面和模版减少样式代码，RedisTemplate，xxxTemplate；

### 1.3、什么是 SpringBoot

学过 javaweb 的同学就知道，开发一个 web 应用，从最初开始接触 Servlet 结合 Tomcat, 跑出一个 Hello Wolrld 程序，是要经历特别多的步骤；后来就用了框架 Struts，再后来是 SpringMVC，到了现在的 SpringBoot，过一两年又会有其他 web 框架出现；你们有经历过框架不断的演进，然后自己开发项目所有的技术也在不断的变化、改造吗？建议都可以去经历一遍；

言归正传，什么是 SpringBoot 呢，就是一个 javaweb 的开发框架，和 SpringMVC 类似，对比其他 javaweb 框架的好处，官方说是简化开发，约定大于配置， you can “just run”，能迅速的开发 web 应用，几行代码开发一个 http 接口。

所有的技术框架的发展似乎都遵循了一条主线规律：从一个复杂应用场景 衍生 一种规范框架，人们只需要进行各种配置而不需要自己去实现它，这时候强大的配置功能成了优点；发展到一定程度之后，人们根据实际生产应用情况，选取其中实用功能和设计精华，重构出一些轻量级的框架；之后为了提高开发效率，嫌弃原先的各类配置过于麻烦，于是开始提倡 “约定大于配置”，进而衍生出一些一站式的解决方案。

是的这就是 Java 企业级应用 ->J2EE->spring->springboot 的过程。

随着 Spring 不断的发展，涉及的领域越来越多，项目整合开发需要配合各种各样的文件，慢慢变得不那么易用简单，违背了最初的理念，甚至人称配置地狱。Spring Boot 正是在这样的一个背景下被抽象出来的开发框架，目的为了让大家更容易的使用 Spring 、更容易的集成各种常用的中间件、开源软件；

Spring Boot 基于 Spring 开发，Spirng Boot 本身并不提供 Spring 框架的核心特性以及扩展功能，只是用于快速、敏捷地开发新一代基于 Spring 框架的应用程序。也就是说，它并不是用来替代 Spring 的解决方案，而是和 Spring 框架紧密结合用于提升 Spring 开发者体验的工具。Spring Boot 以**约定大于配置的核心思想**，默认帮我们进行了很多设置，多数 Spring Boot 应用只需要很少的 Spring 配置。同时它集成了大量常用的第三方库配置（例如 Redis、MongoDB、Jpa、RabbitMQ、Quartz 等等），Spring Boot 应用中这些第三方库几乎可以零配置的开箱即用。

简单来说就是 SpringBoot 其实不是什么新的框架，它默认配置了很多框架的使用方式，就像 maven 整合了所有的 jar 包，spring boot 整合了所有的框架 。

Spring Boot 出生名门，从一开始就站在一个比较高的起点，又经过这几年的发展，生态足够完善，Spring Boot 已经当之无愧成为 Java 领域最热门的技术。

**Spring Boot 的主要优点：**

*   为所有 Spring 开发者更快的入门
*   **开箱即用**，提供各种默认配置来简化项目配置
*   内嵌式容器简化 Web 项目
*   没有冗余代码生成和 XML 配置的要求

真的很爽，我们快速去体验开发个接口的感觉吧！

Hello，World

### 1.4、准备工作

我们将学习如何快速的创建一个 Spring Boot 应用，并且实现一个简单的 Http 请求处理。通过这个例子对 Spring Boot 有一个初步的了解，并体验其结构简单、开发快速的特性。

我的环境准备：

*   java version “1.8.0_181”
*   Maven-3.6.1
*   SpringBoot 2.x 最新版

开发工具：

*   IDEA

### 1.5、创建基础项目说明

Spring 官方提供了非常方便的工具让我们快速构建应用

Spring Initializr：https://start.spring.io/

**项目创建方式一：** 使用 Spring Initializr 的 Web 页面创建项目

1、打开 https://start.spring.io/

2、填写项目信息

3、点击”Generate Project“按钮生成项目；下载此项目

4、解压项目包，并用 IDEA 以 Maven 项目导入，一路下一步即可，直到项目导入完毕。

5、如果是第一次使用，可能速度会比较慢，包比较多、需要耐心等待一切就绪。

**项目创建方式二：** 使用 IDEA 直接创建项目

1.  创建一个新项目
2.  选择 spring initalizr ， 可以看到默认就是去官网的快速构建工具那里实现
3.  填写项目信息
4.  选择初始化的组件（初学勾选 Web 即可）
5.  填写项目路径
6.  等待项目构建成功

**项目结构分析：**

通过上面步骤完成了基础项目的创建。就会自动生成以下文件。

1.  程序的主启动类
2.  一个 application.properties 配置文件
3.  一个 测试类
4.  一个 pom.xml

### 1.6、pom.xml 分析

打开 pom.xml，看看 Spring Boot 项目的依赖：

```
<!-- 父依赖 -->
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.2.5.RELEASE</version>
    <relativePath/>
</parent>

<dependencies>
    <!-- web场景启动器 -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-web</artifactId>
    </dependency>
    <!-- springboot单元测试 -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-test</artifactId>
        <scope>test</scope>
        <!-- 剔除依赖 -->
        <exclusions>
            <exclusion>
                <groupId>org.junit.vintage</groupId>
                <artifactId>junit-vintage-engine</artifactId>
            </exclusion>
        </exclusions>
    </dependency>
</dependencies>

<build>
    <plugins>
        <!-- 打包插件 -->
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
    </plugins>
</build>
```

### 1.7、编写一个 http 接口

1、在主程序的同级目录下，新建一个 controller 包，一定要在同级目录下，否则识别不到

2、在包中新建一个 HelloController 类

```
@RestController
public class HelloController {

    @RequestMapping("/hello")
    public String hello() {
        return "Hello World";
    }
    
}
```

3、编写完毕后，从主程序启动项目，浏览器发起请求，看页面返回；控制台输出了 Tomcat 访问的端口号！

![](https://img-blog.csdnimg.cn/img_convert/944eed3d38d6a5521b7c37a939bdb200.png)

简单几步，就完成了一个 web 接口的开发，SpringBoot 就是这么简单。所以我们常用它来建立我们的微服务项目！

### 1.8、将项目打成 jar 包，点击 maven 的 package

![](https://img-blog.csdnimg.cn/img_convert/e549b72b933edcd30eece147f8930c57.png)

如果遇到以上错误，可以配置打包时 跳过项目运行测试用例

```
<!--
    在工作中,很多情况下我们打包是不想执行测试用例的
    可能是测试用例不完事,或是测试用例会影响数据库数据
    跳过测试用例执
    -->
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-surefire-plugin</artifactId>
    <configuration>
        <!--跳过项目运行测试用例-->
        <skipTests>true</skipTests>
    </configuration>
</plugin>
```

如果打包成功，则会在 target 目录下生成一个 jar 包

![](https://img-blog.csdnimg.cn/img_convert/06db9a34bfad5a5dc3578fe6f695632c.png)

打成了 jar 包后，就可以在任何地方运行了！OK

**彩蛋**

如何更改启动时显示的字符拼成的字母，SpringBoot 呢？也就是 banner 图案；

只需一步：到项目下的 resources 目录下新建一个 banner.txt 即可。

图案可以到：https://www.bootschool.net/ascii 这个网站生成，然后拷贝到文件中即可！

![](https://img-blog.csdnimg.cn/img_convert/6a867ca2eda07df87a85647428dac6c9.png)

P2、运行原理初探
---------

我们之前写的 HelloSpringBoot，到底是怎么运行的呢，Maven 项目，我们一般从 pom.xml 文件探究起；

> ==================================**pom.xml** ==================================

### 2.1、父依赖

其中它主要是依赖一个父项目，主要是管理项目的资源过滤及插件！

```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>2.2.5.RELEASE</version>
    <relativePath/> <!-- lookup parent from repository -->
</parent>
```

点进去，发现还有一个父依赖

```
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-dependencies</artifactId>
    <version>2.2.5.RELEASE</version>
    <relativePath>../../spring-boot-dependencies</relativePath>
</parent>
```

这里才是真正管理 SpringBoot 应用里面所有依赖版本的地方，SpringBoot 的版本控制中心；

**以后我们导入依赖默认是不需要写版本；但是如果导入的包没有在依赖中管理着就需要手动配置版本了；**

### 2.2、启动器 [spring-boot](https://so.csdn.net/so/search?q=spring-boot&spm=1001.2101.3001.7020)-starter

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

**springboot-boot-starter-xxx**：就是 spring-boot 的场景启动器

**spring-boot-starter-web**：帮我们导入了 web 模块正常运行所依赖的组件；

SpringBoot 将所有的功能场景都抽取出来，做成一个个的 starter （启动器），只需要在项目中引入这些 starter 即可，所有相关的依赖都会导入进来 ， 我们要用什么功能就导入什么样的场景启动器即可 ；我们未来也可以自己自定义 starter；

> ================================== **主启动类** ==================================

分析完了 pom.xml 来看看这个启动类

### 2.3、默认的主启动类

```
//@SpringBootApplication 来标注一个主程序类
//说明这是一个Spring Boot应用
@SpringBootApplication
public class SpringbootApplication {

   public static void main(String[] args) {
     //以为是启动了一个方法，没想到启动了一个服务
      SpringApplication.run(SpringbootApplication.class, args);
   }

}
```

但是 ** 一个简单的启动类并不简单！** 我们来分析一下这些注解都干了什么

### 2.4、@SpringBootApplication

作用：标注在某个类上说明这个类是 SpringBoot 的主配置类 ， SpringBoot 就应该运行这个类的 main 方法来启动 SpringBoot 应用；

进入这个注解：可以看到上面还有很多其他注解！

```
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(
    excludeFilters = {@Filter(
    type = FilterType.CUSTOM,
    classes = {TypeExcludeFilter.class}
), @Filter(
    type = FilterType.CUSTOM,
    classes = {AutoConfigurationExcludeFilter.class}
)}
)
public @interface SpringBootApplication {
    // ......
}
```

### 2.5、@ComponentScan

这个注解在 Spring 中很重要 , 它对应 XML 配置中的元素。

作用：自动扫描并加载符合条件的组件或者 bean ， 将这个 bean 定义加载到 IOC 容器中

### 2.6、@SpringBootConfiguration

作用：SpringBoot 的配置类 ，标注在某个类上 ， 表示这是一个 SpringBoot 的配置类；

我们继续进去这个注解查看

```
// 点进去得到下面的 @Component
@Configuration
public @interface SpringBootConfiguration {}

@Component
public @interface Configuration {}
```

这里的 @Configuration，说明这是一个配置类 ，配置类就是对应 Spring 的 xml 配置文件；

里面的 @Component 这就说明，启动类本身也是 Spring 中的一个组件而已，负责启动应用！

我们回到 SpringBootApplication 注解中继续看。

### 2.7、@EnableAutoConfiguration

**@EnableAutoConfiguration ：开启自动配置功能**

以前我们需要自己配置的东西，而现在 SpringBoot 可以自动帮我们配置 ；@EnableAutoConfiguration 告诉 SpringBoot 开启自动配置功能，这样自动配置才能生效；

点进注解接续查看：

**@AutoConfigurationPackage ：自动配置包**

```
@Import({Registrar.class})
public @interface AutoConfigurationPackage {
}
```

**@import** ：Spring 底层注解 @import ， 给容器中导入一个组件

Registrar.class 作用：将主启动类的所在包及包下面所有子包里面的所有组件扫描到 Spring 容器 ；

这个分析完了，退到上一步，继续看

**@Import({AutoConfigurationImportSelector.class}) ：给容器导入组件 ；**

AutoConfigurationImportSelector ：自动配置导入选择器，那么它会导入哪些组件的选择器呢？我们点击去这个类看源码：

1、这个类中有一个这样的方法

```
// 获得候选的配置
protected List<String> getCandidateConfigurations(AnnotationMetadata metadata, AnnotationAttributes attributes) {
    //这里的getSpringFactoriesLoaderFactoryClass（）方法
    //返回的就是我们最开始看的启动自动导入配置文件的注解类；EnableAutoConfiguration
    List<String> configurations = SpringFactoriesLoader.loadFactoryNames(this.getSpringFactoriesLoaderFactoryClass(), this.getBeanClassLoader());
    Assert.notEmpty(configurations, "No auto configuration classes found in META-INF/spring.factories. If you are using a custom packaging, make sure that file is correct.");
    return configurations;
}
```

2、这个方法又调用了 SpringFactoriesLoader 类的静态方法！我们进入 SpringFactoriesLoader 类 loadFactoryNames() 方法

```
public static List<String> loadFactoryNames(Class<?> factoryClass, @Nullable ClassLoader classLoader) {
    String factoryClassName = factoryClass.getName();
    //这里它又调用了 loadSpringFactories 方法
    return (List)loadSpringFactories(classLoader).getOrDefault(factoryClassName, Collections.emptyList());
}
```

3、我们继续点击查看 loadSpringFactories 方法

```
private static Map<String, List<String>> loadSpringFactories(@Nullable ClassLoader classLoader) {
    //获得classLoader ， 我们返回可以看到这里得到的就是EnableAutoConfiguration标注的类本身
    MultiValueMap<String, String> result = (MultiValueMap)cache.get(classLoader);
    if (result != null) {
        return result;
    } else {
        try {
            //去获取一个资源 "META-INF/spring.factories"
            Enumeration<URL> urls = classLoader != null ? classLoader.getResources("META-INF/spring.factories") : ClassLoader.getSystemResources("META-INF/spring.factories");
            LinkedMultiValueMap result = new LinkedMultiValueMap();

            //将读取到的资源遍历，封装成为一个Properties
            while(urls.hasMoreElements()) {
                URL url = (URL)urls.nextElement();
                UrlResource resource = new UrlResource(url);
                Properties properties = PropertiesLoaderUtils.loadProperties(resource);
                Iterator var6 = properties.entrySet().iterator();

                while(var6.hasNext()) {
                    Entry<?, ?> entry = (Entry)var6.next();
                    String factoryClassName = ((String)entry.getKey()).trim();
                    String[] var9 = StringUtils.commaDelimitedListToStringArray((String)entry.getValue());
                    int var10 = var9.length;

                    for(int var11 = 0; var11 < var10; ++var11) {
                        String factoryName = var9[var11];
                        result.add(factoryClassName, factoryName.trim());
                    }
                }
            }

            cache.put(classLoader, result);
            return result;
        } catch (IOException var13) {
            throw new IllegalArgumentException("Unable to load factories from location [META-INF/spring.factories]", var13);
        }
    }
}
```

4、发现一个多次出现的文件：spring.factories，全局搜索它

### 2.8、spring.factories

我们根据源头打开 spring.factories ， 看到了很多自动配置的文件；这就是自动配置根源所在！

![](https://img-blog.csdnimg.cn/img_convert/96fcad1886f23acaba2d6e418b5be170.png)

**WebMvcAutoConfiguration**

我们在上面的自动配置类随便找一个打开看看，比如 ：WebMvcAutoConfiguration

![](https://img-blog.csdnimg.cn/img_convert/70e07fb65a5768f3cd1b1b46f264869a.png)

可以看到这些一个个的都是 JavaConfig 配置类，而且都注入了一些 Bean，可以找一些自己认识的类，看着熟悉一下！

所以，自动配置真正实现是从 classpath 中搜寻所有的 META-INF/spring.factories 配置文件 ，并将其中对应的 org.springframework.boot.autoconfigure. 包下的配置项，通过反射实例化为对应标注了 @Configuration 的 JavaConfig 形式的 IOC 容器配置类 ， 然后将这些都汇总成为一个实例并加载到 IOC 容器中。

**结论：**

1.  SpringBoot 在启动的时候从类路径下的 META-INF/spring.factories 中获取 EnableAutoConfiguration 指定的值
2.  将这些值作为自动配置类导入容器 ， 自动配置类就生效 ， 帮我们进行自动配置工作；
3.  整个 J2EE 的整体解决方案和自动配置都在 springboot-autoconfigure 的 jar 包中；
4.  它会给容器中导入非常多的自动配置类 （xxxAutoConfiguration）, 就是给容器中导入这个场景需要的所有组件 ， 并配置好这些组件 ；
5.  有了自动配置类 ， 免去了我们手动编写配置注入功能组件等的工作；

**现在大家应该大概的了解了下，SpringBoot 的运行原理，后面我们还会深化一次！**

> ==================================**SpringApplication** ==================================

### 2.9、不简单的方法

我最初以为就是运行了一个 main 方法，没想到却开启了一个服务；

```
@SpringBootApplication
public class SpringbootApplication {
    public static void main(String[] args) {
        SpringApplication.run(SpringbootApplication.class, args);
    }
}
```

**SpringApplication.run 分析**

分析该方法主要分两部分，一部分是 SpringApplication 的实例化，二是 run 方法的执行；

### 2.10、SpringApplication

**这个类主要做了以下四件事情：**

1、推断应用的类型是普通的项目还是 Web 项目

2、查找并加载所有可用初始化器 ， 设置到 initializers 属性中

3、找出所有的应用程序监听器，设置到 listeners 属性中

4、推断并设置 main 方法的定义类，找到运行的主类

查看构造器：

```
public SpringApplication(ResourceLoader resourceLoader, Class... primarySources) {
    // ......
    this.webApplicationType = WebApplicationType.deduceFromClasspath();
    this.setInitializers(this.getSpringFactoriesInstances();
    this.setListeners(this.getSpringFactoriesInstances(ApplicationListener.class));
    this.mainApplicationClass = this.deduceMainApplicationClass();
}
```

### 2.11、run 方法流程分析

![](https://img-blog.csdnimg.cn/img_convert/a6e1f5b3b53c4b22e84245962b3d202f.png)  
跟着源码和这幅图就可以一探究竟了！

P3、yaml 配置注入
------------

yaml 语法学习

### 3.1、配置文件

SpringBoot 使用一个全局的配置文件 ， 配置文件名称是固定的

*   application.properties
*   *   语法结构 ：key=value
*   application.yml
*   *   语法结构 ：key：空格 value

**配置文件的作用** ：修改 SpringBoot 自动配置的默认值，因为 SpringBoot 在底层都给我们自动配置好了；

比如我们可以在配置文件中修改 Tomcat 默认启动的端口号！测试一下！

*   server.port=8081

### 3.2、yaml 概述

YAML 是 “YAML Ain’t a Markup Language” （YAML 不是一种标记语言）的递归缩写。在开发的这种语言时，YAML 的意思其实是：“Yet Another Markup Language”（仍是一种标记语言）

**这种语言以数据作为中心，而不是以标记语言为重点！**

以前的配置文件，大多数都是使用 xml 来配置；比如一个简单的端口配置，我们来对比下 yaml 和 xml

传统 xml 配置：

```
<server>
    <port>8081<port>
</server>
```

yaml 配置：

```
server：
  prot: 8080
```

### 3.3、yaml 基础语法

说明：语法要求严格！

1、空格不能省略

2、以缩进来控制层级关系，只要是左边对齐的一列数据都是同一个层级的。

3、属性和值的大小写都是十分敏感的。

**字面量：普通的值 [数字，布尔值，字符串]**

字面量直接写在后面就可以 ， 字符串默认不用加上双引号或者单引号；

```
k: v
```

注意：

*   “ ” 双引号，不会转义字符串里面的特殊字符 ， 特殊字符会作为本身想表示的意思；
    
    比如 ：name: “kuang \n shen” 输出 ：kuang 换行 shen
    
*   ‘’ 单引号，会转义特殊字符 ， 特殊字符最终会变成和普通字符一样输出
    
    比如 ：name: ‘kuang \n shen’ 输出 ：kuang \n shen
    

**对象、Map（键值对）**

```
#对象、Map格式
k: 
    v1:
    v2:
```

在下一行来写对象的属性和值得关系，注意缩进；比如：

```
student:
    name: qinjiang
    age: 3
```

行内写法

```
student: {name: qinjiang,age: 3}
```

**数组（ List、set ）**

用 - 值表示数组中的一个元素, 比如：

```
pets:
 - cat
 - dog
 - pig
```

行内写法

```
pets: [cat,dog,pig]
```

**修改 SpringBoot 的默认端口号**

配置文件中添加，端口号的参数，就可以切换端口；

```
server:  
  port: 8082
```

注入配置文件

yaml 文件更强大的地方在于，他可以给我们的实体类直接注入匹配值！

### 3.4、yaml 注入配置文件

1、在 springboot 项目中的 resources 目录下新建一个文件 application.yml

2、编写一个实体类 Dog；

```
package com.kuang.springboot.pojo;

@Component  //注册bean到容器中
public class Dog {
    private String name;
    private Integer age;
    
    //有参无参构造、get、set方法、toString()方法  
}
```

3、思考，我们原来是如何给 bean 注入属性值的！@Value，给狗狗类测试一下：

```
@Component //注册bean
public class Dog {
    @Value("阿黄")
    private String name;
    @Value("18")
    private Integer age;
}
```

4、在 SpringBoot 的测试类下注入狗狗输出一下；

```
@SpringBootTest
class DemoApplicationTests {

    @Autowired //将狗狗自动注入进来
    Dog dog;

    @Test
    public void contextLoads() {
        System.out.println(dog); //打印看下狗狗对象
    }

}
```

结果成功输出，@Value 注入成功，这是我们原来的办法对吧。

![](https://img-blog.csdnimg.cn/img_convert/90c7049a08847bca1d50462ab41c990c.png)

5、我们在编写一个复杂一点的实体类：Person 类

```
@Component //注册bean到容器中
public class Person {
    private String name;
    private Integer age;
    private Boolean happy;
    private Date birth;
    private Map<String,Object> maps;
    private List<Object> lists;
    private Dog dog;
    
    //有参无参构造、get、set方法、toString()方法  
}
```

6、我们来使用 yaml 配置的方式进行注入，大家写的时候注意区别和优势，我们编写一个 yaml 配置！

```
person:
  name: qinjiang
  age: 3
  happy: false
  birth: 2000/01/01
  maps: {k1: v1,k2: v2}
  lists:
   - code
   - girl
   - music
  dog:
    name: 旺财
    age: 1
```

7、我们刚才已经把 person 这个对象的所有值都写好了，我们现在来注入到我们的类中！

```
/*
@ConfigurationProperties作用：
将配置文件中配置的每一个属性的值，映射到这个组件中；
告诉SpringBoot将本类中的所有属性和配置文件中相关的配置进行绑定
参数 prefix = “person” : 将配置文件中的person下面的所有属性一一对应
*/
@Component //注册bean
@ConfigurationProperties(prefix = "person")
public class Person {
    private String name;
    private Integer age;
    private Boolean happy;
    private Date birth;
    private Map<String,Object> maps;
    private List<Object> lists;
    private Dog dog;
}
```

8、IDEA 提示，springboot 配置注解处理器没有找到，让我们看文档，我们可以查看文档，找到一个依赖！

![](https://img-blog.csdnimg.cn/img_convert/1ba98f0770460027e7cbaaa76d99d65b.png)

![](https://img-blog.csdnimg.cn/img_convert/26dbc3a32b218c8952785c13a4f3f8ac.png)

```
<!-- 导入配置文件处理器，配置文件进行绑定就会有提示，需要重启 -->
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-configuration-processor</artifactId>
  <optional>true</optional>
</dependency>
```

9、确认以上配置都 OK 之后，我们去测试类中测试一下：

```
@SpringBootTest
class DemoApplicationTests {

    @Autowired
    Person person; //将person自动注入进来

    @Test
    public void contextLoads() {
        System.out.println(person); //打印person信息
    }

}
```

结果：所有值全部注入成功！

![](https://img-blog.csdnimg.cn/img_convert/da20b17ba44f22bef2fdc81662b3b25c.png)

**yaml 配置注入到实体类完全 OK！**

课堂测试：

1、将配置文件的 key 值 和 属性的值设置为不一样，则结果输出为 null，注入失败

2、在配置一个 person2，然后将 @ConfigurationProperties(prefix = “person2”) 指向我们的 person2；

### 3.5、加载指定的配置文件

**@PropertySource ：** 加载指定的配置文件；

**@configurationProperties**：默认从全局配置文件中获取值；

1、我们去在 resources 目录下新建一个 **person.properties** 文件

```
name=kuangshen
```

2、然后在我们的代码中指定加载 person.properties 文件

```
@PropertySource(value = "classpath:person.properties")
@Component //注册bean
public class Person {

    @Value("${name}")
    private String name;

    ......  
}
```

3、再次输出测试一下：指定配置文件绑定成功！

![](https://img-blog.csdnimg.cn/img_convert/04d910e74f300da2f8eab727983f7974.png)

### 3.6、配置文件占位符

配置文件还可以编写占位符生成随机数

```
person:
    name: qinjiang${random.uuid} # 随机uuid
    age: ${random.int}  # 随机int
    happy: false
    birth: 2000/01/01
    maps: {k1: v1,k2: v2}
    lists:
      - code
      - girl
      - music
    dog:
      name: ${person.hello:other}_旺财
      age: 1
```

### 3.7、回顾 properties 配置

我们上面采用的 yaml 方法都是最简单的方式，开发中最常用的；也是 springboot 所推荐的！那我们来唠唠其他的实现方式，道理都是相同的；写还是那样写；配置文件除了 yml 还有我们之前常用的 properties ， 我们没有讲，我们来唠唠！

【注意】properties 配置文件在写中文的时候，会有乱码 ， 我们需要去 IDEA 中设置编码格式为 UTF-8；

settings–>FileEncodings 中配置；

![](https://img-blog.csdnimg.cn/img_convert/30e3569276787d7265d754be2fa9f816.png)

**测试步骤：**

1、新建一个实体类 User

```
@Component //注册bean
public class User {
    private String name;
    private int age;
    private String sex;
}
```

2、编辑配置文件 user.properties

```
user1.name=kuangshen
user1.age=18user1.sex=男
```

3、我们在 User 类上使用 @Value 来进行注入！

```
@Component //注册bean
@PropertySource(value = "classpath:user.properties")
public class User {
    //直接使用@value
    @Value("${user.name}") //从配置文件中取值
    private String name;
    @Value("#{9*2}")  // #{SPEL} Spring表达式
    private int age;
    @Value("男")  // 字面量
    private String sex;
}
```

4、Springboot 测试

```
user1.name=kuangshen
user1.age=18
user1.sex=男
```

结果正常输出：

![](https://img-blog.csdnimg.cn/img_convert/3cfb4bba9a6481e71fbe8f971bd490da.png)

### 3.8、对比小结

@Value 这个使用起来并不友好！我们需要为每个属性单独注解赋值，比较麻烦；我们来看个功能对比图

![](https://img-blog.csdnimg.cn/img_convert/8526e91e323c9052be6228b354b4328f.png)

1、@ConfigurationProperties 只需要写一次即可 ， @Value 则需要每个字段都添加

2、松散绑定：这个什么意思呢? 比如我的 yml 中写的 last-name，这个和 lastName 是一样的， - 后面跟着的字母默认是大写的。这就是松散绑定。可以测试一下

3、[JSR303](https://so.csdn.net/so/search?q=JSR303&spm=1001.2101.3001.7020) 数据校验 ， 这个就是我们可以在字段是增加一层过滤器验证 ， 可以保证数据的合法性

4、复杂类型封装，yml 中可以封装对象 ， 使用 value 就不支持

**结论：**

配置 yml 和配置 properties 都可以获取到值 ， 强烈推荐 yml；

如果我们在某个业务中，只需要获取配置文件中的某个值，可以使用一下 @value；

如果说，我们专门编写了一个 JavaBean 来和配置文件进行一一映射，就直接 @configurationProperties，不要犹豫！

P4、JSR303 [数据校验](https://so.csdn.net/so/search?q=%E6%95%B0%E6%8D%AE%E6%A0%A1%E9%AA%8C&spm=1001.2101.3001.7020)及多环境切换
--------------------------------------------------------------------------------------------------------------------

JSR303 数据校验

### 4.1、先看看如何使用

Springboot 中可以用 @validated 来校验数据，如果数据异常则会统一抛出异常，方便异常中心统一处理。我们这里来写个注解让我们的 name 只能支持 Email 格式；

```
@Component //注册bean
@ConfigurationProperties(prefix = "person")
@Validated  //数据校验
public class Person {

    @Email(message="邮箱格式错误") //name必须是邮箱格式
    private String name;
}
```

运行结果 ：default message [不是一个合法的电子邮件地址];

![](https://img-blog.csdnimg.cn/img_convert/638fd0cbf0a7100a6c45b79730b43dbe.png)

**使用数据校验，可以保证数据的正确性；**

### 4.2、常见参数

```
@NotNull(message="名字不能为空")
private String userName;
@Max(value=120,message="年龄最大不能查过120")
private int age;
@Email(message="邮箱格式错误")
private String email;

空检查
@Null       验证对象是否为null
@NotNull    验证对象是否不为null, 无法查检长度为0的字符串
@NotBlank   检查约束字符串是不是Null还有被Trim的长度是否大于0,只对字符串,且会去掉前后空格.
@NotEmpty   检查约束元素是否为NULL或者是EMPTY.
    
Booelan检查
@AssertTrue     验证 Boolean 对象是否为 true  
@AssertFalse    验证 Boolean 对象是否为 false  
    
长度检查
@Size(min=, max=) 验证对象（Array,Collection,Map,String）长度是否在给定的范围之内  
@Length(min=, max=) string is between min and max included.

日期检查
@Past       验证 Date 和 Calendar 对象是否在当前时间之前  
@Future     验证 Date 和 Calendar 对象是否在当前时间之后  
@Pattern    验证 String 对象是否符合正则表达式的规则

.......等等
除此以外，我们还可以自定义一些数据校验规则
```

多环境切换

profile 是 Spring 对不同环境提供不同配置功能的支持，可以通过激活不同的环境版本，实现快速切换环境；

### 4.3、多配置文件

我们在主配置文件编写的时候，文件名可以是 application-{profile}.properties/yml , 用来指定多个环境版本；

**例如：**

application-test.properties 代表测试环境配置

application-dev.properties 代表开发环境配置

但是 Springboot 并不会直接启动这些配置文件，它**默认使用 application.properties 主配置文件**；

我们需要通过一个配置来选择需要激活的环境：

```
#比如在配置文件中指定使用dev环境，我们可以通过设置不同的端口号进行测试；
#我们启动SpringBoot，就可以看到已经切换到dev下的配置了；
spring.profiles.active=dev
```

### 4.4、yaml 的多文档块

和 properties 配置文件中一样，但是使用 yml 去实现不需要创建多个配置文件，更加方便了 !

```
server:
  port: 8081
#选择要激活那个环境块
spring:
  profiles:
    active: prod

---
server:
  port: 8083
spring:
  profiles: dev #配置环境的名称


---

server:
  port: 8084
spring:
  profiles: prod  #配置环境的名称
```

**注意：如果 yml 和 properties 同时都配置了端口，并且没有激活其他环境 ， 默认会使用 properties 配置文件的！**

### 4.5、配置文件加载位置

**外部加载配置文件的方式十分多，我们选择最常用的即可，在开发的资源文件中进行配置！**

官方外部配置文件说明参考文档

![](https://img-blog.csdnimg.cn/img_convert/2c0d61df7e9e6ae8425c09887db366c5.png)

springboot 启动会扫描以下位置的 application.properties 或者 application.yml 文件作为 Spring boot 的默认配置文件：

```
优先级1：项目路径下的config文件夹配置文件
优先级2：项目路径下配置文件
优先级3：资源路径下的config文件夹配置文件
优先级4：资源路径下配置文件
```

优先级由高到底，高优先级的配置会覆盖低优先级的配置；

**SpringBoot 会从这四个位置全部加载主配置文件；互补配置；**

我们在最低级的配置文件中设置一个项目访问路径的配置来测试互补问题；

```
#配置项目的访问路径
server.servlet.context-path=/kuang
```

### 4.6、拓展，运维小技巧

指定位置加载配置文件

我们还可以通过 spring.config.location 来改变默认的配置文件位置

项目打包好以后，我们可以使用命令行参数的形式，启动项目的时候来指定配置文件的新位置；这种情况，一般是后期运维做的多，相同配置，外部指定的配置文件优先级最高

P5、自动配置原理
---------

自动配置原理

配置文件到底能写什么？怎么写？

SpringBoot 官方文档中有大量的配置，我们无法全部记住

![](https://img-blog.csdnimg.cn/img_convert/124cd74fa51f4fd88b740f0d28c8225a.png)

### 5.1、分析自动配置原理

我们以 **HttpEncodingAutoConfiguration（Http 编码自动配置）** 为例解释自动配置原理；

```
//表示这是一个配置类，和以前编写的配置文件一样，也可以给容器中添加组件；
@Configuration 

//启动指定类的ConfigurationProperties功能；
  //进入这个HttpProperties查看，将配置文件中对应的值和HttpProperties绑定起来；
  //并把HttpProperties加入到ioc容器中
@EnableConfigurationProperties({HttpProperties.class}) 

//Spring底层@Conditional注解
  //根据不同的条件判断，如果满足指定的条件，整个配置类里面的配置就会生效；
  //这里的意思就是判断当前应用是否是web应用，如果是，当前配置类生效
@ConditionalOnWebApplication(
    type = Type.SERVLET
)

//判断当前项目有没有这个类CharacterEncodingFilter；SpringMVC中进行乱码解决的过滤器；
@ConditionalOnClass({CharacterEncodingFilter.class})

//判断配置文件中是否存在某个配置：spring.http.encoding.enabled；
  //如果不存在，判断也是成立的
  //即使我们配置文件中不配置pring.http.encoding.enabled=true，也是默认生效的；
@ConditionalOnProperty(
    prefix = "spring.http.encoding",
    value = {"enabled"},
    matchIfMissing = true
)

public class HttpEncodingAutoConfiguration {
    //他已经和SpringBoot的配置文件映射了
    private final Encoding properties;
    //只有一个有参构造器的情况下，参数的值就会从容器中拿
    public HttpEncodingAutoConfiguration(HttpProperties properties) {
        this.properties = properties.getEncoding();
    }
    
    //给容器中添加一个组件，这个组件的某些值需要从properties中获取
    @Bean
    @ConditionalOnMissingBean //判断容器没有这个组件？
    public CharacterEncodingFilter characterEncodingFilter() {
        CharacterEncodingFilter filter = new OrderedCharacterEncodingFilter();
        filter.setEncoding(this.properties.getCharset().name());
        filter.setForceRequestEncoding(this.properties.shouldForce(org.springframework.boot.autoconfigure.http.HttpProperties.Encoding.Type.REQUEST));
        filter.setForceResponseEncoding(this.properties.shouldForce(org.springframework.boot.autoconfigure.http.HttpProperties.Encoding.Type.RESPONSE));
        return filter;
    }
    //。。。。。。。
}
```

**一句话总结 ：根据当前不同的条件判断，决定这个配置类是否生效！**

*   一但这个配置类生效；这个配置类就会给容器中添加各种组件；
*   这些组件的属性是从对应的 properties 类中获取的，这些类里面的每一个属性又是和配置文件绑定的；
*   所有在配置文件中能配置的属性都是在 xxxxProperties 类中封装着；
*   配置文件能配置什么就可以参照某个功能对应的这个属性类

```
//从配置文件中获取指定的值和bean的属性进行绑定
@ConfigurationProperties(prefix = "spring.http") 
public class HttpProperties {
    // .....
}
```

我们去配置文件里面试试前缀，看提示！

![](https://img-blog.csdnimg.cn/img_convert/227b15e3dfe8a079f2838e664bbb469f.png)

**这就是自动装配的原理！**

### 5.2、精髓

1、SpringBoot 启动会加载大量的自动配置类

2、我们看我们需要的功能有没有在 SpringBoot 默认写好的自动配置类当中；

3、我们再来看这个自动配置类中到底配置了哪些组件；（只要我们要用的组件存在在其中，我们就不需要再手动配置了）

4、给容器中自动配置类添加组件的时候，会从 properties 类中获取某些属性。我们只需要在配置文件中指定这些属性的值即可；

**xxxxAutoConfigurartion：自动配置类；** 给容器中添加组件

**xxxxProperties: 封装配置文件中相关属性；**

### 5.3、了解：@Conditional

了解完自动装配的原理后，我们来关注一个细节问题，**自动配置类必须在一定的条件下才能生效；**

**@Conditional 派生注解（Spring 注解版原生的 @Conditional 作用）**

作用：必须是 @Conditional 指定的条件成立，才给容器中添加组件，配置配里面的所有内容才生效；

![](https://img-blog.csdnimg.cn/img_convert/2c23d2bf372da743d7df034066afb90a.png)

**那么多的自动配置类，必须在一定的条件下才能生效；也就是说，我们加载了这么多的配置类，但不是所有的都生效了。**

我们怎么知道哪些自动配置类生效？

**我们可以通过启用 debug=true 属性；来让控制台打印自动配置报告，这样我们就可以很方便的知道哪些自动配置类生效；**

```
#开启springboot的调试类
debug=true
```

**Positive matches:（自动配置类启用的：正匹配）**

**Negative matches:（没有启动，没有匹配成功的自动配置类：负匹配）**

**Unconditional classes: （没有条件的类）**

【演示：查看输出的日志】

掌握吸收理解原理，即可以不变应万变！

P6、自定义 starter
--------------

我们分析完毕了源码以及自动装配的过程，我们可以尝试自定义一个启动器来玩玩！

### 6.1、说明

启动器模块是一个 空 jar 文件，仅提供辅助性依赖管理，这些依赖可能用于自动装配或者其他类库；

**命名归约：**

官方命名：

*   前缀：spring-boot-starter-xxx
*   比如：spring-boot-starter-web…

自定义命名：

*   xxx-spring-boot-starter
*   比如：mybatis-spring-boot-starter

### 6.2、编写启动器

1、在 IDEA 中新建一个空项目 spring-boot-starter-diy

2、新建一个普通 Maven 模块：kuang-spring-boot-starter

![](https://img-blog.csdnimg.cn/img_convert/d44e02c69c824e965e9f382a45f213f0.png)

3、新建一个 Springboot 模块：kuang-spring-boot-starter-autoconfigure

![](https://img-blog.csdnimg.cn/img_convert/f279b233d71b9db71501c3163ddf864f.png)

4、点击 apply 即可，基本结构

![](https://img-blog.csdnimg.cn/img_convert/8379323729b14707b65a822888273c89.png)

5、在我们的 starter 中 导入 autoconfigure 的依赖！

```
<!-- 启动器 -->
<dependencies>
    <!--  引入自动配置模块 -->
    <dependency>
        <groupId>com.kuang</groupId>
        <artifactId>kuang-spring-boot-starter-autoconfigure</artifactId>
        <version>0.0.1-SNAPSHOT</version>
    </dependency>
</dependencies>
```

6、将 autoconfigure 项目下多余的文件都删掉，Pom 中只留下一个 starter，这是所有的启动器基本配置！

![](https://img-blog.csdnimg.cn/img_convert/60c00990d63d7eb046ac80ac8577098c.png)

7、我们编写一个自己的服务

```
package com.kuang;

public class HelloService {

    HelloProperties helloProperties;

    public HelloProperties getHelloProperties() {
        return helloProperties;
    }

    public void setHelloProperties(HelloProperties helloProperties) {
        this.helloProperties = helloProperties;
    }

    public String sayHello(String name){
        return helloProperties.getPrefix() + name + helloProperties.getSuffix();
    }

}
```

8、编写 HelloProperties 配置类

```
package com.kuang;

import org.springframework.boot.context.properties.ConfigurationProperties;

// 前缀 kuang.hello
@ConfigurationProperties(prefix = "kuang.hello")
public class HelloProperties {

    private String prefix;
    private String suffix;

    public String getPrefix() {
        return prefix;
    }

    public void setPrefix(String prefix) {
        this.prefix = prefix;
    }

    public String getSuffix() {
        return suffix;
    }

    public void setSuffix(String suffix) {
        this.suffix = suffix;
    }
}
```

9、编写我们的自动配置类并注入 bean，测试！

```
package com.kuang;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.autoconfigure.condition.ConditionalOnWebApplication;
import org.springframework.boot.context.properties.EnableConfigurationProperties;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
@ConditionalOnWebApplication //web应用生效
@EnableConfigurationProperties(HelloProperties.class)
public class HelloServiceAutoConfiguration {

    @Autowired
    HelloProperties helloProperties;

    @Bean
    public HelloService helloService(){
        HelloService service = new HelloService();
        service.setHelloProperties(helloProperties);
        return service;
    }

}
```

10、在 resources 编写一个自己的 META-INF\spring.factories

```
# Auto Configure
org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
com.kuang.HelloServiceAutoConfiguration
```

11、编写完成后，可以安装到 maven 仓库中！

![](https://img-blog.csdnimg.cn/img_convert/c8b16b6539eb0447b2fdac72fb6e6980.png)

### 6.3、新建项目测试我们自己写的启动器

1、新建一个 SpringBoot 项目

2、导入我们自己写的启动器

```
<dependency>
    <groupId>com.kuang</groupId>
    <artifactId>kuang-spring-boot-starter</artifactId>
    <version>1.0-SNAPSHOT</version>
</dependency>
```

3、编写一个 HelloController 进行测试我们自己的写的接口！

```
package com.kuang.controller;

@RestController
public class HelloController {

    @Autowired
    HelloService helloService;

    @RequestMapping("/hello")
    public String hello(){
        return helloService.sayHello("zxc");
    }

}
```

4、编写配置文件 application.properties

```
kuang.hello.prefix="ppp"
kuang.hello.suffix="sss"
```

5、启动项目进行测试，结果成功 !

![](https://img-blog.csdnimg.cn/img_convert/5776ffd896b1823a26093d0cf53f5f57.png)

P7、SpringBoot 整合 JDBC
---------------------

### 7.1、SpringData 简介

对于数据访问层，无论是 SQL(关系型数据库) 还是 NOSQL(非关系型数据库)，Spring Boot 底层都是采用 Spring Data 的方式进行统一处理。

Spring Boot 底层都是采用 Spring Data 的方式进行统一处理各种数据库，Spring Data 也是 Spring 中与 Spring Boot、Spring Cloud 等齐名的知名项目。

Sping Data 官网：https://spring.io/projects/spring-data

数据库相关的启动器 ：可以参考官方文档：  
https://docs.spring.io/spring-boot/docs/2.2.5.RELEASE/reference/htmlsingle/#using-boot-starter

整合 JDBC

### 7.2、创建测试项目测试数据源

1、我去新建一个项目测试：springboot-data-jdbc ; 引入相应的模块！基础模块

![](https://img-blog.csdnimg.cn/img_convert/60270d1872a1c413c5e1c656050472a8.png)

2、项目建好之后，发现自动帮我们导入了如下的启动器

```
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-jdbc</artifactId>
</dependency>
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <scope>runtime</scope>
</dependency>
```

3、编写 yaml 配置文件连接数据库；

```
spring:
  datasource:
    username: root
    password: 123456
    #?serverTimezone=UTC解决时区的报错
    url: jdbc:mysql://localhost:3306/springboot?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
    driver-class-name: com.mysql.cj.jdbc.Driver
```

4、配置完这一些东西后，我们就可以直接去使用了，因为 SpringBoot 已经默认帮我们进行了自动配置；去测试类测试一下

```
@SpringBootTest
class SpringbootDataJdbcApplicationTests {

    //DI注入数据源
    @Autowired
    DataSource dataSource;

    @Test
    public void contextLoads() throws SQLException {
        //看一下默认数据源
        System.out.println(dataSource.getClass());
        //获得连接
        Connection connection =   dataSource.getConnection();
        System.out.println(connection);
        //关闭连接
        connection.close();
    }
}
```

结果：我们可以看到他默认给我们配置的数据源为 : class com.zaxxer.hikari.HikariDataSource ， 我们并没有手动配置

我们来全局搜索一下，找到数据源的所有自动配置都在 ：DataSourceAutoConfiguration 文件：

```
@Import(
    {Hikari.class, Tomcat.class, Dbcp2.class, Generic.class, DataSourceJmxConfiguration.class}
)
protected static class PooledDataSourceConfiguration {
    protected PooledDataSourceConfiguration() {
    }
}
```

这里导入的类都在 DataSourceConfiguration 配置类下，可以看出 Spring Boot 2.2.5 默认使用 HikariDataSource 数据源，而以前版本，如 Spring Boot 1.5 默认使用 org.apache.tomcat.jdbc.pool.DataSource 作为数据源；

**HikariDataSource 号称 Java WEB 当前速度最快的数据源，相比于传统的 C3P0 、DBCP、Tomcat jdbc 等连接池更加优秀；**

**可以使用 spring.datasource.type 指定自定义的数据源类型，值为 要使用的连接池实现的完全限定名。**

关于数据源我们并不做介绍，有了数据库连接，显然就可以 CRUD 操作数据库了。但是我们需要先了解一个对象 JdbcTemplate

### 7.3、JDBCTemplate

1、有了数据源 (com.zaxxer.hikari.HikariDataSource)，然后可以拿到数据库连接 (java.sql.Connection)，有了连接，就可以使用原生的 JDBC 语句来操作数据库；  
2、即使不使用第三方第数据库操作框架，如 MyBatis 等，Spring 本身也对原生的 JDBC 做了轻量级的封装，即 JdbcTemplate。  
3、数据库操作的所有 CRUD 方法都在 JdbcTemplate 中。  
4、Spring Boot 不仅提供了默认的数据源，同时默认已经配置好了 JdbcTemplate 放在了容器中，程序员只需自己注入即可使用  
5、JdbcTemplate 的自动配置是依赖 org.springframework.boot.autoconfigure.jdbc 包下的 JdbcTemplateConfiguration 类

**JdbcTemplate 主要提供以下几类方法：**

*   execute 方法：可以用于执行任何 SQL 语句，一般用于执行 DDL 语句；
*   update 方法及 batchUpdate 方法：update 方法用于执行新增、修改、删除等语句；batchUpdate 方法用于执行批处理相关语句；
*   query 方法及 queryForXXX 方法：用于执行查询相关语句；
*   call 方法：用于执行存储过程、函数相关语句。

### 7.4、测试

编写一个 Controller，注入 jdbcTemplate，编写测试方法进行访问测试；

```
package com.kuang.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.jdbc.core.JdbcTemplate;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.Date;
import java.util.List;
import java.util.Map;

@RestController
@RequestMapping("/jdbc")
public class JdbcController {

    /**
     * Spring Boot 默认提供了数据源，默认提供了 org.springframework.jdbc.core.JdbcTemplate
     * JdbcTemplate 中会自己注入数据源，用于简化 JDBC操作
     * 还能避免一些常见的错误,使用起来也不用再自己来关闭数据库连接
     */
    @Autowired
    JdbcTemplate jdbcTemplate;

    //查询employee表中所有数据
    //List 中的1个 Map 对应数据库的 1行数据
    //Map 中的 key 对应数据库的字段名，value 对应数据库的字段值
    @GetMapping("/list")
    public List<Map<String, Object>> userList(){
        String sql = "select * from employee";
        List<Map<String, Object>> maps = jdbcTemplate.queryForList(sql);
        return maps;
    }
    
    //新增一个用户
    @GetMapping("/add")
    public String addUser(){
        //插入语句，注意时间问题
        String sql = "insert into employee(last_name, email,gender,department,birth)" +
                " values ('狂神说','24736743@qq.com',1,101,'"+ new Date().toLocaleString() +"')";
        jdbcTemplate.update(sql);
        //查询
        return "addOk";
    }

    //修改用户信息
    @GetMapping("/update/{id}")
    public String updateUser(@PathVariable("id") int id){
        //插入语句
        String sql = "update employee set last_name=?,email=? where id="+id;
        //数据
        Object[] objects = new Object[2];
        objects[0] = "秦疆";
        objects[1] = "24736743@sina.com";
        jdbcTemplate.update(sql,objects);
        //查询
        return "updateOk";
    }

    //删除用户
    @GetMapping("/delete/{id}")
    public String delUser(@PathVariable("id") int id){
        //插入语句
        String sql = "delete from employee where id=?";
        jdbcTemplate.update(sql,id);
        //查询
        return "deleteOk";
    }
    
}
```

测试请求，结果正常；

到此，CURD 的基本操作，使用 JDBC 就搞定了。https://docs.spring.io/spring-boot/docs/2.0.4.RELEASE/reference/htmlsingle/#using-boot-starter)

### 7.5、原理探究 ：

org.springframework.boot.autoconfigure.jdbc.DataSourceConfiguration 数据源配置类作用 ：根据逻辑判断之后，添加数据源；

**SpringBoot 默认支持以下数据源：**

**com.zaxxer.hikari.HikariDataSource （Spring Boot 2.0 以上，默认使用此数据源）**

org.apache.tomcat.jdbc.pool.DataSource  
org.apache.commons.dbcp2.BasicDataSource

**可以使用 spring.datasource.type 指定自定义的数据源类型，值为 要使用的连接池实现的完全限定名。默认情况下，它是从类路径自动检测的。**

```
@Configuration
    @ConditionalOnMissingBean({DataSource.class})
    @ConditionalOnProperty(
        name = {"spring.datasource.type"}
    )
    static class Generic {
        Generic() {
        }

        @Bean
        public DataSource dataSource(DataSourceProperties properties) {
            return properties.initializeDataSourceBuilder().build();
        }
    }
```

P8、SpringBoot 整合 Druid
----------------------

### 8.1、Druid 简介

> Java 程序很大一部分要操作数据库，为了提高性能操作数据库的时候，又不得不使用数据库连接池。
> 
> Druid 是阿里巴巴开源平台上一个数据库连接池实现，结合了 C3P0、DBCP 等 DB 池的优点，同时加入了日志监控。
> 
> Druid 可以很好的监控 DB 池连接和 SQL 的执行情况，天生就是针对监控而生的 DB 连接池。
> 
> Druid 已经在阿里巴巴部署了超过 600 个应用，经过一年多生产环境大规模部署的严苛考验。
> 
> Spring Boot 2.0 以上默认使用 Hikari 数据源，可以说 Hikari 与 Driud 都是当前 Java Web  
> 上最优秀的数据源，我们来重点介绍 Spring Boot 如何集成 Druid 数据源，如何实现数据库监控。
> 
> Github 地址：https://github.com/alibaba/druid/

**com.alibaba.druid.pool.DruidDataSource 基本配置参数如下：**

<table><thead><tr><th>配置</th><th>缺省值</th><th>说明</th></tr></thead><tbody><tr><td>name</td><td></td><td>配置这个属性的意义在于，如果存在多个数据源，监控的时候可以通过名字来区分开来。 如果没有配置，将会生成一个名字，格式是：“DataSource-” + System.identityHashCode(this). 另外配置此属性至少在 1.0.5 版本中是不起作用的，强行设置 name 会出错 <a href="http://blog.csdn.net/lanmo555/article/details/41248763">详情 - 点此处</a>。</td></tr><tr><td>url</td><td></td><td>连接数据库的 url，不同数据库不一样。例如： mysql : jdbc:mysql://10.20.153.104:3306/druid2 oracle : jdbc:oracle:thin:@10.20.149.85:1521:ocnauto</td></tr><tr><td>username</td><td></td><td>连接数据库的用户名</td></tr><tr><td>password</td><td></td><td>连接数据库的密码。如果你不希望密码直接写在配置文件中，可以使用 ConfigFilter。详细看这里：https://github.com/alibaba/druid/wiki / 使用 ConfigFilter</td></tr><tr><td>driverClassName</td><td>根据 url 自动识别</td><td>这一项可配可不配，如果不配置 druid 会根据 url 自动识别 dbType，然后选择相应的 driverClassName</td></tr><tr><td>initialSize</td><td>0</td><td>初始化时建立物理连接的个数。初始化发生在显示调用 init 方法，或者第一次 getConnection 时</td></tr><tr><td>maxActive</td><td>8</td><td>最大连接池数量</td></tr><tr><td>maxIdle</td><td>8</td><td>已经不再使用，配置了也没效果</td></tr><tr><td>minIdle</td><td></td><td>最小连接池数量</td></tr><tr><td>maxWait</td><td></td><td>获取连接时最大等待时间，单位毫秒。配置了 maxWait 之后，缺省启用公平锁，并发效率会有所下降，如果需要可以通过配置 useUnfairLock 属性为 true 使用非公平锁。</td></tr><tr><td>poolPreparedStatements</td><td>false</td><td>是否缓存 preparedStatement，也就是 PSCache。PSCache 对支持游标的数据库性能提升巨大，比如说 oracle。在 mysql 下建议关闭。</td></tr><tr><td>maxOpenPreparedStatements</td><td>-1</td><td>要启用 PSCache，必须配置大于 0，当大于 0 时，poolPreparedStatements 自动触发修改为 true。在 Druid 中，不会存在 Oracle 下 PSCache 占用内存过多的问题，可以把这个数值配置大一些，比如说 100</td></tr><tr><td>validationQuery</td><td></td><td>用来检测连接是否有效的 sql，要求是一个查询语句。如果 validationQuery 为 null，testOnBorrow、testOnReturn、testWhileIdle 都不会其作用。</td></tr><tr><td>validationQueryTimeout</td><td></td><td>单位：秒，检测连接是否有效的超时时间。底层调用 jdbc Statement 对象的 void setQueryTimeout(int seconds) 方法</td></tr><tr><td>testOnBorrow</td><td>true</td><td>申请连接时执行 validationQuery 检测连接是否有效，做了这个配置会降低性能。</td></tr><tr><td>testOnReturn</td><td>false</td><td>归还连接时执行 validationQuery 检测连接是否有效，做了这个配置会降低性能</td></tr><tr><td>testWhileIdle</td><td>false</td><td>建议配置为 true，不影响性能，并且保证安全性。申请连接的时候检测，如果空闲时间大于 timeBetweenEvictionRunsMillis，执行 validationQuery 检测连接是否有效。</td></tr><tr><td>timeBetweenEvictionRunsMillis</td><td>1 分钟（1.0.14）</td><td>有两个含义： 1) Destroy 线程会检测连接的间隔时间，如果连接空闲时间大于等于 minEvictableIdleTimeMillis 则关闭物理连接 2) testWhileIdle 的判断依据，详细看 testWhileIdle 属性的说明</td></tr><tr><td>numTestsPerEvictionRun</td><td></td><td>不再使用，一个 DruidDataSource 只支持一个 EvictionRun</td></tr><tr><td>minEvictableIdleTimeMillis</td><td>30 分钟（1.0.14）</td><td>连接保持空闲而不被驱逐的最长时间</td></tr><tr><td>connectionInitSqls</td><td></td><td>物理连接初始化的时候执行的 sql</td></tr><tr><td>exceptionSorter</td><td>根据 dbType 自动识别</td><td>当数据库抛出一些不可恢复的异常时，抛弃连接</td></tr><tr><td>filters</td><td></td><td>属性类型是字符串，通过别名的方式配置扩展插件，常用的插件有： 监控统计用的 filter:stat 日志用的 filter:log4j 防御 sql 注入的 filter:wall</td></tr><tr><td>proxyFilters</td><td></td><td>类型是 List&lt;com.alibaba.druid.filter.Filter&gt;，如果同时配置了 filters 和 proxyFilters，是组合关系，并非替换关系</td></tr></tbody></table>

### 8.2、配置数据源

1、添加上 Druid 数据源依赖。

```
<!-- https://mvnrepository.com/artifact/com.alibaba/druid -->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.1.12</version>
</dependency>
```

2、切换数据源；之前已经说过 Spring Boot 2.0 以上默认使用 com.zaxxer.hikari.HikariDataSource 数据源，但可以 通过 spring.datasource.type 指定数据源。

```
spring:
  datasource:
    username: root
    password: 123456
    url: jdbc:mysql://localhost:3306/springboot?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
    driver-class-name: com.mysql.cj.jdbc.Driver
    type: com.alibaba.druid.pool.DruidDataSource # 自定义数据源
```

3、数据源切换之后，在测试类中注入 DataSource，然后获取到它，输出一看便知是否成功切换；

![](https://img-blog.csdnimg.cn/img_convert/c750fb675c916db609fe3562ea41a846.png)

4、切换成功！既然切换成功，就可以设置数据源连接初始化大小、最大连接数、等待时间、最小连接数 等设置项；可以查看源码

```
spring:
  datasource:
    username: root
    password: 123456
    #?serverTimezone=UTC解决时区的报错
    url: jdbc:mysql://localhost:3306/springboot?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
    driver-class-name: com.mysql.cj.jdbc.Driver
    type: com.alibaba.druid.pool.DruidDataSource

    #Spring Boot 默认是不注入这些属性值的，需要自己绑定
    #druid 数据源专有配置
    initialSize: 5
    minIdle: 5
    maxActive: 20
    maxWait: 60000
    timeBetweenEvictionRunsMillis: 60000
    minEvictableIdleTimeMillis: 300000
    validationQuery: SELECT 1 FROM DUAL
    testWhileIdle: true
    testOnBorrow: false
    testOnReturn: false
    poolPreparedStatements: true

    #配置监控统计拦截的filters，stat:监控统计、log4j：日志记录、wall：防御sql注入
    #如果允许时报错  java.lang.ClassNotFoundException: org.apache.log4j.Priority
    #则导入 log4j 依赖即可，Maven 地址：https://mvnrepository.com/artifact/log4j/log4j
    filters: stat,wall,log4j
    maxPoolPreparedStatementPerConnectionSize: 20
    useGlobalDataSourceStat: true
    connectionProperties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=500
```

5、导入 Log4j 的依赖

```
<!-- https://mvnrepository.com/artifact/log4j/log4j -->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
            <version>1.2.17</version>
        </dependency>
```

6、现在需要程序员自己为 DruidDataSource 绑定全局配置文件中的参数，再添加到容器中，而不再使用 Spring Boot 的自动生成了；我们需要 自己添加 DruidDataSource 组件到容器中，并绑定属性；

```
package com.kuang.config;

import com.alibaba.druid.pool.DruidDataSource;
import org.springframework.boot.context.properties.ConfigurationProperties;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

import javax.sql.DataSource;

@Configuration
public class DruidConfig {

    /*
       将自定义的 Druid数据源添加到容器中，不再让 Spring Boot 自动创建
       绑定全局配置文件中的 druid 数据源属性到 com.alibaba.druid.pool.DruidDataSource从而让它们生效
       @ConfigurationProperties(prefix = "spring.datasource")：作用就是将 全局配置文件中
       前缀为 spring.datasource的属性值注入到 com.alibaba.druid.pool.DruidDataSource 的同名参数中
     */
    @ConfigurationProperties(prefix = "spring.datasource")
    @Bean
    public DataSource druidDataSource() {
        return new DruidDataSource();
    }

}
```

7、去测试类中测试一下；看是否成功！

```
@SpringBootTest
class SpringbootDataJdbcApplicationTests {

    //DI注入数据源
    @Autowired
    DataSource dataSource;

    @Test
    public void contextLoads() throws SQLException {
        //看一下默认数据源
        System.out.println(dataSource.getClass());
        //获得连接
        Connection connection =   dataSource.getConnection();
        System.out.println(connection);

        DruidDataSource druidDataSource = (DruidDataSource) dataSource;
        System.out.println("druidDataSource 数据源最大连接数：" + druidDataSource.getMaxActive());
        System.out.println("druidDataSource 数据源初始化连接数：" + druidDataSource.getInitialSize());

        //关闭连接
        connection.close();
    }
}
```

输出结果 ：可见配置参数已经生效！

![](https://img-blog.csdnimg.cn/img_convert/2c2e4232e457b1876207ebd374d60375.png)

### 8.3、配置 Druid 数据源监控

Druid 数据源具有监控的功能，并提供了一个 web 界面方便用户查看，类似安装 路由器 时，人家也提供了一个默认的 web 页面。

所以第一步需要设置 Druid 的后台管理页面，比如 登录账号、密码 等；配置后台管理；

```
//配置 Druid 监控管理后台的Servlet；
//内置 Servlet 容器时没有web.xml文件，所以使用 Spring Boot 的注册 Servlet 方式
@Bean
public ServletRegistrationBean statViewServlet() {
    ServletRegistrationBean bean = new ServletRegistrationBean(new StatViewServlet(), "/druid/*");

    // 这些参数可以在 com.alibaba.druid.support.http.StatViewServlet 
    // 的父类 com.alibaba.druid.support.http.ResourceServlet 中找到
    Map<String, String> initParams = new HashMap<>();
    initParams.put("loginUsername", "admin"); //后台管理界面的登录账号
    initParams.put("loginPassword", "123456"); //后台管理界面的登录密码

    //后台允许谁可以访问
    //initParams.put("allow", "localhost")：表示只有本机可以访问
    //initParams.put("allow", "")：为空或者为null时，表示允许所有访问
    initParams.put("allow", "");
    //deny：Druid 后台拒绝谁访问
    //initParams.put("kuangshen", "192.168.1.20");表示禁止此ip访问

    //设置初始化参数
    bean.setInitParameters(initParams);
    return bean;
}
```

配置完毕后，我们可以选择访问 ：http://localhost:8080/druid/login.html

![](https://img-blog.csdnimg.cn/img_convert/e082fcc2d42ea375beff79a767cc9cc1.png)

进入之后

![](https://img-blog.csdnimg.cn/img_convert/6247f8a64457acd4a15e2b0ab6494549.png)

**配置 Druid web 监控 filter 过滤器**

```
//配置 Druid 监控 之  web 监控的 filter
//WebStatFilter：用于配置Web和Druid数据源之间的管理关联监控统计
@Bean
public FilterRegistrationBean webStatFilter() {
    FilterRegistrationBean bean = new FilterRegistrationBean();
    bean.setFilter(new WebStatFilter());

    //exclusions：设置哪些请求进行过滤排除掉，从而不进行统计
    Map<String, String> initParams = new HashMap<>();
    initParams.put("exclusions", "*.js,*.css,/druid/*,/jdbc/*");
    bean.setInitParameters(initParams);

    //"/*" 表示过滤所有请求
    bean.setUrlPatterns(Arrays.asList("/*"));
    return bean;
}
```

平时在工作中，按需求进行配置即可，主要用作监

P9、SpringBoot 整合 mybatis
------------------------

### 9.1、导入 mybatis 所需要的依赖

```
<!-- 引入 myBatis，这是 MyBatis官方提供的适配 Spring Boot 的，而不是Spring Boot自己的-->
        <dependency>
            <groupId>org.mybatis.spring.boot</groupId>
            <artifactId>mybatis-spring-boot-starter</artifactId>
            <version>2.1.0</version>
        </dependency>
```

### 9.2、配置数据库连接信息

```
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
spring.datasource.driver-class-name=com.mysql.jdbc.Driver
```

### 9.3、我们这里就是用默认的数据源了；先去测试一下连接是否成功！

```
@RunWith(SpringRunner.class)
@SpringBootTest
public class SpringbootDemoMybatisApplicationTests {

    @Autowired
    DataSource dataSource;

    @Test
    public void contextLoads() throws SQLException {

        System.out.println("数据源>>>>>>" + dataSource.getClass());
        Connection connection = dataSource.getConnection();
        System.out.println("连接>>>>>>>>>" + connection);
        System.out.println("连接地址>>>>>" + connection.getMetaData().getURL());
        connection.close();

    }

}
```

**查看输出结果，数据库配置 OK！**

### 9.4、创建实体类

```
package com.kuang.mybatis.pojo;

public class User {

    private int id;
    private String name;
    private String pwd;

    public User() {
    }

    public User(int id, String name, String pwd) {
        this.id = id;
        this.name = name;
        this.pwd = pwd;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getPwd() {
        return pwd;
    }

    public void setPwd(String pwd) {
        this.pwd = pwd;
    }

    @Override
    public String toString() {
        return "User{" +
                "id=" + id +
                ",  + name + '\'' +
                ", pwd='" + pwd + '\'' +
                '}';
    }

}
```

### 9.5、配置 Mapper 接口类

```
package com.kuang.mybatis.pojo.mapper;

import com.kuang.mybatis.pojo.User;
import org.apache.ibatis.annotations.Mapper;
import org.springframework.stereotype.Repository;

import java.util.List;

//@Mapper : 表示本类是一个 MyBatis 的 Mapper，等价于以前 Spring 整合 MyBatis 时的 Mapper 接口
@Mapper
@Repository
public interface UserMapper {

    //选择全部用户
    List<User> selectUser();
    //根据id选择用户
    User selectUserById(int id);
    //添加一个用户
    int addUser(User user);
    //修改一个用户
    int updateUser(User user);
    //根据id删除用户
    int deleteUser(int id);

}
```

### 9.6、对应 Mapper 映射文件

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.kuang.mybatis.pojo.mapper.UserMapper">

    <select id="selectUser" resultType="User">
    select * from user
  </select>

    <select id="selectUserById" resultType="User">
    select * from user where id = #{id}
</select>

    <insert id="addUser" parameterType="User">
    insert into user (id,name,pwd) values (#{id},#{name},#{pwd})
</insert>

    <update id="updateUser" parameterType="User">
    update user set name=#{name},pwd=#{pwd} where id = #{id}
</update>

    <delete id="deleteUser" parameterType="int">
    delete from user where id = #{id}
</delete>
</mapper>
```

### 9.7、maven 配置资源过滤问题

```
<resources>
    <resource>
        <directory>src/main/java</directory>
        <includes>
            <include>**/*.xml</include>
        </includes>
        <filtering>true</filtering>
    </resource>
</resources>
```

### 9.8、SpringBoot 整合！

以前 MyBatis 未与 spring 整合时，配置数据源、事务、连接数据库的账号、密码等都是在 myBatis 核心配置文件中进行的 myBatis 与 spring 整合后，配置数据源、事务、连接数据库的账号、密码等就交由 spring 管理。因此，在这里我们即使不使用 mybatis 配置文件也完全 ok！  
**既然已经提供了 myBatis 的映射配置文件，自然要告诉 spring boot 这些文件的位置**

```
spring.datasource.username=root
spring.datasource.password=123456
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
spring.datasource.driver-class-name=com.mysql.jdbc.Driver

#指定myBatis的核心配置文件与Mapper映射文件
mybatis.mapper-locations=classpath:mybatis/mapper/*.xml
# 注意：对应实体类的路径
mybatis.type-aliases-package=com.kuang.mybatis.pojo
```

已经说过 spring boot 官方并没有提供 myBaits 的启动器，是 myBatis 官方提供的开发包来适配的 spring boot，从 pom.xml 文件中的依赖包名也能看出来，并非是以 spring-boot 开头的；

同理上面全局配置文件中的这两行配置也是以 mybatis 开头 而非 spring 开头也充分说明这些都是 myBatis 官方提供的

可以从 org.mybatis.spring.boot.autoconfigure.MybatisProperties 中查看所有配置项

```
@ConfigurationProperties(
    prefix = "mybatis"
)
public class MybatisProperties {
    public static final String MYBATIS_PREFIX = "mybatis";
    private static final ResourcePatternResolver resourceResolver = new PathMatchingResourcePatternResolver();
    private String configLocation;
    private String[] mapperLocations;
    private String typeAliasesPackage;
    private Class<?> typeAliasesSuperType;
    private String typeHandlersPackage;
    private boolean checkConfigLocation = false;
    private ExecutorType executorType;
    private Class<? extends LanguageDriver> defaultScriptingLanguageDriver;
    private Properties configurationProperties;
    @NestedConfigurationProperty
    private Configuration configuration;
```

也可以直接去查看 [官方文档](http://www.mybatis.org/spring-boot-starter/mybatis-spring-boot-autoconfigure/)

### 9.9、编写 controller

```
package com.kuang.mybatis.controller;

import com.kuang.mybatis.pojo.User;
import com.kuang.mybatis.pojo.mapper.UserMapper;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.List;

@RestController
public class UserController {

    @Autowired
    private UserMapper userMapper;

    //选择全部用户
    @GetMapping("/selectUser")
    public String selectUser(){
        List<User> users = userMapper.selectUser();
        for (User user : users) {
            System.out.println(user);
        }

        return "ok";
    }
    //根据id选择用户
    @GetMapping("/selectUserById")
    public String selectUserById(){
        User user = userMapper.selectUserById(1);
        System.out.println(user);
        return "ok";
    }
    //添加一个用户
    @GetMapping("/addUser")
    public String addUser(){
        userMapper.addUser(new User(5,"阿毛","456789"));
        return "ok";
    }
    //修改一个用户
    @GetMapping("/updateUser")
    public String updateUser(){
        userMapper.updateUser(new User(5,"阿毛","421319"));
        return "ok";
    }
    //根据id删除用户
    @GetMapping("/deleteUser")
    public String deleteUser(){
        userMapper.deleteUser(5);
        return "ok";
    }

}
```

### 9.10、启动项目访问进行测试！

**步骤：**

Mybatis 整合包

mybatis-spring-boot-starter

1. 导入包

2. 配置文件

3.mybatis 配置

4. 编写 sql

5.service 层调用 dao 层

6.controller 调用 service 层

### 注：配置数据库连接信息（不变）

```
spring:
  datasource:
    username: root
    password: 123456
    #?serverTimezone=UTC解决时区的报错
    url: jdbc:mysql://localhost:3306/mybatis?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
    driver-class-name: com.mysql.jdbc.Driver
    type: com.alibaba.druid.pool.DruidDataSource

    #Spring Boot 默认是不注入这些属性值的，需要自己绑定
    #druid 数据源专有配置
    initialSize: 5
    minIdle: 5
    maxActive: 20
    maxWait: 60000
    timeBetweenEvictionRunsMillis: 60000
    minEvictableIdleTimeMillis: 300000
    validationQuery: SELECT 1 FROM DUAL
    testWhileIdle: true
    testOnBorrow: false
    testOnReturn: false
    poolPreparedStatements: true

    #配置监控统计拦截的filters，stat:监控统计、log4j：日志记录、wall：防御sql注入
    #如果允许时报错  java.lang.ClassNotFoundException: org.apache.log4j.Priority
    #则导入 log4j 依赖即可，Maven 地址： https://mvnrepository.com/artifact/log4j/log4j
    filters: stat,wall,log4j
    maxPoolPreparedStatementPerConnectionSize: 20
    useGlobalDataSourceStat: true
    connectionProperties: druid.stat.mergeSql=true;druid.stat.slowSqlMillis=500
```

P10、Web 开发静态资源处理
----------------

Web 开发探究

### 10.1、简介

好的，同学们，那么接下来呢，我们开始学习 SpringBoot 与 Web 开发，从这一章往后，就属于我们实战部分的内容了；

其实 SpringBoot 的东西用起来非常简单，因为 SpringBoot 最大的特点就是自动装配。

**使用 SpringBoot 的步骤：**

1、创建一个 SpringBoot 应用，选择我们需要的模块，SpringBoot 就会默认将我们的需要的模块自动配置好

2、手动在配置文件中配置部分配置项目就可以运行起来了

3、专注编写业务代码，不需要考虑以前那样一大堆的配置了。

要熟悉掌握开发，之前学习的自动配置的原理一定要搞明白！

比如 SpringBoot 到底帮我们配置了什么？我们能不能修改？我们能修改哪些配置？我们能不能扩展？

*   向容器中自动配置组件 ：*** Autoconfiguration
*   自动配置类，封装配置文件的内容：***Properties

没事就找找类，看看自动装配原理！

我们之后来进行一个单体项目的小项目测试，让大家能够快速上手开发！

静态资源处理

### 10.2、静态资源映射规则

**首先，我们搭建一个普通的 SpringBoot 项目，回顾一下 HelloWorld 程序！**

写请求非常简单，那我们要引入我们前端资源，我们项目中有许多的静态资源，比如 css，js 等文件，这个 SpringBoot 怎么处理呢？

如果我们是一个 web 应用，我们的 main 下会有一个 webapp，我们以前都是将所有的页面导在这里面的，对吧！但是我们现在的 pom 呢，打包方式是为 jar 的方式，那么这种方式 SpringBoot 能不能来给我们写页面呢？当然是可以的，但是 SpringBoot 对于静态资源放置的位置，是有规定的！

**我们先来聊聊这个静态资源映射规则：**

SpringBoot 中，SpringMVC 的 web 配置都在 WebMvcAutoConfiguration 这个配置类里面；

我们可以去看看 WebMvcAutoConfigurationAdapter 中有很多配置方法；

有一个方法：addResourceHandlers 添加资源处理

```
@Override
public void addResourceHandlers(ResourceHandlerRegistry registry) {
    if (!this.resourceProperties.isAddMappings()) {
        // 已禁用默认资源处理
        logger.debug("Default resource handling disabled");
        return;
    }
    // 缓存控制
    Duration cachePeriod = this.resourceProperties.getCache().getPeriod();
    CacheControl cacheControl = this.resourceProperties.getCache().getCachecontrol().toHttpCacheControl();
    // webjars 配置
    if (!registry.hasMappingForPattern("/webjars/**")) {
        customizeResourceHandlerRegistration(registry.addResourceHandler("/webjars/**")
                                             .addResourceLocations("classpath:/META-INF/resources/webjars/")
                                             .setCachePeriod(getSeconds(cachePeriod)).setCacheControl(cacheControl));
    }
    // 静态资源配置
    String staticPathPattern = this.mvcProperties.getStaticPathPattern();
    if (!registry.hasMappingForPattern(staticPathPattern)) {
        customizeResourceHandlerRegistration(registry.addResourceHandler(staticPathPattern)
                                             .addResourceLocations(getResourceLocations(this.resourceProperties.getStaticLocations()))
                                             .setCachePeriod(getSeconds(cachePeriod)).setCacheControl(cacheControl));
    }
}
```

读一下源代码：比如所有的 /webjars/** ， 都需要去 classpath:/META-INF/resources/webjars/ 找对应的资源；

### 10.3、什么是 webjars 呢？

Webjars 本质就是以 jar 包的方式引入我们的静态资源 ， 我们以前要导入一个静态资源文件，直接导入即可。

使用 SpringBoot 需要使用 Webjars，我们可以去搜索一下：

网站：[https://www.webjars.org](https://www.webjars.org/)

要使用 jQuery，我们只要要引入 jQuery 对应版本的 pom 依赖即可！

```
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>jquery</artifactId>
    <version>3.4.1</version>
</dependency>
```

导入完毕，查看 webjars 目录结构，并访问 Jquery.js 文件！

![](https://img-blog.csdnimg.cn/img_convert/d9e8374fcf594e909386267393caab34.png)

访问：只要是静态资源，SpringBoot 就会去对应的路径寻找资源，我们这里访问：http://localhost:8080/webjars/jquery/3.4.1/jquery.js

![](https://img-blog.csdnimg.cn/img_convert/cb239ee3c8a96312f5fd0e5965eb81ad.png)

### 10.4、第二种静态资源映射规则

那我们项目中要是使用自己的静态资源该怎么导入呢？我们看下一行代码；

我们去找 staticPathPattern 发现第二种映射规则 ：/** , 访问当前的项目任意资源，它会去找 resourceProperties 这个类，我们可以点进去看一下分析：

```
// 进入方法
public String[] getStaticLocations() {
    return this.staticLocations;
}
// 找到对应的值
private String[] staticLocations = CLASSPATH_RESOURCE_LOCATIONS;
// 找到路径
private static final String[] CLASSPATH_RESOURCE_LOCATIONS = { 
    "classpath:/META-INF/resources/",
  "classpath:/resources/", 
    "classpath:/static/", 
    "classpath:/public/" 
};
```

ResourceProperties 可以设置和我们静态资源有关的参数；这里面指向了它会去寻找资源的文件夹，即上面数组的内容。

所以得出结论，以下四个目录存放的静态资源可以被我们识别：

```
"classpath:/META-INF/resources/"
"classpath:/resources/"
"classpath:/static/"
"classpath:/public/"
```

我们可以在 resources 根目录下新建对应的文件夹，都可以存放我们的静态文件；

比如我们访问 http://localhost:8080/1.js , 他就会去这些文件夹中寻找对应的静态资源文件；

### 10.5、自定义静态资源路径

我们也可以自己通过配置文件来指定一下，哪些文件夹是需要我们放静态资源文件的，在 application.properties 中配置；

```
spring.resources.static-locations=classpath:/coding/,classpath:/kuang/
```

一旦自己定义了静态文件夹的路径，原来的自动配置就都会失效了！

首页处理

静态资源文件夹说完后，我们继续向下看源码！可以看到一个欢迎页的映射，就是我们的首页！

```
@Bean
public WelcomePageHandlerMapping welcomePageHandlerMapping(ApplicationContext applicationContext, FormattingConversionService mvcConversionService,ResourceUrlProvider mvcResourceUrlProvider) {
    WelcomePageHandlerMapping welcomePageHandlerMapping = new WelcomePageHandlerMapping(
        new TemplateAvailabilityProviders(applicationContext), applicationContext, getWelcomePage(), // getWelcomePage 获得欢迎页
        this.mvcProperties.getStaticPathPattern());
    welcomePageHandlerMapping.setInterceptors(getInterceptors(mvcConversionService, mvcResourceUrlProvider));
    return welcomePageHandlerMapping;
}
```

点进去继续看

```
private Optional<Resource> getWelcomePage() {
    String[] locations = getResourceLocations(this.resourceProperties.getStaticLocations());
    // ::是java8 中新引入的运算符
    // Class::function的时候function是属于Class的，应该是静态方法。
    // this::function的funtion是属于这个对象的。
    // 简而言之，就是一种语法糖而已，是一种简写
    return Arrays.stream(locations).map(this::getIndexHtml).filter(this::isReadable).findFirst();
}
// 欢迎页就是一个location下的的 index.html 而已
private Resource getIndexHtml(String location) {
    return this.resourceLoader.getResource(location + "index.html");
}
```

欢迎页，静态资源文件夹下的所有 index.html 页面；被 /** 映射。

比如我访问 http://localhost:8080/ ，就会找静态资源文件夹下的 index.html

新建一个 index.html ，在我们上面的 3 个目录中任意一个；然后访问测试 http://localhost:8080/ 看结果！

**关于网站图标说明**：

![](https://img-blog.csdnimg.cn/img_convert/201f18ce91e5d4044a6d06abd08d88c5.png)

与其他静态资源一样，Spring Boot 在配置的静态内容位置中查找 favicon.ico。如果存在这样的文件，它将自动用作应用程序的 favicon。

1、关闭 SpringBoot 默认图标

```
#关闭默认图标spring.mvc.favicon.enabled=false
```

2、自己放一个图标在静态资源目录下，我放在 public 目录下

3、清除浏览器缓存！刷新网页，发现图标已经变成自己的了！

![](https://img-blog.csdnimg.cn/img_convert/92b2a57bacbc97ac273de31f8f76ccee.png)

P11、Thymeleaf 模板引擎
------------------

### 11.1、模板引擎

前端交给我们的页面，是 html 页面。如果是我们以前开发，我们需要把他们转成 jsp 页面，jsp 好处就是当我们查出一些数据转发到 JSP 页面以后，我们可以用 jsp 轻松实现数据的显示，及交互等。

jsp 支持非常强大的功能，包括能写 Java 代码，但是呢，我们现在的这种情况，SpringBoot 这个项目首先是以 jar 的方式，不是 war，像第二，我们用的还是嵌入式的 Tomcat，所以呢，**他现在默认是不支持 jsp 的**。

那不支持 jsp，如果我们直接用纯静态页面的方式，那给我们开发会带来非常大的麻烦，那怎么办呢？

**SpringBoot 推荐你可以来使用模板引擎：**

模板引擎，我们其实大家听到很多，其实 jsp 就是一个模板引擎，还有用的比较多的 freemarker，包括 SpringBoot 给我们推荐的 Thymeleaf，模板引擎有非常多，但再多的模板引擎，他们的思想都是一样的，什么样一个思想呢我们来看一下这张图：

![](https://img-blog.csdnimg.cn/img_convert/ab7d4de8088ffd6bda615abfac88de03.png)

模板引擎的作用就是我们来写一个页面模板，比如有些值呢，是动态的，我们写一些表达式。而这些值，从哪来呢，就是我们在后台封装一些数据。然后把这个模板和这个数据交给我们模板引擎，模板引擎按照我们这个数据帮你把这表达式解析、填充到我们指定的位置，然后把这个数据最终生成一个我们想要的内容给我们写出去，这就是我们这个模板引擎，不管是 jsp 还是其他模板引擎，都是这个思想。只不过呢，就是说不同模板引擎之间，他们可能这个语法有点不一样。其他的我就不介绍了，我主要来介绍一下 SpringBoot 给我们推荐的 Thymeleaf 模板引擎，这模板引擎呢，是一个高级语言的模板引擎，他的这个语法更简单。而且呢，功能更强大。

我们呢，就来看一下这个模板引擎，那既然要看这个模板引擎。首先，我们来看 SpringBoot 里边怎么用。

### 11.2、引入 Thymeleaf

怎么引入呢，对于 springboot 来说，什么事情不都是一个 start 的事情嘛，我们去在项目中引入一下。给大家三个网址：

Thymeleaf 官网：https://www.thymeleaf.org/

Thymeleaf 在 Github 的主页：https://github.com/thymeleaf/thymeleaf

Spring 官方文档：找到我们对应的版本

https://docs.spring.io/spring-boot/docs/2.2.5.RELEASE/reference/htmlsingle/#using-boot-starter

找到对应的 pom 依赖：可以适当点进源码看下本来的包！

```
<!--thymeleaf-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-thymeleaf</artifactId>
</dependency>
```

Maven 会自动下载 jar 包，我们可以去看下下载的东西；

![](https://img-blog.csdnimg.cn/img_convert/d45c6d0924d968f111e24e7280000d82.png)

### 11.3、Thymeleaf 分析

前面呢，我们已经引入了 Thymeleaf，那这个要怎么使用呢？

我们首先得按照 SpringBoot 的自动配置原理看一下我们这个 Thymeleaf 的自动配置规则，在按照那个规则，我们进行使用。

我们去找一下 Thymeleaf 的自动配置类：ThymeleafPropert

```
@ConfigurationProperties(
    prefix = "spring.thymeleaf"
)
public class ThymeleafProperties {
    private static final Charset DEFAULT_ENCODING;
    public static final String DEFAULT_PREFIX = "classpath:/templates/";
    public static final String DEFAULT_SUFFIX = ".html";
    private boolean checkTemplate = true;
    private boolean checkTemplateLocation = true;
    private String prefix = "classpath:/templates/";
    private String suffix = ".html";
    private String mode = "HTML";
    private Charset encoding;
}
```

我们可以在其中看到默认的前缀和后缀！

我们只需要把我们的 html 页面放在类路径下的 templates 下，thymeleaf 就可以帮我们自动渲染了。

使用 thymeleaf 什么都不需要配置，只需要将他放在指定的文件夹下即可！

**测试**

1、编写一个 TestController

```
@Controller
public class TestController {
    
    @RequestMapping("/t1")
    public String test1(){
        //classpath:/templates/test.html
        return "test";
    }
    
}
```

2、编写一个测试页面 test.html 放在 templates 目录下

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
<h1>测试页面</h1>

</body>
</html>
```

3、启动项目请求测试

### 11.4、Thymeleaf 语法学习

要学习语法，还是参考官网文档最为准确，我们找到对应的版本看一下；

Thymeleaf 官网：https://www.thymeleaf.org/ ， 简单看一下官网！我们去下载 Thymeleaf 的官方文档！

**我们做个最简单的练习 ：我们需要查出一些数据，在页面中展示**

1、修改测试请求，增加数据传输；

```
@RequestMapping("/t1")
public String test1(Model model){
    //存入数据
    model.addAttribute("msg","Hello,Thymeleaf");
    //classpath:/templates/test.html
    return "test";
}
```

2、我们要使用 thymeleaf，需要在 html 文件中导入命名空间的约束，方便提示。

我们可以去官方文档的 #3 中看一下命名空间拿来过来：

```
xmlns:th="http://www.thymeleaf.org"
```

3、我们去编写下前端页面

```
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>狂神说</title>
</head>
<body>
<h1>测试页面</h1>

<!--th:text就是将div中的内容设置为它指定的值，和之前学习的Vue一样-->
<div th:text="${msg}"></div>
</body>
</html>
```

4、启动测试！

![](https://img-blog.csdnimg.cn/img_convert/b441efe272b69e5938f4358a22dd5dbe.png)

**OK，入门搞定，我们来认真研习一下 Thymeleaf 的使用语法！**

**1、我们可以使用任意的 th:attr 来替换 Html 中原生属性的值！**

![](https://img-blog.csdnimg.cn/img_convert/586cff12471215ee29d9ba87f5da7f21.png)

**2、我们能写哪些表达式呢？**

```
Simple expressions:（表达式语法）
Variable Expressions: ${...}：获取变量值；OGNL；
    1）、获取对象的属性、调用方法
    2）、使用内置的基本对象：#18
         #ctx : the context object.
         #vars: the context variables.
         #locale : the context locale.
         #request : (only in Web Contexts) the HttpServletRequest object.
         #response : (only in Web Contexts) the HttpServletResponse object.
         #session : (only in Web Contexts) the HttpSession object.
         #servletContext : (only in Web Contexts) the ServletContext object.

    3）、内置的一些工具对象：
　　　　　　#execInfo : information about the template being processed.
　　　　　　#uris : methods for escaping parts of URLs/URIs
　　　　　　#conversions : methods for executing the configured conversion service (if any).
　　　　　　#dates : methods for java.util.Date objects: formatting, component extraction, etc.
　　　　　　#calendars : analogous to #dates , but for java.util.Calendar objects.
　　　　　　#numbers : methods for formatting numeric objects.
　　　　　　#strings : methods for String objects: contains, startsWith, prepending/appending, etc.
　　　　　　#objects : methods for objects in general.
　　　　　　#bools : methods for boolean evaluation.
　　　　　　#arrays : methods for arrays.
　　　　　　#lists : methods for lists.
　　　　　　#sets : methods for sets.
　　　　　　#maps : methods for maps.
　　　　　　#aggregates : methods for creating aggregates on arrays or collections.
==================================================================================

  Selection Variable Expressions: *{...}：选择表达式：和${}在功能上是一样；
  Message Expressions: #{...}：获取国际化内容
  Link URL Expressions: @{...}：定义URL；
  Fragment Expressions: ~{...}：片段引用表达式

Literals（字面量）
      Text literals: 'one text' , 'Another one!' ,…
      Number literals: 0 , 34 , 3.0 , 12.3 ,…
      Boolean literals: true , false
      Null literal: null
      Literal tokens: one , sometext , main ,…
      
Text operations:（文本操作）
    String concatenation: +
    Literal substitutions: |The name is ${name}|
    
Arithmetic operations:（数学运算）
    Binary operators: + , - , * , / , %
    Minus sign (unary operator): -
    
Boolean operations:（布尔运算）
    Binary operators: and , or
    Boolean negation (unary operator): ! , not
    
Comparisons and equality:（比较运算）
    Comparators: > , < , >= , <= ( gt , lt , ge , le )
    Equality operators: == , != ( eq , ne )
    
Conditional operators:条件运算（三元运算符）
    If-then: (if) ? (then)
    If-then-else: (if) ? (then) : (else)
    Default: (value) ?: (defaultvalue)
    
Special tokens:
    No-Operation: _
```

**练习测试：**

1、 我们编写一个 Controller，放一些数据

```
@RequestMapping("/t2")
public String test2(Map<String,Object> map){
    //存入数据
    map.put("msg","<h1>Hello</h1>");
    map.put("users", Arrays.asList("qinjiang","kuangshen"));
    //classpath:/templates/test.html
    return "test";
}
```

2、测试页面取出数据

```
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
    <meta charset="UTF-8">
    <title>狂神说</title>
</head>
<body>
<h1>测试页面</h1>

<div th:text="${msg}"></div>
<!--不转义-->
<div th:utext="${msg}"></div>

<!--遍历数据-->
<!--th:each每次遍历都会生成当前这个标签：官网#9-->
<h4 th:each="user :${users}" th:text="${user}"></h4>

<h4>
    <!--行内写法：官网#12-->
    <span th:each="user:${users}">[[${user}]]</span>
</h4>

</body>
</html>
```

3、启动项目测试！

**我们看完语法，很多样式，我们即使现在学习了，也会忘记，所以我们在学习过程中，需要使用什么，根据官方文档来查询，才是最重要的，要熟练使用官方文档！**

P12、MVC 自动配置原理
--------------

### 12.1、官网阅读

在进行项目编写前，我们还需要知道一个东西，就是 SpringBoot 对我们的 SpringMVC 还做了哪些配置，包括如何扩展，如何定制。

只有把这些都搞清楚了，我们在之后使用才会更加得心应手。途径一：源码分析，途径二：官方文档！

地址 ：https://docs.spring.io/spring-boot/docs/2.2.5.RELEASE/reference/htmlsingle/#boot-features-spring-mvc-auto-configuration

```
Spring MVC Auto-configuration
// Spring Boot为Spring MVC提供了自动配置，它可以很好地与大多数应用程序一起工作。
Spring Boot provides auto-configuration for Spring MVC that works well with most applications.
// 自动配置在Spring默认设置的基础上添加了以下功能：
The auto-configuration adds the following features on top of Spring’s defaults:
// 包含视图解析器
Inclusion of ContentNegotiatingViewResolver and BeanNameViewResolver beans.
// 支持静态资源文件夹的路径，以及webjars
Support for serving static resources, including support for WebJars 
// 自动注册了Converter：
// 转换器，这就是我们网页提交数据到后台自动封装成为对象的东西，比如把"1"字符串自动转换为int类型
// Formatter：【格式化器，比如页面给我们了一个2019-8-10，它会给我们自动格式化为Date对象】
Automatic registration of Converter, GenericConverter, and Formatter beans.
// HttpMessageConverters
// SpringMVC用来转换Http请求和响应的的，比如我们要把一个User对象转换为JSON字符串，可以去看官网文档解释；
Support for HttpMessageConverters (covered later in this document).
// 定义错误代码生成规则的
Automatic registration of MessageCodesResolver (covered later in this document).
// 首页定制
Static index.html support.
// 图标定制
Custom Favicon support (covered later in this document).
// 初始化数据绑定器：帮我们把请求数据绑定到JavaBean中！
Automatic use of a ConfigurableWebBindingInitializer bean (covered later in this document).

/*
如果您希望保留Spring Boot MVC功能，并且希望添加其他MVC配置（拦截器、格式化程序、视图控制器和其他功能），则可以添加自己
的@configuration类，类型为webmvcconfiguer，但不添加@EnableWebMvc。如果希望提供
RequestMappingHandlerMapping、RequestMappingHandlerAdapter或ExceptionHandlerExceptionResolver的自定义
实例，则可以声明WebMVCregistrationAdapter实例来提供此类组件。
*/
If you want to keep Spring Boot MVC features and you want to add additional MVC configuration 
(interceptors, formatters, view controllers, and other features), you can add your own 
@Configuration class of type WebMvcConfigurer but without @EnableWebMvc. If you wish to provide 
custom instances of RequestMappingHandlerMapping, RequestMappingHandlerAdapter, or 
ExceptionHandlerExceptionResolver, you can declare a WebMvcRegistrationsAdapter instance to provide such components.

// 如果您想完全控制Spring MVC，可以添加自己的@Configuration，并用@EnableWebMvc进行注释。
If you want to take complete control of Spring MVC, you can add your own @Configuration annotated with @EnableWebMvc.
```

我们来仔细对照，看一下它怎么实现的，它告诉我们 SpringBoot 已经帮我们自动配置好了 SpringMVC，然后自动配置了哪些东西呢？

### 12.2、ContentNegotiatingViewResolver 内容协商视图解析器

自动配置了 ViewResolver，就是我们之前学习的 SpringMVC 的视图解析器；

即根据方法的返回值取得视图对象（View），然后由视图对象决定如何渲染（转发，重定向）。

我们去看看这里的源码：我们找到 WebMvcAutoConfiguration ， 然后搜索 ContentNegotiatingViewResolver。找到如下方法！

```
@Bean
@ConditionalOnBean(ViewResolver.class)
@ConditionalOnMissingBean(name = "viewResolver", value = ContentNegotiatingViewResolver.class)
public ContentNegotiatingViewResolver viewResolver(BeanFactory beanFactory) {
    ContentNegotiatingViewResolver resolver = new ContentNegotiatingViewResolver();
    resolver.setContentNegotiationManager(beanFactory.getBean(ContentNegotiationManager.class));
    // ContentNegotiatingViewResolver使用所有其他视图解析器来定位视图，因此它应该具有较高的优先级
    resolver.setOrder(Ordered.HIGHEST_PRECEDENCE);
    return resolver;
}
```

我们可以点进这类看看！找到对应的解析视图的代码；

```
@Nullable // 注解说明：@Nullable 即参数可为null
public View resolveViewName(String viewName, Locale locale) throws Exception {
    RequestAttributes attrs = RequestContextHolder.getRequestAttributes();
    Assert.state(attrs instanceof ServletRequestAttributes, "No current ServletRequestAttributes");
    List<MediaType> requestedMediaTypes = this.getMediaTypes(((ServletRequestAttributes)attrs).getRequest());
    if (requestedMediaTypes != null) {
        // 获取候选的视图对象
        List<View> candidateViews = this.getCandidateViews(viewName, locale, requestedMediaTypes);
        // 选择一个最适合的视图对象，然后把这个对象返回
        View bestView = this.getBestView(candidateViews, requestedMediaTypes, attrs);
        if (bestView != null) {
            return bestView;
        }
    }
    // .....
}
```

我们继续点进去看，他是怎么获得候选的视图的呢？

getCandidateViews 中看到他是把所有的视图解析器拿来，进行 while 循环，挨个解析！

```
Iterator var5 = this.viewResolvers.iterator();
```

所以得出结论：**ContentNegotiatingViewResolver 这个视图解析器就是用来组合所有的视图解析器的**

我们再去研究下他的组合逻辑，看到有个属性 viewResolvers，看看它是在哪里进行赋值的！

```
protected void initServletContext(ServletContext servletContext) {
    // 这里它是从beanFactory工具中获取容器中的所有视图解析器
    // ViewRescolver.class 把所有的视图解析器来组合的
    Collection<ViewResolver> matchingBeans = BeanFactoryUtils.beansOfTypeIncludingAncestors(this.obtainApplicationContext(), ViewResolver.class).values();
    ViewResolver viewResolver;
    if (this.viewResolvers == null) {
        this.viewResolvers = new ArrayList(matchingBeans.size());
    }
    // ...............
}
```

既然它是在容器中去找视图解析器，我们是否可以猜想，我们就可以去实现一个视图解析器了呢？

我们可以自己给容器中去添加一个视图解析器；这个类就会帮我们自动的将它组合进来；**我们去实现一下**

1、我们在我们的主程序中去写一个视图解析器来试试；

```
@Bean //放到bean中
public ViewResolver myViewResolver(){
    return new MyViewResolver();
}

//我们写一个静态内部类，视图解析器就需要实现ViewResolver接口
private static class MyViewResolver implements ViewResolver{
    @Override
    public View resolveViewName(String s, Locale locale) throws Exception {
        return null;
    }
}
```

2、怎么看我们自己写的视图解析器有没有起作用呢？

我们给 DispatcherServlet 中的 doDispatch 方法 加个断点进行调试一下，因为所有的请求都会走到这个方法中

![](https://img-blog.csdnimg.cn/img_convert/1af49a3b82ed4eb6e983cf40849f1df8.png)

3、我们启动我们的项目，然后随便访问一个页面，看一下 Debug 信息；

找到 this

![](https://img-blog.csdnimg.cn/img_convert/da94e712a5cf0e947ff6b06b62f1cb08.png)

找到视图解析器，我们看到我们自己定义的就在这里了；

![](https://img-blog.csdnimg.cn/img_convert/f8de080062640b693111dfdcd336631f.png)

所以说，我们如果想要使用自己定制化的东西，我们只需要给容器中添加这个组件就好了！剩下的事情 SpringBoot 就会帮我们做了！

### 12.3、转换器和格式化器

找到格式化转换器：

```
@Bean
@Override
public FormattingConversionService mvcConversionService() {
    // 拿到配置文件中的格式化规则
    WebConversionService conversionService = 
        new WebConversionService(this.mvcProperties.getDateFormat());
    addFormatters(conversionService);
    return conversionService;
}
```

点击去：

```
public String getDateFormat() {
    return this.dateFormat;
}

/**
* Date format to use. For instance, `dd/MM/yyyy`. 默认的
 */
private String dateFormat;
```

可以看到在我们的 Properties 文件中，我们可以进行自动配置它！

如果配置了自己的格式化方式，就会注册到 Bean 中生效，我们可以在配置文件中配置日期格式化的规则：

![](https://img-blog.csdnimg.cn/img_convert/b4735809104d12f32a7ed1c6f048c45b.png)

其余的就不一一举例了，大家可以下去多研究探讨即可！

### 12.4、修改 SpringBoot 的默认配置

这么多的自动配置，原理都是一样的，通过这个 WebMVC 的自动配置原理分析，我们要学会一种学习方式，通过源码探究，得出结论；这个结论一定是属于自己的，而且一通百通。

SpringBoot 的底层，大量用到了这些设计细节思想，所以，没事需要多阅读源码！得出结论；

SpringBoot 在自动配置很多组件的时候，先看容器中有没有用户自己配置的（如果用户自己配置 @bean），如果有就用用户配置的，如果没有就用自动配置的；

如果有些组件可以存在多个，比如我们的视图解析器，就将用户配置的和自己默认的组合起来！

**扩展使用 SpringMVC** 官方文档如下：

If you want to keep Spring Boot MVC features and you want to add additional MVC configuration (interceptors, formatters, view controllers, and other features), you can add your own @Configuration class of type WebMvcConfigurer but without @EnableWebMvc. If you wish to provide custom instances of RequestMappingHandlerMapping, RequestMappingHandlerAdapter, or ExceptionHandlerExceptionResolver, you can declare a WebMvcRegistrationsAdapter instance to provide such components.

我们要做的就是编写一个 @Configuration 注解类，并且类型要为 WebMvcConfigurer，还不能标注 @EnableWebMvc 注解；我们去自己写一个；我们新建一个包叫 config，写一个类 MyMvcConfig；

```
//应为类型要求为WebMvcConfigurer，所以我们实现其接口
//可以使用自定义类扩展MVC的功能
@Configuration
public class MyMvcConfig implements WebMvcConfigurer {

    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        // 浏览器发送/test ， 就会跳转到test页面；
        registry.addViewController("/test").setViewName("test");
    }
}
```

我们去浏览器访问一下：

![](https://img-blog.csdnimg.cn/img_convert/dbce122c3d56e5ef17323b29f4fb043f.png)

**确实也跳转过来了！所以说，我们要扩展 SpringMVC，官方就推荐我们这么去使用，既保 SpringBoot 留所有的自动配置，也能用我们扩展的配置！**

我们可以去分析一下原理：

1、WebMvcAutoConfiguration 是 SpringMVC 的自动配置类，里面有一个类 WebMvcAutoConfigurationAdapter

2、这个类上有一个注解，在做其他自动配置时会导入：@Import(EnableWebMvcConfiguration.class)

3、我们点进 EnableWebMvcConfiguration 这个类看一下，它继承了一个父类：DelegatingWebMvcConfiguration

这个父类中有这样一段代码：

```
public class DelegatingWebMvcConfiguration extends WebMvcConfigurationSupport {
    private final WebMvcConfigurerComposite configurers = new WebMvcConfigurerComposite();
    
  // 从容器中获取所有的webmvcConfigurer
    @Autowired(required = false)
    public void setConfigurers(List<WebMvcConfigurer> configurers) {
        if (!CollectionUtils.isEmpty(configurers)) {
            this.configurers.addWebMvcConfigurers(configurers);
        }
    }
}
```

4、我们可以在这个类中去寻找一个我们刚才设置的 viewController 当做参考，发现它调用了一个

```
protected void addViewControllers(ViewControllerRegistry registry) {
    this.configurers.addViewControllers(registry);
}
```

5、我们点进去看一下

```
public void addViewControllers(ViewControllerRegistry registry) {
    Iterator var2 = this.delegates.iterator();

    while(var2.hasNext()) {
        // 将所有的WebMvcConfigurer相关配置来一起调用！包括我们自己配置的和Spring给我们配置的
        WebMvcConfigurer delegate = (WebMvcConfigurer)var2.next();
        delegate.addViewControllers(registry);
    }

}
```

所以得出结论：所有的 WebMvcConfiguration 都会被作用，不止 Spring 自己的配置类，我们自己的配置类当然也会被调用；

### 12.5、全面接管 SpringMVC

官方文档：

```
If you want to take complete control of Spring MVC
you can add your own @Configuration annotated with @EnableWebMvc.
```

全面接管即：SpringBoot 对 SpringMVC 的自动配置不需要了，所有都是我们自己去配置！

只需在我们的配置类中要加一个 @EnableWebMvc。

我们看下如果我们全面接管了 SpringMVC 了，我们之前 SpringBoot 给我们配置的静态资源映射一定会无效，我们可以去测试一下；

不加注解之前，访问首页：

![](https://img-blog.csdnimg.cn/img_convert/d5baaadd4dee1245ee4d9fb10c11b6bb.png)

给配置类加上注解：@EnableWebMvc

![](https://img-blog.csdnimg.cn/img_convert/cf7863f7a5d4ee6ecd2c5aa201c9af8d.png)

我们发现所有的 SpringMVC 自动配置都失效了！回归到了最初的样子；

**当然，我们开发中，不推荐使用全面接管 SpringMVC**

思考问题？为什么加了一个注解，自动配置就失效了！我们看下源码：

1、这里发现它是导入了一个类，我们可以继续进去看

```
@Import({DelegatingWebMvcConfiguration.class})public @interface EnableWebMvc {}
```

2、它继承了一个父类 WebMvcConfigurationSupport

```
public class DelegatingWebMvcConfiguration extends WebMvcConfigurationSupport {  // ......}
```

3、我们来回顾一下 Webmvc 自动配置类

```
@Configuration(proxyBeanMethods = false)
@ConditionalOnWebApplication(type = Type.SERVLET)
@ConditionalOnClass({ Servlet.class, DispatcherServlet.class, WebMvcConfigurer.class })
// 这个注解的意思就是：容器中没有这个组件的时候，这个自动配置类才生效
@ConditionalOnMissingBean(WebMvcConfigurationSupport.class)
@AutoConfigureOrder(Ordered.HIGHEST_PRECEDENCE + 10)
@AutoConfigureAfter({ DispatcherServletAutoConfiguration.class, TaskExecutionAutoConfiguration.class,
    ValidationAutoConfiguration.class })
public class WebMvcAutoConfiguration {
    
}
```

总结一句话：@EnableWebMvc 将 WebMvcConfigurationSupport 组件导入进来了；

而导入的 WebMvcConfigurationSupport 只是 SpringMVC 最基本的功能！

**在 SpringBoot 中会有非常多的扩展配置，只要看见了这个，我们就应该多留心注意~**

P13、页面国际化
---------

有的时候，我们的网站会去涉及中英文甚至多语言的切换，这时候我们就需要学习国际化了！

### 13.1、准备工作

先在 IDEA 中统一设置 properties 的编码问题！

![](https://img-blog.csdnimg.cn/img_convert/609cc0020ab86ed034a14df5935b1696.png)

编写国际化配置文件，抽取页面需要显示的国际化页面消息。我们可以去登录页面查看一下，哪些内容我们需要编写国际化的配置！

### 13.2、配置文件编写

1、我们在 resources 资源文件下新建一个 i18n 目录，存放国际化配置文件

2、建立一个 login.properties 文件，还有一个 login_zh_CN.properties；发现 IDEA 自动识别了我们要做国际化操作；文件夹变了！

![](https://img-blog.csdnimg.cn/img_convert/033747a0c47f9b7a05a98582053129be.png)

3、我们可以在这上面去新建一个文件；

![](https://img-blog.csdnimg.cn/img_convert/51789db1202458b24a7dcfcbbe994120.png)

弹出如下页面：我们再添加一个英文的；

![](https://img-blog.csdnimg.cn/img_convert/11a63cfc8a5168f629fbd429b78e986c.png)

这样就快捷多了！

![](https://img-blog.csdnimg.cn/img_convert/bd1f55e5b0cf9c1ad5b4ce6aaf350fd3.png)

**4、接下来，我们就来编写配置，我们可以看到 idea 下面有另外一个视图；**

![](https://img-blog.csdnimg.cn/img_convert/1cc5e471fc8cda1a1b867520e2dd2e61.png)

这个视图我们点击 + 号就可以直接添加属性了；我们新建一个 login.tip，可以看到边上有三个文件框可以输入

![](https://img-blog.csdnimg.cn/img_convert/454d033d7e5de0e9fbce70dc9aa237b4.png)

我们添加一下首页的内容！

![](https://img-blog.csdnimg.cn/img_convert/b21fe2f0a6f1c41fefde28d6239a1425.png)

然后依次添加其他页面内容即可！

![](https://img-blog.csdnimg.cn/img_convert/5a5ba72abd5285080db60759baa8f0ce.png)

然后去查看我们的配置文件；

login.properties ：默认

```
login.btn=登录
login.password=密码
login.remember=记住我
login.tip=请登录
login.username=用户名
```

英文：

```
login.btn=Sign in
login.password=Password
login.remember=Remember me
login.tip=Please sign in
login.username=Username
```

中文：

```
login.btn=登录
login.password=密码
login.remember=记住我
login.tip=请登录
login.username=用户名
```

OK，配置文件步骤搞定！

### 13.3、配置文件生效探究

我们去看一下 SpringBoot 对国际化的自动配置！这里又涉及到一个类：MessageSourceAutoConfiguration

里面有一个方法，这里发现 SpringBoot 已经自动配置好了管理我们国际化资源文件的组件 ResourceBundleMessageSource；

```
// 获取 properties 传递过来的值进行判断
@Bean
public MessageSource messageSource(MessageSourceProperties properties) {
    ResourceBundleMessageSource messageSource = new ResourceBundleMessageSource();
    if (StringUtils.hasText(properties.getBasename())) {
        // 设置国际化文件的基础名（去掉语言国家代码的）
        messageSource.setBasenames(
            StringUtils.commaDelimitedListToStringArray(
                                       StringUtils.trimAllWhitespace(properties.getBasename())));
    }
    if (properties.getEncoding() != null) {
        messageSource.setDefaultEncoding(properties.getEncoding().name());
    }
    messageSource.setFallbackToSystemLocale(properties.isFallbackToSystemLocale());
    Duration cacheDuration = properties.getCacheDuration();
    if (cacheDuration != null) {
        messageSource.setCacheMillis(cacheDuration.toMillis());
    }
    messageSource.setAlwaysUseMessageFormat(properties.isAlwaysUseMessageFormat());
    messageSource.setUseCodeAsDefaultMessage(properties.isUseCodeAsDefaultMessage());
    return messageSource;
}
```

我们真实 的情况是放在了 i18n 目录下，所以我们要去配置这个 messages 的路径；

```
spring.messages.basename=i18n.login
```

### 13.4、配置页面国际化值

去页面获取国际化的值，查看 Thymeleaf 的文档，找到 message 取值操作为：#{…}。我们去页面测试下：

IDEA 还有提示，非常智能的！

![](https://img-blog.csdnimg.cn/img_convert/b2c86af81af87827c3ef29d8459e14e6.png)

我们可以去启动项目，访问一下，发现已经自动识别为中文的了！

![](https://img-blog.csdnimg.cn/img_convert/a00cd236ee44dc4c3a51d92d52f41d6f.png)

**但是我们想要更好！可以根据按钮自动切换中文英文！**

### 13.5、配置国际化解析

在 Spring 中有一个国际化的 Locale （区域信息对象）；里面有一个叫做 LocaleResolver （获取区域信息对象）的解析器！

我们去我们 webmvc 自动配置文件，寻找一下！看到 SpringBoot 默认配置：

```
@Bean
@ConditionalOnMissingBean
@ConditionalOnProperty(prefix = "spring.mvc", name = "locale")
public LocaleResolver localeResolver() {
    // 容器中没有就自己配，有的话就用用户配置的
    if (this.mvcProperties.getLocaleResolver() == WebMvcProperties.LocaleResolver.FIXED) {
        return new FixedLocaleResolver(this.mvcProperties.getLocale());
    }
    // 接收头国际化分解
    AcceptHeaderLocaleResolver localeResolver = new AcceptHeaderLocaleResolver();
    localeResolver.setDefaultLocale(this.mvcProperties.getLocale());
    return localeResolver;
}
```

AcceptHeaderLocaleResolver 这个类中有一个方法

```
public Locale resolveLocale(HttpServletRequest request) {
    Locale defaultLocale = this.getDefaultLocale();
    // 默认的就是根据请求头带来的区域信息获取Locale进行国际化
    if (defaultLocale != null && request.getHeader("Accept-Language") == null) {
        return defaultLocale;
    } else {
        Locale requestLocale = request.getLocale();
        List<Locale> supportedLocales = this.getSupportedLocales();
        if (!supportedLocales.isEmpty() && !supportedLocales.contains(requestLocale)) {
            Locale supportedLocale = this.findSupportedLocale(request, supportedLocales);
            if (supportedLocale != null) {
                return supportedLocale;
            } else {
                return defaultLocale != null ? defaultLocale : requestLocale;
            }
        } else {
            return requestLocale;
        }
    }
}
```

那假如我们现在想点击链接让我们的国际化资源生效，就需要让我们自己的 Locale 生效！

我们去自己写一个自己的 LocaleResolver，可以在链接上携带区域信息！

修改一下前端页面的跳转连接：

```
<!-- 这里传入参数不需要使用 ？使用 （key=value）-->
<a class="btn btn-sm" th:href="@{/index.html(l='zh_CN')}">中文</a>
<a class="btn btn-sm" th:href="@{/index.html(l='en_US')}">English</a>
```

我们去写一个处理的组件类！

```
package com.kuang.component;

import org.springframework.util.StringUtils;
import org.springframework.web.servlet.LocaleResolver;

import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.util.Locale;

//可以在链接上携带区域信息
public class MyLocaleResolver implements LocaleResolver {

    //解析请求
    @Override
    public Locale resolveLocale(HttpServletRequest request) {

        String language = request.getParameter("l");
        Locale locale = Locale.getDefault(); // 如果没有获取到就使用系统默认的
        //如果请求链接不为空
        if (!StringUtils.isEmpty(language)){
            //分割请求参数
            String[] split = language.split("_");
            //国家，地区
            locale = new Locale(split[0],split[1]);
        }
        return locale;
    }

    @Override
    public void setLocale(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Locale locale) {

    }
}
```

为了让我们的区域化信息能够生效，我们需要再配置一下这个组件！在我们自己的 MvcConofig 下添加 bean；

```
@Beanpublic LocaleResolver localeResolver(){    return new MyLocaleResolver();}
```

**我们重启项目，来访问一下，发现点击按钮可以实现成功切换！搞定收工！**

P14、集成 Swagger 终极版
------------------

![](https://img-blog.csdnimg.cn/img_convert/12ed84cb478a56d22d0565d3feddd26e.png)

**学习目标：**

*   了解 Swagger 的概念及作用
*   掌握在项目中集成 Swagger 自动生成 API 文档

### 14.1、Swagger 简介

**前后端分离**

*   前端 -> 前端控制层、视图层
*   后端 -> 后端控制层、服务层、数据访问层
*   前后端通过 API 进行交互
*   前后端相对独立且松耦合

**产生的问题**

*   前后端集成，前端或者后端无法做到 “及时协商，尽早解决”，最终导致问题集中爆发

**解决方案**

*   首先定义 schema [计划的提纲]，并实时跟踪最新的 API，降低集成风险

**Swagger**

*   号称世界上最流行的 API 框架
*   Restful Api 文档在线自动生成器 => **API 文档 与 API 定义同步更新**
*   直接运行，在线测试 API
*   支持多种语言 （如：Java，PHP 等）
*   官网：https://swagger.io/

### 14.2、SpringBoot 集成 Swagger

**SpringBoot 集成 Swagger** => **springfox**，两个 jar 包

*   **Springfox-swagger2**
*   swagger-springmvc

**使用 Swagger**

要求：jdk 1.8 + 否则 swagger2 无法运行

步骤：

1、新建一个 SpringBoot-web 项目

2、添加 Maven 依赖

```
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger2 -->
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger2</artifactId>
   <version>2.9.2</version>
</dependency>
<!-- https://mvnrepository.com/artifact/io.springfox/springfox-swagger-ui -->
<dependency>
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger-ui</artifactId>
   <version>2.9.2</version>
</dependency>
```

3、编写 HelloController，测试确保运行成功！

4、要使用 Swagger，我们需要编写一个配置类 - SwaggerConfig 来配置 Swagger

```
@Configuration //配置类
@EnableSwagger2// 开启Swagger2的自动配置
public class SwaggerConfig {  
}j
```

5、访问测试 ：http://localhost:8080/swagger-ui.html ，可以看到 swagger 的界面；

![](https://img-blog.csdnimg.cn/img_convert/492bb4b3a2ee560d9e6bd022d5861361.png)

### 14.3、配置 Swagger

1、Swagger 实例 Bean 是 Docket，所以通过配置 Docket 实例来配置 Swaggger。

```
@Bean //配置docket以配置Swagger具体参数
public Docket docket() {
   return new Docket(DocumentationType.SWAGGER_2);
}
```

2、可以通过 apiInfo() 属性配置文档信息

```
//配置文档信息
private ApiInfo apiInfo() {
   Contact contact = new Contact("联系人名字", "http://xxx.xxx.com/联系人访问链接", "联系人邮箱");
   return new ApiInfo(
           "Swagger学习", // 标题
           "学习演示如何配置Swagger", // 描述
           "v1.0", // 版本
           "http://terms.service.url/组织链接", // 组织链接
           contact, // 联系人信息
           "Apach 2.0 许可", // 许可
           "许可链接", // 许可连接
           new ArrayList<>()// 扩展
  );
}
```

3、Docket 实例关联上 apiInfo()

```
@Bean
public Docket docket() {
   return new Docket(DocumentationType.SWAGGER_2).apiInfo(apiInfo());
}
```

4、重启项目，访问测试 http://localhost:8080/swagger-ui.html 看下效果；

### 14.4、配置扫描接口

1、构建 Docket 时通过 select() 方法配置怎么扫描接口。

```
any() // 扫描所有，项目中的所有接口都会被扫描到
none() // 不扫描接口
// 通过方法上的注解扫描，如withMethodAnnotation(GetMapping.class)只扫描get请求
withMethodAnnotation(final Class<? extends Annotation> annotation)
// 通过类上的注解扫描，如.withClassAnnotation(Controller.class)只扫描有controller注解的类中的接口
withClassAnnotation(final Class<? extends Annotation> annotation)
basePackage(final String basePackage) // 根据包路径扫描接口
```

2、重启项目测试，由于我们配置根据包的路径扫描接口，所以我们只能看到一个类

3、除了通过包路径配置扫描接口外，还可以通过配置其他方式扫描接口，这里注释一下所有的配置方式：

```
any() // 扫描所有，项目中的所有接口都会被扫描到
none() // 不扫描接口
// 通过方法上的注解扫描，如withMethodAnnotation(GetMapping.class)只扫描get请求
withMethodAnnotation(final Class<? extends Annotation> annotation)
// 通过类上的注解扫描，如.withClassAnnotation(Controller.class)只扫描有controller注解的类中的接口
withClassAnnotation(final Class<? extends Annotation> annotation)
basePackage(final String basePackage) // 根据包路径扫描接口
```

4、除此之外，我们还可以配置接口扫描过滤：

```
@Bean
public Docket docket() {
   return new Docket(DocumentationType.SWAGGER_2)
      .apiInfo(apiInfo())
      .select()// 通过.select()方法，去配置扫描接口,RequestHandlerSelectors配置如何扫描接口
      .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
       // 配置如何通过path过滤,即这里只扫描请求以/kuang开头的接口
      .paths(PathSelectors.ant("/kuang/**"))
      .build();
}
```

5、这里的可选值还有

```
any() // 任何请求都扫描
none() // 任何请求都不扫描
regex(final String pathRegex) // 通过正则表达式控制
ant(final String antPattern) // 通过ant()控制
```

![](https://img-blog.csdnimg.cn/img_convert/14d62bb94d49b004b47fc263de40cc94.png)

### 14.5、配置 Swagger 开关

1、通过 enable() 方法配置是否启用 swagger，如果是 false，swagger 将不能在浏览器中访问了

```
@Bean
public Docket docket() {
   return new Docket(DocumentationType.SWAGGER_2)
      .apiInfo(apiInfo())
      .enable(false) //配置是否启用Swagger，如果是false，在浏览器将无法访问
      .select()// 通过.select()方法，去配置扫描接口,RequestHandlerSelectors配置如何扫描接口
      .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
       // 配置如何通过path过滤,即这里只扫描请求以/kuang开头的接口
      .paths(PathSelectors.ant("/kuang/**"))
      .build();
}
```

2、如何动态配置当项目处于 test、dev 环境时显示 swagger，处于 prod 时不显示？

```
@Bean
public Docket docket(Environment environment) {
   // 设置要显示swagger的环境
   Profiles of = Profiles.of("dev", "test");
   // 判断当前是否处于该环境
   // 通过 enable() 接收此参数判断是否要显示
   boolean b = environment.acceptsProfiles(of);
   
   return new Docket(DocumentationType.SWAGGER_2)
      .apiInfo(apiInfo())
      .enable(b) //配置是否启用Swagger，如果是false，在浏览器将无法访问
      .select()// 通过.select()方法，去配置扫描接口,RequestHandlerSelectors配置如何扫描接口
      .apis(RequestHandlerSelectors.basePackage("com.kuang.swagger.controller"))
       // 配置如何通过path过滤,即这里只扫描请求以/kuang开头的接口
      .paths(PathSelectors.ant("/kuang/**"))
      .build();
}
```

3、可以在项目中增加一个 dev 的配置文件查看效果！

![](https://img-blog.csdnimg.cn/img_convert/44b9ae10d370c42aa8ba007bf59c5484.png)

### 14.6、配置 API 分组

![](https://img-blog.csdnimg.cn/img_convert/0ab111afc4a0fadccf05a6e48bce7d35.png)

1、如果没有配置分组，默认是 default。通过 groupName() 方法即可配置分组：

```
@Bean
public Docket docket(Environment environment) {
   return new Docket(DocumentationType.SWAGGER_2).apiInfo(apiInfo())
      .groupName("hello") // 配置分组
       // 省略配置....
}
```

2、重启项目查看分组

3、如何配置多个分组？配置多个分组只需要配置多个 docket 即可：

```
@Bean
public Docket docket1(){
   return new Docket(DocumentationType.SWAGGER_2).groupName("group1");
}
@Bean
public Docket docket2(){
   return new Docket(DocumentationType.SWAGGER_2).groupName("group2");
}
@Bean
public Docket docket3(){
   return new Docket(DocumentationType.SWAGGER_2).groupName("group3");
}
```

4、重启项目查看即可

### 14.7、实体配置

1、新建一个实体类

```
@ApiModel("用户实体")
public class User {
   @ApiModelProperty("用户名")
   public String username;
   @ApiModelProperty("密码")
   public String password;
}
```

2、只要这个实体在**请求接口**的返回值上（即使是泛型），都能映射到实体项中：

```
@RequestMapping("/getUser")
public User getUser(){   
	return new User();
}
```

3、重启查看测试

![](https://img-blog.csdnimg.cn/img_convert/7944265d2423c309830a7d5fc41b3198.png)

注：并不是因为 @ApiModel 这个注解让实体显示在这里了，而是只要出现在接口方法的返回值上的实体都会显示在这里，而 @ApiModel 和 @ApiModelProperty 这两个注解只是为实体添加注释的。

@ApiModel 为类添加注释

@ApiModelProperty 为类属性添加注释

### 14.8、常用注解

Swagger 的所有注解定义在 io.swagger.annotations 包下

下面列一些经常用到的，未列举出来的可以另行查阅说明：

<table><thead><tr><th>Swagger 注解</th><th>简单说明</th></tr></thead><tbody><tr><td>@Api(tags = “xxx 模块说明”)</td><td>作用在模块类上</td></tr><tr><td>@ApiOperation(“xxx 接口说明”)</td><td>作用在接口方法上</td></tr><tr><td>@ApiModel(“xxxPOJO 说明”)</td><td>作用在模型类上：如 VO、BO</td></tr><tr><td>@ApiModelProperty(value = “xxx 属性说明”,hidden = true)</td><td>作用在类方法和属性上，hidden 设置为 true 可以隐藏该属性</td></tr><tr><td>@ApiParam(“xxx 参数说明”)</td><td>作用在参数、方法和字段上，类似 @ApiModelProperty</td></tr></tbody></table>

我们也可以给请求的接口配置一些注释

```
@ApiOperation("狂神的接口")
@PostMapping("/kuang")
@ResponseBody
public String kuang(@ApiParam("这个名字会被返回")String username){
   return username;
}
```

这样的话，可以给一些比较难理解的属性或者接口，增加一些配置信息，让人更容易阅读！

相较于传统的 Postman 或 Curl 方式测试接口，使用 swagger 简直就是傻瓜式操作，不需要额外说明文档 (写得好本身就是文档) 而且更不容易出错，只需要录入数据然后点击 Execute，如果再配合自动化框架，可以说基本就不需要人为操作了。

Swagger 是个优秀的工具，现在国内已经有很多的中小型互联网公司都在使用它，相较于传统的要先出 Word 接口文档再测试的方式，显然这样也更符合现在的快速迭代开发行情。当然了，提醒下大家在正式环境要记得关闭 Swagger，一来出于安全考虑二来也可以节省运行时内存。

### 14.9、拓展：其他皮肤

我们可以导入不同的包实现不同的皮肤定义：

1、默认的 **访问 http://localhost:8080/swagger-ui.html**

```
<dependency> 
   <groupId>io.springfox</groupId>
   <artifactId>springfox-swagger-ui</artifactId>
   <version>2.9.2</version>
</dependency>
```

![](https://img-blog.csdnimg.cn/img_convert/a239787cc74bf762cfc01881088fbe8c.png)

2、bootstrap-ui **访问 http://localhost:8080/doc.html**

```
<!-- 引入swagger-bootstrap-ui包 /doc.html-->
<dependency>
   <groupId>com.github.xiaoymin</groupId>
   <artifactId>swagger-bootstrap-ui</artifactId>
   <version>1.9.1</version>
</dependency>
```

![](https://img-blog.csdnimg.cn/img_convert/4b5607bfdc22b68c160ed314fc71020b.png)

3、Layui-ui **访问 http://localhost:8080/docs.html**

```
<!-- 引入swagger-ui-layer包 /docs.html-->
<dependency>
   <groupId>com.github.caspar-chen</groupId>
   <artifactId>swagger-ui-layer</artifactId>
   <version>1.1.3</version>
</dependency>
```

![](https://img-blog.csdnimg.cn/img_convert/77058260c3fb24f010e712cf549847d3.png)

4、mg-ui **访问 http://localhost:8080/document.html**

```
<!-- 引入swagger-ui-layer包 /document.html-->
<dependency>
   <groupId>com.zyplayer</groupId>
   <artifactId>swagger-mg-ui</artifactId>
   <version>1.0.6</version>
</dependency>
```

![](https://img-blog.csdnimg.cn/img_convert/12a9f9a7515755ea1147069b2993ca53.png)

P15、异步、定时、邮件任务
--------------

前言

> 在我们的工作中，常常会用到异步处理任务，比如我们在网站上发送邮件，后台会去发送邮件，此时前台会造成响应不动，直到邮件发送完毕，响应才会成功，所以我们一般会采用多线程的方式去处理这些任务。还有一些定时任务，比如需要在每天凌晨的时候，分析一次前一天的日志信息。还有就是邮件的发送，微信的前身也是邮件服务呢？这些东西都是怎么实现的呢？其实 SpringBoot 都给我们提供了对应的支持，我们上手使用十分的简单，只需要开启一些注解支持，配置一些配置文件即可！那我们来看看吧~

### 15.1、异步任务

1、创建一个 service 包

2、创建一个类 AsyncService

异步处理还是非常常用的，比如我们在网站上发送邮件，后台会去发送邮件，此时前台会造成响应不动，直到邮件发送完毕，响应才会成功，所以我们一般会采用多线程的方式去处理这些任务。

编写方法，假装正在处理数据，使用线程设置一些延时，模拟同步等待的情况；

```
@Service
public class AsyncService {

   public void hello(){
       try {
           Thread.sleep(3000);
      } catch (InterruptedException e) {
           e.printStackTrace();
      }
       System.out.println("业务进行中....");
  }
}
```

3、编写 controller 包

4、编写 AsyncController 类

我们去写一个 Controller 测试一下

```
@RestController
public class AsyncController {

   @Autowired
   AsyncService asyncService;

   @GetMapping("/hello")
   public String hello(){
       asyncService.hello();
       return "success";
  }

}
```

5、访问 http://localhost:8080/hello 进行测试，3 秒后出现 success，这是同步等待的情况。

问题：我们如果想让用户直接得到消息，就在后台使用多线程的方式进行处理即可，但是每次都需要自己手动去编写多线程的实现的话，太麻烦了，我们只需要用一个简单的办法，在我们的方法上加一个简单的注解即可，如下：

6、给 hello 方法添加 @Async 注解；

```
//告诉Spring这是一个异步方法
@Async
public void hello(){
   try {
       Thread.sleep(3000);
  } catch (InterruptedException e) {
       e.printStackTrace();
  }
   System.out.println("业务进行中....");
}
```

SpringBoot 就会自己开一个线程池，进行调用！但是要让这个注解生效，我们还需要在主程序上添加一个注解 @EnableAsync ，开启异步注解功能；

```
@EnableAsync //开启异步注解功能
@SpringBootApplication
public class SpringbootTaskApplication {

   public static void main(String[] args) {
       SpringApplication.run(SpringbootTaskApplication.class, args);
  }

}
```

7、重启测试，网页瞬间响应，后台代码依旧执行！

### 15.2、定时任务

项目开发中经常需要执行一些定时任务，比如需要在每天凌晨的时候，分析一次前一天的日志信息，Spring 为我们提供了异步执行任务调度的方式，提供了两个接口。

*   TaskExecutor 接口
*   TaskScheduler 接口

两个注解：

*   @EnableScheduling
*   @Scheduled

**cron 表达式：**

![](https://img-blog.csdnimg.cn/img_convert/8f04e7e77880e04c0a184e2a2b475841.png)

![](https://img-blog.csdnimg.cn/img_convert/c784995cd91b7e7ae64a474275961389.png)

**测试步骤：**

1、创建一个 ScheduledService

我们里面存在一个 hello 方法，他需要定时执行，怎么处理呢？

```
@Service
public class ScheduledService {
   
   //秒   分   时     日   月   周几
   //0 * * * * MON-FRI
   //注意cron表达式的用法；
   @Scheduled(cron = "0 * * * * 0-7")
   public void hello(){
       System.out.println("hello.....");
  }
}
```

2、这里写完定时任务之后，我们需要在主程序上增加 @EnableScheduling 开启定时任务功能

```
@EnableAsync //开启异步注解功能
@EnableScheduling //开启基于注解的定时任务
@SpringBootApplication
public class SpringbootTaskApplication {

   public static void main(String[] args) {
       SpringApplication.run(SpringbootTaskApplication.class, args);
  }

}
```

3、我们来详细了解下 cron 表达式；

http://www.bejson.com/othertools/cron/

4、常用的表达式

```
(1）0/2 * * * * ?   表示每2秒 执行任务
（1）0 0/2 * * * ?   表示每2分钟 执行任务
（1）0 0 2 1 * ?   表示在每月的1日的凌晨2点调整任务
（2）0 15 10 ? * MON-FRI   表示周一到周五每天上午10:15执行作业
（3）0 15 10 ? 6L 2002-2006   表示2002-2006年的每个月的最后一个星期五上午10:15执行作
（4）0 0 10,14,16 * * ?   每天上午10点，下午2点，4点
（5）0 0/30 9-17 * * ?   朝九晚五工作时间内每半小时
（6）0 0 12 ? * WED   表示每个星期三中午12点
（7）0 0 12 * * ?   每天中午12点触发
（8）0 15 10 ? * *   每天上午10:15触发
（9）0 15 10 * * ?     每天上午10:15触发
（10）0 15 10 * * ?   每天上午10:15触发
（11）0 15 10 * * ? 2005   2005年的每天上午10:15触发
（12）0 * 14 * * ?     在每天下午2点到下午2:59期间的每1分钟触发
（13）0 0/5 14 * * ?   在每天下午2点到下午2:55期间的每5分钟触发
（14）0 0/5 14,18 * * ?     在每天下午2点到2:55期间和下午6点到6:55期间的每5分钟触发
（15）0 0-5 14 * * ?   在每天下午2点到下午2:05期间的每1分钟触发
（16）0 10,44 14 ? 3 WED   每年三月的星期三的下午2:10和2:44触发
（17）0 15 10 ? * MON-FRI   周一至周五的上午10:15触发
（18）0 15 10 15 * ?   每月15日上午10:15触发
（19）0 15 10 L * ?   每月最后一日的上午10:15触发
（20）0 15 10 ? * 6L   每月的最后一个星期五上午10:15触发
（21）0 15 10 ? * 6L 2002-2005   2002年至2005年的每月的最后一个星期五上午10:15触发
（22）0 15 10 ? * 6#3   每月的第三个星期五上午10:15触发
```

### 15.3、邮件任务

邮件发送，在我们的日常开发中，也非常的多，Springboot 也帮我们做了支持

*   邮件发送需要引入 spring-boot-start-mail
*   SpringBoot 自动配置 MailSenderAutoConfiguration
*   定义 MailProperties 内容，配置在 application.yml 中
*   自动装配 JavaMailSender
*   测试邮件发送

**测试：**

1、引入 pom 依赖

```
<<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-mail</artifactId>
</dependency>
```

看它引入的依赖，可以看到 jakarta.mail

```
<dependency>
   <groupId>com.sun.mail</groupId>
   <artifactId>jakarta.mail</artifactId>
   <version>1.6.4</version>
   <scope>compile</scope>
</dependency>
```

2、查看自动配置类：MailSenderAutoConfiguration

![](https://img-blog.csdnimg.cn/img_convert/ef7988bbd631480107dbd61335a7b5aa.png)

这个类中存在 bean，JavaMailSenderImpl

![](https://img-blog.csdnimg.cn/img_convert/904e9eb362abe51a76f9006df5f4cf95.png)

然后我们去看下配置文件

```
@ConfigurationProperties(
   prefix = "spring.mail"
)
public class MailProperties {
   private static final Charset DEFAULT_CHARSET;
   private String host;
   private Integer port;
   private String username;
   private String password;
   private String protocol = "smtp";
   private Charset defaultEncoding;
   private Map<String, String> properties;
   private String jndiName;
}
```

3、配置文件：

```
spring.mail.username=135@qq.comspring.mail.password=你的qq授权码
spring.mail.host=smtp.qq.com# qq需要配置sslspring.mail.properties.mail.smtp.ssl.enable=true
```

获取授权码：在 QQ 邮箱中的设置 -> 账户 -> 开启 pop3 和 smtp 服务

![](https://img-blog.csdnimg.cn/img_convert/e78a60910df651f42032fb9637de8758.png)

4、Spring 单元测试

```
@Autowired
JavaMailSenderImpl mailSender;

@Test
public void contextLoads() {
   //邮件设置1：一个简单的邮件
   SimpleMailMessage message = new SimpleMailMessage();
   message.setSubject("通知-明天来狂神这听课");
   message.setText("今晚7:30开会");

   message.setTo("24736743@qq.com");
   message.setFrom("24736743@qq.com");
   mailSender.send(message);
}

@Test
public void contextLoads2() throws MessagingException {
   //邮件设置2：一个复杂的邮件
   MimeMessage mimeMessage = mailSender.createMimeMessage();
   MimeMessageHelper helper = new MimeMessageHelper(mimeMessage, true);

   helper.setSubject("通知-明天来狂神这听课");
   helper.setText("<b style='color:red'>今天 7:30来开会</b>",true);

   //发送附件
   helper.addAttachment("1.jpg",new File(""));
   helper.addAttachment("2.jpg",new File(""));

   helper.setTo("24736743@qq.com");
   helper.setFrom("24736743@qq.com");

   mailSender.send(mimeMessage);
}
```

查看邮箱，邮件接收成功！

我们只需要使用 Thymeleaf 进行前后端结合即可开发自己网站邮件收发功能了！

P16、富文本编辑器
----------

### 16.1、简介

思考：我们平时在博客园，或者 CSDN 等平台进行写作的时候，有同学思考过他们的编辑器是怎么实现的吗？

在博客园后台的选项设置中，可以看到一个文本编辑器的选项：

![](https://img-blog.csdnimg.cn/img_convert/06e597f1bee829b195cd193a1ff7fdd6.png)

其实这个就是富文本编辑器，市面上有许多非常成熟的富文本编辑器，比如：

*   **Editor.md**——功能非常丰富的编辑器，左端编辑，右端预览，非常方便，完全免费
*   *   官网：https://pandao.github.io/editor.md/
*   **wangEditor**——基于 javascript 和 css 开发的 Web 富文本编辑器， 轻量、简洁、界面美观、易用、开源免费。
*   *   官网：http://www.wangeditor.com/
*   **TinyMCE**——TinyMCE 是一个轻量级的基于浏览器的所见即所得编辑器，由 JavaScript 写成。它对 IE6 + 和 Firefox1.5 + 都有着非常良好的支持。功能齐全，界面美观，就是文档是英文的，对开发人员英文水平有一定要求。
*   *   官网：https://www.tiny.cloud/docs/demo/full-featured/
    *   博客园
*   **百度 ueditor**——UEditor 是由百度 web 前端研发部开发所见即所得富文本 web 编辑器，具有轻量，功能齐全，可定制，注重用户体验等特点，开源基于 MIT 协议，允许自由使用和修改代码，缺点是已经没有更新了
*   *   官网：https://ueditor.baidu.com/website/onlinedemo.html
*   **kindeditor**——界面经典。
*   *   官网：http://kindeditor.net/demo.php
*   **Textbox**——Textbox 是一款极简但功能强大的在线文本编辑器，支持桌面设备和移动设备。主要功能包含内置的图像处理和存储、文件拖放、拼写检查和自动更正。此外，该工具还实现了屏幕阅读器等辅助技术，并符合 WAI-ARIA 可访问性标准。
*   *   官网：https://textbox.io/
*   **CKEditor**——国外的，界面美观。
*   *   官网：https://ckeditor.com/ckeditor-5/demo/
*   **quill**——功能强大，还可以编辑公式等
*   *   官网：https://quilljs.com/
*   **simditor**——界面美观，功能较全。
*   *   官网：https://simditor.tower.im/
*   **summernote**——UI 好看，精美
*   *   官网：https://summernote.org/
*   **jodit**——功能齐全
*   *   官网：https://xdsoft.net/jodit/
*   **froala Editor**——界面非常好看，功能非常强大，非常好用（非免费）
*   *   官网：https://www.froala.com/wysiwyg-editor

总之，目前可用的富文本编辑器有很多… 这只是其中的一部分

### 16.2、Editor.md

我这里使用的就是 Editor.md，作为一个资深码农，Mardown 必然是我们程序猿最喜欢的格式，看下面，就爱上了！

![](https://img-blog.csdnimg.cn/img_convert/1bbbb8ab091585d942c623ff68d3f60e.png)

我们可以在官网下载它：https://pandao.github.io/editor.md/ ， 得到它的压缩包！

解压以后，在 examples 目录下面，可以看到他的很多案例使用！学习，其实就是看人家怎么写的，然后进行模仿就好了！

我们可以将整个解压的文件倒入我们的项目，将一些无用的测试和案例删掉即可！

### 16.3、基础工程搭建

> 数据库设计

article：文章表

<table><thead><tr><th>字段</th><th></th><th>备注</th></tr></thead><tbody><tr><td>id</td><td>int</td><td>文章的唯一 ID</td></tr><tr><td>author</td><td>varchar</td><td>作者</td></tr><tr><td>title</td><td>varchar</td><td>标题</td></tr><tr><td>content</td><td>longtext</td><td>文章的内容</td></tr></tbody></table>

建表 SQL：

```
CREATE TABLE `article` (
`id` int(10) NOT NULL AUTO_INCREMENT COMMENT 'int文章的唯一ID',
`author` varchar(50) NOT NULL COMMENT '作者',
`title` varchar(100) NOT NULL COMMENT '标题',
`content` longtext NOT NULL COMMENT '文章的内容',
PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8
```

> 基础项目搭建

1、建一个 SpringBoot 项目配置

```
spring:
datasource:
  username: root
  password: 123456
  #?serverTimezone=UTC解决时区的报错
  url: jdbc:mysql://localhost:3306/springboot?serverTimezone=UTC&useUnicode=true&characterEncoding=utf-8
  driver-class-name: com.mysql.cj.jdbc.Driver
<resources>
   <resource>
       <directory>src/main/java</directory>
       <includes>
           <include>**/*.xml</include>
       </includes>
       <filtering>true</filtering>
   </resource>
</resources>
```

2、实体类：

```
//文章类
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Article implements Serializable {

   private int id; //文章的唯一ID
   private String author; //作者名
   private String title; //标题
   private String content; //文章的内容

}
```

3、mapper 接口：

```
@Mapper
@Repository
public interface ArticleMapper {
   //查询所有的文章
   List<Article> queryArticles();

   //新增一个文章
   int addArticle(Article article);

   //根据文章id查询文章
   Article getArticleById(int id);

   //根据文章id删除文章
   int deleteArticleById(int id);

}
```

**既然已经提供了 myBatis 的映射配置文件，自然要告诉 spring boot 这些文件的位置**

```
mybatis:
mapper-locations: classpath:com/kuang/mapper/*.xml
type-aliases-package: com.kuang.pojo
```

编写一个 Controller 测试下，是否 ok；

### 16.4、文章编辑整合（重点）

1、导入 editor.md 资源 ，删除多余文件

2、编辑文章页面 editor.html、需要引入 jQuery；

```
<!DOCTYPE html>
<html class="x-admin-sm" lang="zh" xmlns:th="http://www.thymeleaf.org">

<head>
   <meta charset="UTF-8">
   <title>秦疆'Blog</title>
   <meta >
   <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
   <meta  />
   <!--Editor.md-->
   <link rel="stylesheet" th:href="@{/editormd/css/editormd.css}"/>
   <link rel="shortcut icon" href="https://pandao.github.io/editor.md/favicon.ico" type="image/x-icon" />
</head>

<body>

<div class="layui-fluid">
   <div class="layui-row layui-col-space15">
       <div class="layui-col-md12">
           <!--博客表单-->
           <form >
               <div>
                  标题：<input type="text" >
               </div>
               <div>
                  作者：<input type="text" >
               </div>
               <div id="article-content">
                   <textarea > </textarea>
               </div>
           </form>

       </div>
   </div>
</div>
</body>

<!--editormd-->
<script th:src="@{/editormd/lib/jquery.min.js}"></script>
<script th:src="@{/editormd/editormd.js}"></script>

<script type="text/javascript">
   var testEditor;

   //window.onload = function(){ }
   $(function() {
       testEditor = editormd("article-content", {
           width : "95%",
           height : 400,
           syncScrolling : "single",
           path : "../editormd/lib/",
           saveHTMLToTextarea : true,    // 保存 HTML 到 Textarea
           emoji: true,
           theme: "dark",//工具栏主题
           previewTheme: "dark",//预览主题
           editorTheme: "pastel-on-dark",//编辑主题
           tex : true,                   // 开启科学公式TeX语言支持，默认关闭
           flowChart : true,             // 开启流程图支持，默认关闭
           sequenceDiagram : true,       // 开启时序/序列图支持，默认关闭,
           //图片上传
           imageUpload : true,
           imageFormats : ["jpg", "jpeg", "gif", "png", "bmp", "webp"],
           imageUploadURL : "/article/file/upload",
           onload : function() {
               console.log('onload', this);
          },
           /*指定需要显示的功能按钮*/
           toolbarIcons : function() {
               return ["undo","redo","|",
                   "bold","del","italic","quote","ucwords","uppercase","lowercase","|",
                   "h1","h2","h3","h4","h5","h6","|",
                   "list-ul","list-ol","hr","|",
                   "link","reference-link","image","code","preformatted-text",
                   "code-block","table","datetime","emoji","html-entities","pagebreak","|",
                   "goto-line","watch","preview","fullscreen","clear","search","|",
                   "help","info","releaseIcon", "index"]
          },

           /*自定义功能按钮，下面我自定义了2个，一个是发布，一个是返回首页*/
           toolbarIconTexts : {
               releaseIcon : "<span bgcolor=\"gray\">发布</span>",
               index : "<span bgcolor=\"red\">返回首页</span>",
          },

           /*给自定义按钮指定回调函数*/
           toolbarHandlers:{
               releaseIcon : function(cm, icon, cursor, selection) {
                   //表单提交
                   mdEditorForm.method = "post";
                   mdEditorForm.action = "/article/addArticle";//提交至服务器的路径
                   mdEditorForm.submit();
              },
               index : function(){
                   window.location.href = '/';
              },
          }
      });
  });
</script>

</html>
```

3、编写 Controller，进行跳转，以及保存文章

```
@Controller
@RequestMapping("/article")
public class ArticleController {

   @GetMapping("/toEditor")
   public String toEditor(){
       return "editor";
  }
   
   @PostMapping("/addArticle")
   public String addArticle(Article article){
       articleMapper.addArticle(article);
       return "editor";
  }
   
}
```

> 图片上传问题

1、前端 js 中添加配置

```
//图片上传
imageUpload : true,
imageFormats : ["jpg", "jpeg", "gif", "png", "bmp", "webp"],
imageUploadURL : "/article/file/upload", // //这个是上传图片时的访问地址
```

2、后端请求，接收保存这个图片, 需要导入 FastJson 的依赖！

```
//博客图片上传问题
@RequestMapping("/file/upload")
@ResponseBody
public JSONObject fileUpload(@RequestParam(value = "editormd-image-file", required = true) MultipartFile file, HttpServletRequest request) throws IOException {
   //上传路径保存设置

   //获得SpringBoot当前项目的路径：System.getProperty("user.dir")
   String path = System.getProperty("user.dir")+"/upload/";

   //按照月份进行分类：
   Calendar instance = Calendar.getInstance();
   String month = (instance.get(Calendar.MONTH) + 1)+"月";
   path = path+month;

   File realPath = new File(path);
   if (!realPath.exists()){
       realPath.mkdir();
  }

   //上传文件地址
   System.out.println("上传文件保存地址："+realPath);

   //解决文件名字问题：我们使用uuid;
   String filename = "ks-"+UUID.randomUUID().toString().replaceAll("-", "");
   //通过CommonsMultipartFile的方法直接写文件（注意这个时候）
   file.transferTo(new File(realPath +"/"+ filename));

   //给editormd进行回调
   JSONObject res = new JSONObject();
   res.put("url","/upload/"+month+"/"+ filename);
   res.put("success", 1);
   res.put("message", "upload success!");

   return res;
}
```

3、解决文件回显显示的问题，设置虚拟目录映射！在我们自己拓展的 MvcConfig 中进行配置即可！

```
@Configuration
public class MyMvcConfig implements WebMvcConfigurer {

   // 文件保存在真实目录/upload/下，
   // 访问的时候使用虚路径/upload，比如文件名为1.png，就直接/upload/1.png就ok了。
   @Override
   public void addResourceHandlers(ResourceHandlerRegistry registry) {
       registry.addResourceHandler("/upload/**")
          .addResourceLocations("file:"+System.getProperty("user.dir")+"/upload/");
  }

}
```

> 表情包问题

自己手动下载，emoji 表情包，放到图片路径下：

修改 editormd.js 文件

```
// Emoji graphics files url path
editormd.emoji     = {
   path : "../editormd/plugins/emoji-dialog/emoji/",
   ext   : ".png"
};
```

### 16.5、文章展示

1、Controller 中增加方法

```
@GetMapping("/{id}")
public String show(@PathVariable("id") int id,Model model){
   Article article = articleMapper.getArticleById(id);
   model.addAttribute("article",article);
   return "article";
}
```

2、编写页面 article.html

```
<!DOCTYPE html>
<html lang="en" xmlns:th="http://www.thymeleaf.org">
<head>
   <meta charset="UTF-8">
   <meta >
   <title th:text="${article.title}"></title>
</head>
<body>

<div>
   <!--文章头部信息：标题，作者，最后更新日期，导航-->
   <h2 style="margin: auto 0" th:text="${article.title}"></h2>
  作者：<span style="float: left" th:text="${article.author}"></span>
   <!--文章主体内容-->
   <div id="doc-content">
       <textarea style="display:none;" placeholder="markdown" th:text="${article.content}"></textarea>
   </div>

</div>

<link rel="stylesheet" th:href="@{/editormd/css/editormd.preview.css}" />
<script th:src="@{/editormd/lib/jquery.min.js}"></script>
<script th:src="@{/editormd/lib/marked.min.js}"></script>
<script th:src="@{/editormd/lib/prettify.min.js}"></script>
<script th:src="@{/editormd/lib/raphael.min.js}"></script>
<script th:src="@{/editormd/lib/underscore.min.js}"></script>
<script th:src="@{/editormd/lib/sequence-diagram.min.js}"></script>
<script th:src="@{/editormd/lib/flowchart.min.js}"></script>
<script th:src="@{/editormd/lib/jquery.flowchart.min.js}"></script>
<script th:src="@{/editormd/editormd.js}"></script>

<script type="text/javascript">
   var testEditor;
   $(function () {
       testEditor = editormd.markdownToHTML("doc-content", {//注意：这里是上面DIV的id
           htmlDecode: "style,script,iframe",
           emoji: true,
           taskList: true,
           tocm: true,
           tex: true, // 默认不解析
           flowChart: true, // 默认不解析
           sequenceDiagram: true, // 默认不解析
           codeFold: true
      });});
</script>
</body>
</html>
```

重启项目，访问进行测试！大功告成！

小结：

有了富文本编辑器，我们网站的功能就会又多一项，大家到了这里完全可以有时间写一个属于自己的博客网站了，根据所学的知识是完全没有任何问题的！

P17、Dubbo 和 Zookeeper 集成
------------------------

分布式理论

### 17.1、什么是分布式系统？

在《分布式系统原理与范型》一书中有如下定义：“分布式系统是若干独立计算机的集合，这些计算机对于用户来说就像单个相关系统”；

分布式系统是由一组通过网络进行通信、为了完成共同的任务而协调工作的计算机节点组成的系统。分布式系统的出现是为了用廉价的、普通的机器完成单个计算机无法完成的计算、存储任务。其目的是**利用更多的机器，处理更多的数据**。

分布式系统（distributed system）是建立在网络之上的软件系统。

首先需要明确的是，只有当单个节点的处理能力无法满足日益增长的计算、存储任务的时候，且硬件的提升（加内存、加磁盘、使用更好的 CPU）高昂到得不偿失的时候，应用程序也不能进一步优化的时候，我们才需要考虑分布式系统。因为，分布式系统要解决的问题本身就是和单机系统一样的，而由于分布式系统多节点、通过网络通信的拓扑结构，会引入很多单机系统没有的问题，为了解决这些问题又会引入更多的机制、协议，带来更多的问题。。。

### 17.2、Dubbo 文档

随着互联网的发展，网站应用的规模不断扩大，常规的垂直应用架构已无法应对，分布式服务架构以及流动计算架构势在必行，急需**一个治理系统**确保架构有条不紊的演进。

在 Dubbo 的官网文档有这样一张图

![](https://img-blog.csdnimg.cn/img_convert/9f43f2cbdbc68a35973a28884a7049e6.png)

#### 单一应用架构

当网站流量很小时，只需一个应用，将所有功能都部署在一起，以减少部署节点和成本。此时，用于简化增删改查工作量的数据访问框架 (ORM) 是关键。

![](https://img-blog.csdnimg.cn/img_convert/741e3959ba748d0edfe3cf796860cb11.png)

适用于小型网站，小型管理系统，将所有功能都部署到一个功能里，简单易用。

**缺点：**

1、性能扩展比较难

2、协同开发问题

3、不利于升级维护

#### 垂直应用架构

当访问量逐渐增大，单一应用增加机器带来的加速度越来越小，将应用拆成互不相干的几个应用，以提升效率。此时，用于加速前端页面开发的 Web 框架 (MVC) 是关键。

![](https://img-blog.csdnimg.cn/img_convert/1fc602518f825631ba43c6886ded06bb.png)

通过切分业务来实现各个模块独立部署，降低了维护和部署的难度，团队各司其职更易管理，性能扩展也更方便，更有针对性。

缺点：公用模块无法重复利用，开发性的浪费

#### 分布式服务架构

当垂直应用越来越多，应用之间交互不可避免，将核心业务抽取出来，作为独立的服务，逐渐形成稳定的服务中心，使前端应用能更快速的响应多变的市场需求。此时，用于提高业务复用及整合的 ** 分布式服务框架 (RPC)** 是关键。

![](https://img-blog.csdnimg.cn/img_convert/5b4209a4fa8483d8d4b83cb98022fb79.png)

#### 流动计算架构

当服务越来越多，容量的评估，小服务资源的浪费等问题逐渐显现，此时需增加一个调度中心基于访问压力实时管理集群容量，提高集群利用率。此时，用于**提高机器利用率的资源调度和治理中心** (SOA)[ Service Oriented Architecture] 是关键。

![](https://img-blog.csdnimg.cn/img_convert/7d348758d13420316ff6e6c03bb41bcd.png)

什么是 RPC

RPC【Remote Procedure Call】是指远程过程调用，是一种进程间通信方式，他是一种技术的思想，而不是规范。它允许程序调用另一个地址空间（通常是共享网络的另一台机器上）的过程或函数，而不用程序员显式编码这个远程调用的细节。即程序员无论是调用本地的还是远程的函数，本质上编写的调用代码基本相同。

也就是说两台服务器 A，B，一个应用部署在 A 服务器上，想要调用 B 服务器上应用提供的函数 / 方法，由于不在一个内存空间，不能直接调用，需要通过网络来表达调用的语义和传达调用的数据。为什么要用 RPC 呢？就是无法在一个进程内，甚至一个计算机内通过本地调用的方式完成的需求，比如不同的系统间的通讯，甚至不同的组织间的通讯，由于计算能力需要横向扩展，需要在多台机器组成的集群上部署应用。RPC 就是要像调用本地的函数一样去调远程函数；

推荐阅读文章：https://www.jianshu.com/p/2accc2840a1b

**RPC 基本原理**

![](https://img-blog.csdnimg.cn/img_convert/7e83afcf4189173c7e7a744a86a1c0d2.png)

**步骤解析：**

![](https://img-blog.csdnimg.cn/img_convert/1687cf48cad068a97cef3ef4f231efac.png)

RPC 两个核心模块：通讯，序列化。

测试环境搭建

#### Dubbo

Apache Dubbo |ˈdʌbəʊ| 是一款高性能、轻量级的开源 Java RPC 框架，它提供了三大核心能力：面向接口的远程方法调用，智能容错和负载均衡，以及服务自动注册和发现。

dubbo 官网 http://dubbo.apache.org/zh-cn/index.html

1. 了解 Dubbo 的特性

2. 查看官方文档

**dubbo 基本概念**

![](https://img-blog.csdnimg.cn/img_convert/f35eade3aca40e126dbbc734351133e7.png)

**服务提供者**（Provider）：暴露服务的服务提供方，服务提供者在启动时，向注册中心注册自己提供的服务。

**服务消费者**（Consumer）：调用远程服务的服务消费方，服务消费者在启动时，向注册中心订阅自己所需的服务，服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用。

**注册中心**（Registry）：注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者

**监控中心**（Monitor）：服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心

**调用关系说明**

l 服务容器负责启动，加载，运行服务提供者。

l 服务提供者在启动时，向注册中心注册自己提供的服务。

l 服务消费者在启动时，向注册中心订阅自己所需的服务。

l 注册中心返回服务提供者地址列表给消费者，如果有变更，注册中心将基于长连接推送变更数据给消费者。

l 服务消费者，从提供者地址列表中，基于软负载均衡算法，选一台提供者进行调用，如果调用失败，再选另一台调用。

l 服务消费者和提供者，在内存中累计调用次数和调用时间，定时每分钟发送一次统计数据到监控中心。

#### Dubbo 环境搭建

点进 dubbo 官方文档，推荐我们使用 Zookeeper 注册中心

什么是 zookeeper 呢？可以查看官方文档

#### Window 下安装 zookeeper

1、下载 zookeeper ：地址， 我们下载 3.4.14 ， 最新版！解压 zookeeper

2、运行 / bin/zkServer.cmd ，初次运行会报错，没有 zoo.cfg 配置文件；

可能遇到问题：闪退 !

解决方案：编辑 zkServer.cmd 文件末尾添加 pause 。这样运行出错就不会退出，会提示错误信息，方便找到原因。

![](https://img-blog.csdnimg.cn/img_convert/37b2592b9b2b2a7030cc440d91241762.png)

![](https://img-blog.csdnimg.cn/img_convert/4093aba48bc0edda3b8dcde2cf3f89a3.png)

3、修改 zoo.cfg 配置文件

将 conf 文件夹下面的 zoo_sample.cfg 复制一份改名为 zoo.cfg 即可。

注意几个重要位置：

dataDir=./ 临时数据存储的目录（可写相对路径）

clientPort=2181 zookeeper 的端口号

修改完成后再次启动 zookeeper

![](https://img-blog.csdnimg.cn/img_convert/65649169ff9471a8ea50ae7a7012c83b.png)

4、使用 zkCli.cmd 测试

ls /：列出 zookeeper 根下保存的所有节点

```
[zk: 127.0.0.1:2181(CONNECTED) 4] ls /[zookeeper]
```

create –e /kuangshen 123：创建一个 kuangshen 节点，值为 123

![](https://img-blog.csdnimg.cn/img_convert/359e288fec986ea261c9960532c71590.png)

get /kuangshen：获取 / kuangshen 节点的值

![](https://img-blog.csdnimg.cn/img_convert/078f73d023d281a5a4a47cb7b67a62a2.png)

我们再来查看一下节点

![](https://img-blog.csdnimg.cn/img_convert/672f10004f002801ebda1c85518256e7.png)

#### window 下安装 dubbo-admin

dubbo 本身并不是一个服务软件。它其实就是一个 jar 包，能够帮你的 java 程序连接到 zookeeper，并利用 zookeeper 消费、提供服务。

但是为了让用户更好的管理监控众多的 dubbo 服务，官方提供了一个可视化的监控程序 dubbo-admin，不过这个监控即使不装也不影响使用。

我们这里来安装一下：

**1、下载 dubbo-admin**

地址 ：https://github.com/apache/dubbo-admin/tree/master

**2、解压进入目录**

修改 dubbo-admin\src\main\resources \application.properties 指定 zookeeper 地址

```
server.port=7001spring.velocity.cache=falsespring.velocity.charset=UTF-8spring.velocity.layout-url=/templates/default.vmspring.messages.fallback-to-system-locale=falsespring.messages.basename=i18n/messagespring.root.password=rootspring.guest.password=guestdubbo.registry.address=zookeeper://127.0.0.1:2181
```

**3、在项目目录下**打包 dubbo-admin

```
mvn clean package -Dmaven.test.skip=true
```

**第一次打包的过程有点慢，需要耐心等待！直到成功！**

![](https://img-blog.csdnimg.cn/img_convert/936497f80483dcd1c568433ea5de66b1.png)

4、执行 dubbo-admin\target 下的 dubbo-admin-0.0.1-SNAPSHOT.jar

```
java -jar dubbo-admin-0.0.1-SNAPSHOT.jar
```

【注意：zookeeper 的服务一定要打开！】

执行完毕，我们去访问一下 http://localhost:7001/ ， 这时候我们需要输入登录账户和密码，我们都是默认的 root-root；

登录成功后，查看界面

![](https://img-blog.csdnimg.cn/img_convert/dc89de37adb24864cb79fe9876094b15.png)

安装完成！

### 17.3、SpringBoot + Dubbo + zookeeper

#### 框架搭建

**1. 启 zookeeper ！**

**2. IDEA 创建一个空项目；**

**3. 创建一个模块，实现服务提供者：provider-server ， 选择 web 依赖即可**

**4. 项目创建完毕，我们写一个服务，比如卖票的服务；**

编写接口

```
package com.kuang.provider.service;

public interface TicketService {
   public String getTicket();
}
```

编写实现类

```
package com.kuang.provider.service;

public class TicketServiceImpl implements TicketService {
   @Override
   public String getTicket() {
       return "《狂神说Java》";
  }
}
```

**5. 创建一个模块，实现服务消费者：consumer-server ， 选择 web 依赖即可**

**6. 项目创建完毕，我们写一个服务，比如用户的服务；**

编写 service

```
package com.kuang.consumer.service;

public class UserService {
   //我们需要去拿去注册中心的服务
}
```

**需求：现在我们的用户想使用买票的服务，这要怎么弄呢 ？**

#### 服务提供者

**1、将服务提供者注册到注册中心，我们需要整合 Dubbo 和 zookeeper，所以需要导包**

**我们从 dubbo 官网进入 github，看下方的帮助文档，找到 dubbo-springboot，找到依赖包**

```
<!-- Dubbo Spring Boot Starter -->
<dependency>
   <groupId>org.apache.dubbo</groupId>
   <artifactId>dubbo-spring-boot-starter</artifactId>
   <version>2.7.3</version>
</dependency>
```

**zookeeper 的包我们去 maven 仓库下载，zkclient；**

```
<!-- https://mvnrepository.com/artifact/com.github.sgroschupf/zkclient -->
<dependency>
   <groupId>com.github.sgroschupf</groupId>
   <artifactId>zkclient</artifactId>
   <version>0.1</version>
</dependency>
```

**【新版的坑】zookeeper 及其依赖包，解决日志冲突，还需要剔除日志依赖；**

```
<!-- 引入zookeeper -->
<dependency>
   <groupId>org.apache.curator</groupId>
   <artifactId>curator-framework</artifactId>
   <version>2.12.0</version>
</dependency>
<dependency>
   <groupId>org.apache.curator</groupId>
   <artifactId>curator-recipes</artifactId>
   <version>2.12.0</version>
</dependency>
<dependency>
   <groupId>org.apache.zookeeper</groupId>
   <artifactId>zookeeper</artifactId>
   <version>3.4.14</version>
   <!--排除这个slf4j-log4j12-->
   <exclusions>
       <exclusion>
           <groupId>org.slf4j</groupId>
           <artifactId>slf4j-log4j12</artifactId>
       </exclusion>
   </exclusions>
</dependency>
```

**2、在 springboot 配置文件中配置 dubbo 相关属性！**

```
#当前应用名字
dubbo.application.name=provider-server
#注册中心地址
dubbo.registry.address=zookeeper://127.0.0.1:2181
#扫描指定包下服务
dubbo.scan.base-packages=com.kuang.provider.service
```

**3、在 service 的实现类中配置服务注解，发布服务！注意导包问题**

```
import org.apache.dubbo.config.annotation.Service;
import org.springframework.stereotype.Component;

@Service //将服务发布出去
@Component //放在容器中
public class TicketServiceImpl implements TicketService {
   @Override
   public String getTicket() {
       return "《狂神说Java》";
  }
}
```

**逻辑理解 ：应用启动起来，dubbo 就会扫描指定的包下带有 @component 注解的服务，将它发布在指定的注册中心中！**

#### 服务消费者

**1、导入依赖，和之前的依赖一样；**

```
<!--dubbo-->
<!-- Dubbo Spring Boot Starter -->
<dependency>
   <groupId>org.apache.dubbo</groupId>
   <artifactId>dubbo-spring-boot-starter</artifactId>
   <version>2.7.3</version>
</dependency>
<!--zookeeper-->
<!-- https://mvnrepository.com/artifact/com.github.sgroschupf/zkclient -->
<dependency>
   <groupId>com.github.sgroschupf</groupId>
   <artifactId>zkclient</artifactId>
   <version>0.1</version>
</dependency>
<!-- 引入zookeeper -->
<dependency>
   <groupId>org.apache.curator</groupId>
   <artifactId>curator-framework</artifactId>
   <version>2.12.0</version>
</dependency>
<dependency>
   <groupId>org.apache.curator</groupId>
   <artifactId>curator-recipes</artifactId>
   <version>2.12.0</version>
</dependency>
<dependency>
   <groupId>org.apache.zookeeper</groupId>
   <artifactId>zookeeper</artifactId>
   <version>3.4.14</version>
   <!--排除这个slf4j-log4j12-->
   <exclusions>
       <exclusion>
           <groupId>org.slf4j</groupId>
           <artifactId>slf4j-log4j12</artifactId>
       </exclusion>
   </exclusions>
</dependency>
```

2、**配置参数**

```
#当前应用名字
dubbo.application.name=consumer-server
#注册中心地址
dubbo.registry.address=zookeeper://127.0.0.1:2181
```

**3. 本来正常步骤是需要将服务提供者的接口打包，然后用 pom 文件导入，我们这里使用简单的方式，直接将服务的接口拿过来，路径必须保证正确，即和服务提供者相同；**

![](https://img-blog.csdnimg.cn/img_convert/c0a7a5b3975aa181b42731df39978f79.png)

**4. 完善消费者的服务类**

```
package com.kuang.consumer.service;

import com.kuang.provider.service.TicketService;
import org.apache.dubbo.config.annotation.Reference;
import org.springframework.stereotype.Service;

@Service //注入到容器中
public class UserService {

   @Reference //远程引用指定的服务，他会按照全类名进行匹配，看谁给注册中心注册了这个全类名
   TicketService ticketService;

   public void bugTicket(){
       String ticket = ticketService.getTicket();
       System.out.println("在注册中心买到"+ticket);
  }

}
```

**5. 测试类编写；**

```
@RunWith(SpringRunner.class)
@SpringBootTest
public class ConsumerServerApplicationTests {

   @Autowired
   UserService userService;

   @Test
   public void contextLoads() {

       userService.bugTicket();

  }

}
```

#### 启动测试

**1. 开启 zookeeper**

**2. 打开 dubbo-admin 实现监控【可以不用做】**

**3. 开启服务者**

**4. 消费者消费测试，结果：**

![](https://img-blog.csdnimg.cn/img_convert/9c925f66564614cd99abc1e5ab29b66d.png)

**监控中心 ：**

![](https://img-blog.csdnimg.cn/img_convert/00bd4db7f8a48dfd68c51ef3a64ed76a.png)

**ok , 这就是 SpingBoot + dubbo + zookeeper 实现分布式开发的应用，其实就是一个服务拆分的思想；**

P18、集成 SpringSecurity
---------------------

### 18.1、安全简介

在 Web 开发中，安全一直是非常重要的一个方面。安全虽然属于应用的非功能性需求，但是应该在应用开发的初期就考虑进来。如果在应用开发的后期才考虑安全的问题，就可能陷入一个两难的境地：一方面，应用存在严重的安全漏洞，无法满足用户的要求，并可能造成用户的隐私数据被攻击者窃取；另一方面，应用的基本架构已经确定，要修复安全漏洞，可能需要对系统的架构做出比较重大的调整，因而需要更多的开发时间，影响应用的发布进程。因此，从应用开发的第一天就应该把安全相关的因素考虑进来，并在整个应用的开发过程中。

市面上存在比较有名的：Shiro，Spring Security ！

这里需要阐述一下的是，每一个框架的出现都是为了解决某一问题而产生了，那么 Spring Security 框架的出现是为了解决什么问题呢？

首先我们看下它的官网介绍：Spring Security 官网地址

Spring Security is a powerful and highly customizable authentication and access-control framework. It is the de-facto standard for securing Spring-based applications.

Spring Security is a framework that focuses on providing both authentication and authorization to Java applications. Like all Spring projects, the real power of Spring Security is found in how easily it can be extended to meet custom requirements

Spring Security 是一个功能强大且高度可定制的身份验证和访问控制框架。它实际上是保护基于 spring 的应用程序的标准。

Spring Security 是一个框架，侧重于为 Java 应用程序提供身份验证和授权。与所有 Spring 项目一样，Spring 安全性的真正强大之处在于它可以轻松地扩展以满足定制需求

从官网的介绍中可以知道这是一个权限框架。想我们之前做项目是没有使用框架是怎么控制权限的？对于权限 一般会细分为功能权限，访问权限，和菜单权限。代码会写的非常的繁琐，冗余。

怎么解决之前写权限代码繁琐，冗余的问题，一些主流框架就应运而生而 Spring Scecurity 就是其中的一种。

Spring 是一个非常流行和成功的 Java 应用开发框架。Spring Security 基于 Spring 框架，提供了一套 Web 应用安全性的完整解决方案。一般来说，Web 应用的安全性包括用户认证（Authentication）和用户授权（Authorization）两个部分。用户认证指的是验证某个用户是否为系统中的合法主体，也就是说用户能否访问该系统。用户认证一般要求用户提供用户名和密码。系统通过校验用户名和密码来完成认证过程。用户授权指的是验证某个用户是否有权限执行某个操作。在一个系统中，不同用户所具有的权限是不同的。比如对一个文件来说，有的用户只能进行读取，而有的用户可以进行修改。一般来说，系统会为不同的用户分配不同的角色，而每个角色则对应一系列的权限。

对于上面提到的两种应用情景，Spring Security 框架都有很好的支持。在用户认证方面，Spring Security 框架支持主流的认证方式，包括 HTTP 基本认证、HTTP 表单验证、HTTP 摘要认证、OpenID 和 LDAP 等。在用户授权方面，Spring Security 提供了基于角色的访问控制和访问控制列表（Access Control List，ACL），可以对应用中的领域对象进行细粒度的控制。

### 18.2、实战测试

#### 18.2.1、实验环境搭建

1、新建一个初始的 springboot 项目 web 模块，thymeleaf 模块

2、导入静态资源

```
welcome.html
|views
|level1
1.html
2.html
3.html
|level2
1.html
2.html
3.html
|level3
1.html
2.html
3.html
Login.html
```

3、controller 跳转！

```
package com.kuang.controller;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
public class RouterController {

   @RequestMapping({"/","/index"})
   public String index(){
       return "index";
  }

   @RequestMapping("/toLogin")
   public String toLogin(){
       return "views/login";
  }

   @RequestMapping("/level1/{id}")
   public String level1(@PathVariable("id") int id){
       return "views/level1/"+id;
  }

   @RequestMapping("/level2/{id}")
   public String level2(@PathVariable("id") int id){
       return "views/level2/"+id;
  }

   @RequestMapping("/level3/{id}")
   public String level3(@PathVariable("id") int id){
       return "views/level3/"+id;
  }

}
```

4、测试实验环境是否 OK！

#### 18.2.2、认识 SpringSecurity

Spring Security 是针对 Spring 项目的安全框架，也是 Spring Boot 底层安全模块默认的技术选型，他可以实现强大的 Web 安全控制，对于安全控制，我们仅需要引入 spring-boot-starter-security 模块，进行少量的配置，即可实现强大的安全管理！

记住几个类：

*   WebSecurityConfigurerAdapter：自定义 Security 策略
*   AuthenticationManagerBuilder：自定义认证策略
*   @EnableWebSecurity：开启 WebSecurity 模式

Spring Security 的两个主要目标是 “认证” 和 “授权”（访问控制）。

**“认证”（Authentication）**

身份验证是关于验证您的凭据，如用户名 / 用户 ID 和密码，以验证您的身份。

身份验证通常通过用户名和密码完成，有时与身份验证因素结合使用。

**“授权” （Authorization）**

授权发生在系统成功验证您的身份后，最终会授予您访问资源（如信息，文件，数据库，资金，位置，几乎任何内容）的完全权限。

这个概念是通用的，而不是只在 Spring Security 中存在。

#### 18.2.3、认证和授权

目前，我们的测试环境，是谁都可以访问的，我们使用 Spring Security 增加上认证和授权的功能

1、引入 Spring Security 模块

```
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

2、编写 Spring Security 配置类

参考官网：https://spring.io/projects/spring-security

查看我们自己项目中的版本，找到对应的帮助文档：

https://docs.spring.io/spring-security/site/docs/5.3.0.RELEASE/reference/html5 #servlet-applications 8.16.4

![](https://img-blog.csdnimg.cn/img_convert/408a48afe020e5de4eed7b79d01c5970.png)

3、编写基础配置类

```
package com.kuang.config;

import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;

@EnableWebSecurity // 开启WebSecurity模式
public class SecurityConfig extends WebSecurityConfigurerAdapter {

   @Override
   protected void configure(HttpSecurity http) throws Exception {
       
  }
}
```

4、定制请求的授权规则

```
@Override
protected void configure(HttpSecurity http) throws Exception {
   // 定制请求的授权规则
   // 首页所有人可以访问
   http.authorizeRequests().antMatchers("/").permitAll()
  .antMatchers("/level1/**").hasRole("vip1")
  .antMatchers("/level2/**").hasRole("vip2")
  .antMatchers("/level3/**").hasRole("vip3");
}
```

5、测试一下：发现除了首页都进不去了！因为我们目前没有登录的角色，因为请求需要登录的角色拥有对应的权限才可以！

6、在 configure() 方法中加入以下配置，开启自动配置的登录功能！

```
// 开启自动配置的登录功能
// /login 请求来到登录页
// /login?error 重定向到这里表示登录失败
http.formLogin();
```

7、测试一下：发现，没有权限的时候，会跳转到登录的页面！

![](https://img-blog.csdnimg.cn/img_convert/eaf88d568106ce6b46869427a35de839.png)

8、查看刚才登录页的注释信息；

我们可以定义认证规则，重写 configure(AuthenticationManagerBuilder auth) 方法

```
//定义认证规则
@Override
protected void configure(AuthenticationManagerBuilder auth) throws Exception {
   
   //在内存中定义，也可以在jdbc中去拿....
   auth.inMemoryAuthentication()
          .withUser("kuangshen").password("123456").roles("vip2","vip3")
          .and()
          .withUser("root").password("123456").roles("vip1","vip2","vip3")
          .and()
          .withUser("guest").password("123456").roles("vip1","vip2");
}
```

9、测试，我们可以使用这些账号登录进行测试！发现会报错！

There is no PasswordEncoder mapped for the id “null”

![](https://img-blog.csdnimg.cn/img_convert/370af0af88d94173b6ed5bc6d62ca70f.png)

10、原因，我们要将前端传过来的密码进行某种方式加密，否则就无法登录，修改代码

```
//定义认证规则
@Override
protected void configure(AuthenticationManagerBuilder auth) throws Exception {
   //在内存中定义，也可以在jdbc中去拿....
   //Spring security 5.0中新增了多种加密方式，也改变了密码的格式。
   //要想我们的项目还能够正常登陆，需要修改一下configure中的代码。我们要将前端传过来的密码进行某种方式加密
   //spring security 官方推荐的是使用bcrypt加密方式。
   
   auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
          .withUser("kuangshen").password(new BCryptPasswordEncoder().encode("123456")).roles("vip2","vip3")
          .and()
          .withUser("root").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2","vip3")
          .and()
          .withUser("guest").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2");
}
```

11、测试，发现，登录成功，并且每个角色只能访问自己认证下的规则！搞定

#### 18.2.4、权限控制和注销

1、开启自动配置的注销的功能

```
//定制请求的授权规则
@Override
protected void configure(HttpSecurity http) throws Exception {
   //....
   //开启自动配置的注销的功能
      // /logout 注销请求
   http.logout();
}
```

2、我们在前端，增加一个注销的按钮，index.html 导航栏中

```
<a class="item" th:href="@{/logout}">
   <i class="address card icon"></i> 注销
</a>
```

3、我们可以去测试一下，登录成功后点击注销，发现注销完毕会跳转到登录页面！

4、但是，我们想让他注销成功后，依旧可以跳转到首页，该怎么处理呢？

```
// .logoutSuccessUrl("/"); 注销成功来到首页
http.logout().logoutSuccessUrl("/");
```

5、测试，注销完毕后，发现跳转到首页 OK

6、我们现在又来一个需求：用户没有登录的时候，导航栏上只显示登录按钮，用户登录之后，导航栏可以显示登录的用户信息及注销按钮！还有就是，比如 kuangshen 这个用户，它只有 vip2，vip3 功能，那么登录则只显示这两个功能，而 vip1 的功能菜单不显示！这个就是真实的网站情况了！该如何做呢？

**我们需要结合 thymeleaf 中的一些功能**

sec：authorize=“isAuthenticated()”: 是否认证登录！来显示不同的页面

Maven 依赖：

```
<!-- https://mvnrepository.com/artifact/org.thymeleaf.extras/thymeleaf-extras-springsecurity4 -->
<dependency>
   <groupId>org.thymeleaf.extras</groupId>
   <artifactId>thymeleaf-extras-springsecurity5</artifactId>
   <version>3.0.4.RELEASE</version>
</dependency>
```

7、修改我们的 前端页面

1.  导入命名空间
    
2.  ```
    xmlns:sec="http://www.thymeleaf.org/thymeleaf-extras-springsecurity5"
    ```
    
3.  修改导航栏，增加认证判断
    
4.  ```
    <!--登录注销-->
    <div class="right menu">
    
       <!--如果未登录-->
       <div sec:authorize="!isAuthenticated()">
           <a class="item" th:href="@{/login}">
               <i class="address card icon"></i> 登录
           </a>
       </div>
    
       <!--如果已登录-->
       <div sec:authorize="isAuthenticated()">
           <a class="item">
               <i class="address card icon"></i>
              用户名：<span sec:authentication="principal.username"></span>
              角色：<span sec:authentication="principal.authorities"></span>
           </a>
       </div>
    
       <div sec:authorize="isAuthenticated()">
           <a class="item" th:href="@{/logout}">
               <i class="address card icon"></i> 注销
           </a>
       </div>
    </div>
    ```
    

8、重启测试，我们可以登录试试看，登录成功后确实，显示了我们想要的页面；

9、如果注销 404 了，就是因为它默认防止 csrf 跨站请求伪造，因为会产生安全问题，我们可以将请求改为 post 表单提交，或者在 spring security 中关闭 csrf 功能；我们试试：在 配置中增加 `http.csrf().disable();`

```
http.csrf().disable();//关闭csrf功能:跨站请求伪造,默认只能通过post方式提交logout请求
http.logout().logoutSuccessUrl("/");
```

10、我们继续将下面的角色功能块认证完成！

```
<!-- sec:authorize="hasRole('vip1')" -->
<div class="column" sec:authorize="hasRole('vip1')">
   <div class="ui raised segment">
       <div class="ui">
           <div class="content">
               <h5 class="content">Level 1</h5>
               <hr>
               <div><a th:href="@{/level1/1}"><i class="bullhorn icon"></i> Level-1-1</a></div>
               <div><a th:href="@{/level1/2}"><i class="bullhorn icon"></i> Level-1-2</a></div>
               <div><a th:href="@{/level1/3}"><i class="bullhorn icon"></i> Level-1-3</a></div>
           </div>
       </div>
   </div>
</div>

<div class="column" sec:authorize="hasRole('vip2')">
   <div class="ui raised segment">
       <div class="ui">
           <div class="content">
               <h5 class="content">Level 2</h5>
               <hr>
               <div><a th:href="@{/level2/1}"><i class="bullhorn icon"></i> Level-2-1</a></div>
               <div><a th:href="@{/level2/2}"><i class="bullhorn icon"></i> Level-2-2</a></div>
               <div><a th:href="@{/level2/3}"><i class="bullhorn icon"></i> Level-2-3</a></div>
           </div>
       </div>
   </div>
</div>

<div class="column" sec:authorize="hasRole('vip3')">
   <div class="ui raised segment">
       <div class="ui">
           <div class="content">
               <h5 class="content">Level 3</h5>
               <hr>
               <div><a th:href="@{/level3/1}"><i class="bullhorn icon"></i> Level-3-1</a></div>
               <div><a th:href="@{/level3/2}"><i class="bullhorn icon"></i> Level-3-2</a></div>
               <div><a th:href="@{/level3/3}"><i class="bullhorn icon"></i> Level-3-3</a></div>
           </div>
       </div>
   </div>
</div>
```

11、测试一下！

12、权限控制和注销搞定！

#### 18.2.5、记住我

现在的情况，我们只要登录之后，关闭浏览器，再登录，就会让我们重新登录，但是很多网站的情况，就是有一个记住密码的功能，这个该如何实现呢？很简单

1、开启记住我功能

```
//定制请求的授权规则
@Override
protected void configure(HttpSecurity http) throws Exception {
//。。。。。。。。。。。
   //记住我
   http.rememberMe();
}
```

2、我们再次启动项目测试一下，发现登录页多了一个记住我功能，我们登录之后关闭 浏览器，然后重新打开浏览器访问，发现用户依旧存在！

思考：如何实现的呢？其实非常简单

我们可以查看浏览器的 cookie

![](https://img-blog.csdnimg.cn/img_convert/e9b5578efb77d9ec466eeca9613882ed.png)

3、我们点击注销的时候，可以发现，spring security 帮我们自动删除了这个 cookie

![](https://img-blog.csdnimg.cn/img_convert/8bc4b63bae73a0bebe9b70a632b0cc6f.png)  
4、结论：登录成功后，将 cookie 发送给浏览器保存，以后登录带上这个 cookie，只要通过检查就可以免登录了。如果点击注销，则会删除这个 cookie，具体的原理我们在 JavaWeb 阶段都讲过了，这里就不在多说了！

#### 18.2.6、定制登录页

现在这个登录页面都是 spring security 默认的，怎么样可以使用我们自己写的 Login 界面呢？

1、在刚才的登录页配置后面指定 loginpage

```
http.formLogin().loginPage("/toLogin");
```

2、然后前端也需要指向我们自己定义的 login 请求

```
<a class="item" th:href="@{/toLogin}">
   <i class="address card icon"></i> 登录
</a>
```

3、我们登录，需要将这些信息发送到哪里，我们也需要配置，login.html 配置提交请求及方式，方式必须为 post:

在 loginPage() 源码中的注释上有写明：

![](https://img-blog.csdnimg.cn/img_convert/3f0a7ac45b3ef4ef40bb2725f17b38bf.png)

```
<form th:action="@{/login}" method="post">
   <div class="field">
       <label>Username</label>
       <div class="ui left icon input">
           <input type="text" placeholder="Username" >
           <i class="user icon"></i>
       </div>
   </div>
   <div class="field">
       <label>Password</label>
       <div class="ui left icon input">
           <input type="password" >
           <i class="lock icon"></i>
       </div>
   </div>
   <input type="submit" class="ui blue submit button"/>
</form>
```

4、这个请求提交上来，我们还需要验证处理，怎么做呢？我们可以查看 formLogin() 方法的源码！我们配置接收登录的用户名和密码的参数！

```
http.formLogin()
  .usernameParameter("username")
  .passwordParameter("password")
  .loginPage("/toLogin")
  .loginProcessingUrl("/login"); // 登陆表单提交请求
```

5、在登录页增加记住我的多选框

```
<input type="checkbox" > 记住我
```

6、后端验证处理！

```
//定制记住我的参数！
http.rememberMe().rememberMeParameter("remember");
```

7、测试，OK

### 18.3、完整配置代码

```
package com.kuang.config;

import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.builders.HttpSecurity;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;
import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;

@EnableWebSecurity
public class SecurityConfig extends WebSecurityConfigurerAdapter {

   //定制请求的授权规则
   @Override
   protected void configure(HttpSecurity http) throws Exception {

       http.authorizeRequests().antMatchers("/").permitAll()
      .antMatchers("/level1/**").hasRole("vip1")
      .antMatchers("/level2/**").hasRole("vip2")
      .antMatchers("/level3/**").hasRole("vip3");


       //开启自动配置的登录功能：如果没有权限，就会跳转到登录页面！
           // /login 请求来到登录页
           // /login?error 重定向到这里表示登录失败
       http.formLogin()
          .usernameParameter("username")
          .passwordParameter("password")
          .loginPage("/toLogin")
          .loginProcessingUrl("/login"); // 登陆表单提交请求

       //开启自动配置的注销的功能
           // /logout 注销请求
           // .logoutSuccessUrl("/"); 注销成功来到首页

       http.csrf().disable();//关闭csrf功能:跨站请求伪造,默认只能通过post方式提交logout请求
       http.logout().logoutSuccessUrl("/");

       //记住我
       http.rememberMe().rememberMeParameter("remember");
  }

   //定义认证规则
   @Override
   protected void configure(AuthenticationManagerBuilder auth) throws Exception {
       //在内存中定义，也可以在jdbc中去拿....
       //Spring security 5.0中新增了多种加密方式，也改变了密码的格式。
       //要想我们的项目还能够正常登陆，需要修改一下configure中的代码。我们要将前端传过来的密码进行某种方式加密
       //spring security 官方推荐的是使用bcrypt加密方式。

       auth.inMemoryAuthentication().passwordEncoder(new BCryptPasswordEncoder())
              .withUser("kuangshen").password(new BCryptPasswordEncoder().encode("123456")).roles("vip2","vip3")
              .and()
              .withUser("root").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2","vip3")
              .and()
              .withUser("guest").password(new BCryptPasswordEncoder().encode("123456")).roles("vip1","vip2");
  }
}
```

附上小狂神的赞赏码：  
![](https://img-blog.csdnimg.cn/2e55de8ea0914167b1574be84094f398.png)