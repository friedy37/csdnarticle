> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_46563201/article/details/112006876?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522171790764416800185844262%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=171790764416800185844262&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-112006876-null-null.142^v100^pc_search_result_base5&utm_term=java%E5%AD%A6%E4%B9%A0%E7%AC%94%E8%AE%B0&spm=1018.2226.3001.4187)

#### 文章目录

*   [前言](#_1)
*   [java 语言特性](#java_6)
*   [java 的编译与运行](#java_13)
*   [JDK、JRE、JVM](#JDKJREJVM_15)
*   [字符编码](#_24)
*   [数据类型](#_33)
*   *   [数据类型取值范围](#_44)
    *   [数据类型默认转换](#_47)
*   [标识符命名方法](#_58)
*   [数组](#_66)
*   *   [一维数组](#_67)
    *   [二维数组](#_92)
    *   [数组排序算法](#_109)
    *   [数组查找算法](#_117)
    *   [数组工具类（Arrays）](#Arrays_121)
*   [逻辑运算符](#_140)
*   [输入操作](#_148)
*   [Java 中的命名规则](#Java_185)
*   *   [有符号数据表示法](#_195)
*   [面向对象与面向过程](#_203)
*   [包](#_233)
*   [类](#_246)
*   *   [类的描述](#_247)
    *   [类的导入](#_257)
    *   [自定义类的使用](#_265)
    *   [类的初始化过程](#_284)
    *   [类的设计技巧](#_304)
    *   [类的加载](#_314)
    *   [类的加载时机](#_328)
    *   [类加载器](#_339)
*   [对象](#_345)
*   *   [匿名对象](#_349)
*   [方法](#_365)
*   *   [方法概述](#_366)
    *   [Java 中值传递和引用传递](#Java_401)
    *   [方法的内存分配与变化](#_409)
    *   [方法重载](#_420)
    *   [方法重写](#_425)
    *   [main 方法的格式讲解](#main_432)
*   [构造器](#_447)
*   [变量](#_476)
*   *   [Java 中的变量类型](#Java_477)
    *   [成员变量与局部变量](#_479)
*   [访问控制权限修饰符](#_489)
*   [封装](#_508)
*   *   [this 关键字](#this_515)
*   [static 关键字](#static_521)
*   [final 关键字](#final_535)
*   [代码块](#_550)
*   [继承](#_564)
*   *   [super 关键字](#super_596)
    *   [继承中构造方法的关系](#_623)
    *   [继承使用场景](#_628)
    *   [继承的设计技巧](#_631)
*   [多态](#_635)
*   *   [多态中的成员访问特点](#_672)
*   [抽象类](#_680)
*   [接口](#_701)
*   [简单修饰符归纳](#_745)
*   [内部类](#_753)
*   *   [成员内部类](#_764)
    *   [局部内部类](#_778)
    *   [匿名内部类](#_785)
    *   [静态内部类](#_799)
    *   [JVM 的类加载规则](#JVM_813)
*   [Java 中的 String](#JavaString_822)
*   *   [Java 中的 StringBuffer 和 StringBuilder](#JavaStringBufferStringBuilder_835)
*   [增强 for](#for_920)
*   [包装类](#_938)
*   [Math 类](#Math_994)
*   [Random 类](#Random_1024)
*   [System 类（系统类）](#System_1046)
*   [BigInteger 类](#BigInteger_1070)
*   [BigDecimal 类](#BigDecimal_1098)
*   [Date 类](#Date_1131)
*   [DateFormat 类](#DateFormat_1152)
*   [Calendar 类](#Calendar_1172)
*   [集合](#_1194)
*   *   [Collection](#Collection_1205)
    *   [迭代器](#_1241)
    *   [List](#List_1282)
    *   [LinkedList](#LinkedList_1314)
    *   [Map](#Map_1332)
    *   [哈希表的数据结构](#_1378)
    *   [TreeSet](#TreeSet_1388)
    *   [Collections](#Collections_1413)
*   [泛型](#_1447)
*   *   [泛型通配符](#_1462)
*   [静态导入](#_1482)
*   [可变参数](#_1498)
*   [枚举](#_1516)
*   [异常](#_1533)
*   *   [异常继承体系图](#_1535)
    *   [** 处理异常的两种方式 **](#_1544)
    *   [自定义异常](#_1634)
    *   [final、finally、finalize](#finalfinallyfinalize_1654)
    *   [异常注意事项](#_1660)
*   [IO 流](#IO_1666)
*   *   [IO 流的释义](#IO_1667)
    *   [IO 流的分类](#IO_1669)
    *   [文件专属流](#_1691)
    *   [转换流](#_1775)
    *   [缓冲流](#_1791)
    *   [数据流](#_1806)
    *   [标准输出流](#_1810)
    *   [序列化与反序列化](#_1831)
    *   [File 类](#File_1952)
*   [多线程](#_2049)
*   *   [名词释义](#_2050)
    *   [多线程实现](#_2069)
    *   [线程的生命周期](#_2208)
    *   [线程的优先级](#_2360)
    *   [线程的调度模型](#_2375)
    *   [线程安全](#_2381)
    *   [守护线程](#_2633)
    *   [定时器](#_2650)
    *   [Object 中的 wait 方法和 notify 方法](#Objectwaitnotify_2690)
    *   [获取文件绝对路径](#_2721)
*   [资源绑定器](#_2739)
*   [反射](#_2748)
*   *   [反射的优点](#_2845)
    *   [反射的缺点](#_2852)
*   [注解](#_2861)
*   [面向对象思想设计原则](#_2961)
*   [设计模式](#_2973)
*   [Java 小知识](#Java_2985)
*   [Eclipse 中常用的快捷键](#Eclipse_3084)
*   [结语](#_3144)

前言
--

**个人博客网站：[XLFBlog](http://blog.huiyuanai.cloud/index)（http://blog.huiyuanai.cloud/index），欢迎大家交流学习哦~**

以下是一名 java 初学者在自学过程中所整理的笔记，欢迎大家浏览并留言，若有错误的地方请大家指正。

java 语言特性
---------

*   **简单性**：相对于其他编程语言而言，java 较为简单，例如：java 不再支持多继承，C++ 是支持多继承的，多继承比较复杂，C++ 中有指针，java 中屏蔽了指针的概念，避免了绝大部分的指针越界和内存泄露的问题，这里说明一下，java 语言低层是用 C++ 实现的，并不是 C 语言。
*   **面向对象**：java 是纯面向对象的，更符合人的思维模式，易于理解。
*   **健壮性**：java 的健壮性与自动垃圾回收机制有关，自动垃圾回收机制简称 GC 机制，java 语言运行过程中产生的垃圾是自动回收的，不需要程序员关心。
*   **可移植性**：java 程序可以做到一次编译，到处运行。在 Windows 操作系统上运行的 java 程序，不做任何修改，可以直接放到 Linux 操作系统上运行，这个被称为 java 程序的可移植性（跨平台）。java 的跨平台性是通过 JVM（java 虚拟机）实现的，java 代码不直接与底层操作系统打交道，而是通过 JVM 这个中间介质间接与底层操作系统交互，JVM 屏蔽了各操作系统之间的差异，不同版本的操作系统就有不同版本的 JVM，只有在 JVM 这个环境下的 java 程序才能运行。
*   **多线程**

java 的编译与运行
-----------

![](https://img-blog.csdnimg.cn/20201231155839274.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

JDK、JRE、JVM
-----------

*   **JDK**：java 开发工具包
*   **JRE**：java 运行时环境
*   **JVM**：java 虚拟机  
    说明：  
    1、JDK 和 JRE 都可以单独安装，若不需要开发 Java 程序，只需要运行的话，那么，只用安装 JRE 即可。  
    2、JVM 不能单独安装。  
    以下为三者关系图：  
    ![](https://img-blog.csdnimg.cn/20201231160651167.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

字符编码
----

_为了让计算机可以表示现实世界中的文字，需要人提前制定好 “文字” 和“二进制”之间的对照关系，这种对照转换关系被称为“字符编码”。_

*   **ASCII 码**：采用一个字节编码，主要针对英文编码
*   **GBK**：主要是简体汉字编码
*   **Unicode**: 统一了全世界的所有文字编码，采用这三种方式实现（UTF-8、UTF-16、UTF-32）  
    说明：  
    1、Java 采用 Unicode 编码方式  
    2、在实际开发中，一般使用 UTF-8 编码方式实现

数据类型
----

*   Java 程序中最基本的单位是类
*   Java 中变量赋值时必须类型对应，否则不兼容，编译不过，可用强转
*   Java 中局部变量不赋值不能使用

![](https://img-blog.csdnimg.cn/20201231163659829.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)  
说明：整数默认为 int，浮点数默认为 double，布尔类型默认为 false

### 数据类型取值范围

![](https://img-blog.csdnimg.cn/20210103204119123.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

### 数据类型默认转换

```
byte、short、char-->int-->long-->float-->double
```

**注**：为什么 long 比 float 所占字节长度更大却是 long 转换为 float 呢？  
_因为它们底层的存储结构不同，float 表示的数据范围要比 long 的范围更大。_

标识符命名方法
-------

*   **小驼峰命名法**：标识符是由一个单词组成时首字母小写，多个单词组成时第一个单词首字母小写，其余单词首字母大写。
*   **大驼峰命名法**：标识符是由一个单词组成时首字母大写，多个单词组成时每一个单词首字母大写。  
    _说明：小驼峰命名法用于方法、变量的命名，大驼峰命名法用于类的命名。_

数组
--

### [一维数组](https://so.csdn.net/so/search?q=%E4%B8%80%E7%BB%B4%E6%95%B0%E7%BB%84&spm=1001.2101.3001.7020)

格式如下：

```
/*动态初始化*/
数组类型[] 数组名 = new 数组类型[元素个数（数组长度）];

/*静态初始化*/
数组类型[] 数组名 = {元素1, 元素2, 元素3, .....} = new 数组类型[]{元素1, 元素2, 元素3, .....};
```

举例：

```
String[] array1 = {"abc", "a", "ad"};//字符串数组中不能有字符（''）
char[] array2 = {'A', 'b'};//字符数组中不能有字符串（""）
int[] array3 = {23, 12, 90};
```

说明：以上例子中可以把 “[]” 放在数组名后面（array1[]）, 但是 Java 中不建议这样，放在数组名前面更易于理解。

*   用 “数组名. length” 的方式来获得数组长度
*   字符数组默认初始值为一个空字符（“\u000”）
*   boolean 数组默认初始值为 false，其余数组默认值为 0
*   Java 中的数组必须先初始化（赋值后）才能使用

### [二维数组](https://so.csdn.net/so/search?q=%E4%BA%8C%E7%BB%B4%E6%95%B0%E7%BB%84&spm=1001.2101.3001.7020)

格式如下：

```
/*动态初始化*/
写法一：数据类型[][] 数组名 = new 数据类型[m][n];//m表示这个二维数组有m个一维数组， n表示每一个一维数组有n个元素
写法二：数据类型 数组名[][] = new 数据类型[m][n];
写法三：数据类型[] 数组名[] = new 数据类型[m][n];
数据类型[][] 数组名 = new 数据类型[m][];//如果没有给出每个一维数组的元素个数，就表示这个二维数组是变化的，但不能没有一维数组的个数

/*静态初始化*/
数据类型[][] 数组名 = {{元素...}, {元素...}, {元素...}......} = new 数据类型[][] {{元素...}, {元素...}, {元素...}......};

/*注明*/
int[] x, y[];//x是一维数组，y是二维数组
```

### 数组排序算法

*   **选择排序**：把 0 索引的元素和 1 索引后的元素进行比较  
    ![](https://img-blog.csdnimg.cn/20210111132327109.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)
*   **冒泡排序**：相邻元素比较  
    ![](https://img-blog.csdnimg.cn/20210111132548725.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

### 数组查找算法

*   **二分查找（折半查找）**：针对数组有序的情况，切记不要将已给出的数组先排序后再查找  
    ![](https://img-blog.csdnimg.cn/20210111133839873.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

### 数组工具类（Arrays）

*   数组转字符串功能

```
public static String toString(int[] array);
```

*   快速排序功能

```
public static void sort(int[] array);
```

*   二分查找功能

```
public static int binarySearch(int[] array, int key);
```

[逻辑运算符](https://so.csdn.net/so/search?q=%E9%80%BB%E8%BE%91%E8%BF%90%E7%AE%97%E7%AC%A6&spm=1001.2101.3001.7020)
--------------------------------------------------------------------------------------------------------------

![](https://img-blog.csdnimg.cn/20201231201209167.png)

1.  **短路运算符**：“&&” 、 “||”
2.  **非短路运算符**：“&” 、 "|"
3.  **短路运算符与非短路运算符的区别**：短路运算符两边表达式有可能只执行一边的表达式，效率较高，最常用；非短路运算符两边表达式无论什么情况都会执行。
4.  最最常用的逻辑运算符：“&&” 、 “||” 、 "!"

输入操作
----

步骤如下：

1.  **导包**（必须放在类 class 与包名 package 的中间）

```
import java.util.Scanner;
```

2.  **创建 Scanner 对象**

```
Scanner input = new Scanner(System.in);
```

3.  接收数据

```
int n = input.nextInt();
```

**注：**

```
整型:input.nextInt();
单精度浮点型:input.nextFloat();
双精度浮点型:input.nextDouble();
字符串类型:input.nextLine();//这种写法可以得到带空格的字符串
		  input.next();//此写法在读取内容时会过滤掉有效字符前面的无效字符，所以这种写法不能得到带空格的字符串
短整型:input.nextShort();
字节型:input.nextByte();
字符型:input.next().charAt(i);//i是指从用户输入的字符串中选取第i个单个字符输入到内存中，i从0开始
```

Java 中的命名规则
-----------

*   **包**：实质上是文件夹，用于保证类名的唯一性（区分相同类名）。为了保证包名的唯一性，一般采用公司域名以逆序的形式作为包名，然后对于不同的工程使用不同的子包（域名. 项目名. 模块名）例：com.horstmann.corejava，且包名全部小写
*   **类或接口**：大驼峰命名法
*   **方法或变量**：小驼峰命名法
*   **常量**: 一个单词组成时全部大写，多个单词组成时每个单词大写且单词间用_隔开
*   **二进制数**：以 0b 开头
*   **八进制数**：以 0 开头
*   **十六进制数**：以 0x 开头

### 有符号数据表示法

_在计算机内，有符号数据有三种表示法：原码、反码、补码，**所有数据的运算都是采用补码进行的**_

*   **原码**：二进制定点表示法，即最高位为符号位，“0” 表示正，“1” 表示负，其余位数表示数值大小
*   **反码**：正数的反码与其原码相同，负数的反码是对其原码逐位取反，但符号位除外
*   **补码**：正数的补码与其原码相同，负数的补码是在其反码的末位加 1

面向对象与面向过程
---------

**面向过程**：主要关注实现的具体过程，语句之间是因果关系

*   优点：对于业务逻辑比较简单的程序，可以达到快速开发，前期投入成本较低
*   缺点：采用面向过程的方式开发很难解决非常复杂的业务逻辑，另外面向过程的方式导致软件元素之间的耦合度非常高，只要其中一环出现问题整个系统都将受到影响，导致最终的软件扩展力差，由于没有对象的概念，所以无法达到组件复用

_面向过程程序设计也称作结构化程序设计或结构化编程，它是分析出解决问题所需要的步骤，然后用函数把这些步骤一步一步实现，使用时一个一个依次调用即可。_

**面向对象**：它是基于面向过程的编程思想，也是一种思考问题的方式，主要关注对象能完成哪些功能, 这种思维方法其实就是我们在现实生活中习惯的思维方式，是从人类考虑问题的角度出发，把人类解决问题的思维方式逐步翻译成程序能够理解的思维方式的过程。

_面向对象是把构成问题的事物分解成各个对象，建立对象的目的不是为了完成一个步骤，而是为了描述某个事物在整个解决问题的步骤中的行为_

*   优点：一种更符合我们思想习惯的思想，将我们从执行者变成指挥者，从而达到将复杂问题简单化的目的。耦合度低，扩展力强，更容易解决现实世界中复杂的业务逻辑，组件复用性强
*   缺点：前期投入成本高，需要进行对象的抽取，大量的系统分析与设计
*   如何建立面向对象思维呢？1、首先分析有哪些类；2、分析每个类应该有什么；3、最后分析类与类之间的关系
*   面向对象开发就是不断的创建对象、使用对象、指挥对象做事情
*   面向对象设计就是在管理和维护对象之间的关系
*   **所有面向对象的编程语言都具有的三大特征：封装、继承、多态**

**注**：采用面向对象的方式开发一个软件的生命周期

1.  面向对象的分析（OOA）
2.  面向对象的设计（OOD）
3.  面向对象的编程（OOP）

包
-

*   包的定义：包其实就是文件夹
*   包的作用：1、把相同的类名放到不同包中；2、对类进行分类管理（分类方案：1、按照功能分，如增删改查；2、按照模块分，如老师、学生，每个模块中有对应的功能）
*   package 语句必须是程序的第一条可执行的代码，注释除外
*   package 语句在一个 java 文件中只能有一个
*   如果没有 package，默认无包名（default）
*   拥有包访问权限的类才能访问某个包中的类
*   同一个包中不允许有相同名字的类，不同包中类的名字可以相同，当同时调用两个不同包中的相同类名的类时，应当加上包名加以区分

类
-

### 类的描述

对一个事物的描述：

1.  属性：该事物的描述信息
2.  行为：该事物能够做什么  
    ![](https://img-blog.csdnimg.cn/20210104211148596.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)
3.  _类是一组相关的属性和行为的集合，是构造对象的模板和蓝图，是一个抽象的概念_
4.  由类构造对象的过程称为类的实例化

### 类的导入

一个类可以使用所属包中的所有类，以及其他包中的公共类，有两种方式访问另一个包中的公共类：

1.  使用完全限定名（包名后面跟着类名）如：java.time.LocalDate
2.  使用 import 语句

### 自定义类的使用

*   创建对象的格式：

```
类名 对象名 = new 类名();
```

*   使用成员变量的格式：

```
对象名.变量名
```

*   使用成员方法的格式：

```
对象名.方法名(参数...)
```

### 类的初始化过程

以下代码在内存中做了哪些事情？

```
Student s = new Student();
```

分五步：

1.  加载 Student.class 文件进内存
2.  在栈内存中为引用变量 s 开辟空间
3.  在堆内存中为学生对象开辟空间
4.  对学生对象的成员变量进行默认初始化
5.  对学生对象的成员变量进行显示初始化

对上述语句的解析：

*   右边的 “new Student()” 是以 Student 类为模板，在堆空间里创建一个 Student 对象
*   末尾的 “（）” 意味着在对象创建后立即用 Student 类的构造方法对刚生成的对象进行初始化
*   左边的 “Student s” 创建了一个 Student 类引用变量，它存在于栈空间中，也就是用来指向 Student 对象的对象引用
*   “=” 操作符使对象引用指向刚创建的那个 Student 对象

### 类的设计技巧

1.  一定要保证数据私有化
2.  一定要对数据进行初始化
3.  不要在类中使用过多的基本类型
4.  不是所有的字段都需要单独的字段访问器和字段更改器
5.  分解有过多职责的类
6.  类名和方法名的命名要起到见名知意的效果（类名应当是一个名词或动名词，访问器方法用小写 get 开头，更改器方法用小写 set 开头）

### 类的加载

_当程序要使用某个类时，如果该类还未被加载到内存中，则系统会通过加载、连接、初始化三步来实现对这个类进行的加载_

**加载**：将. class 文件读入内存，并为之创建一个 class 对象，任何类被使用时系统都会建立一个 class 对象

**连接**：

1.  验证：是否有正确的内部结构，并和其他类协调一致
2.  准备：负责为类的静态成员分配内存，并设置默认初始值
3.  解析：将类的二进制数据中的符号引用替换为直接引用

### 类的加载时机

什么时候类会加载？

*   创建类的实例
*   访问类的静态变量，或者为静态变量赋值
*   调用类的静态方法
*   使用反射方式来强制创建某个类或接口对应的 java.lang.class 对象
*   初始化某个类的子类
*   直接使用 java.exe 命令来运行某个主类

### 类加载器

*   根类加载器（Bootstrap ClassLoader）：也叫引导类加载器，负责 Java 核心类的加载，比如 System、String 等，在 JDK 中 JRE 的 lib 目录下的 rt.jar 文件中
*   扩展类加载器（Extension ClassLoader）：负责 JRE 的扩展目录中 jar 包的加载，在 JDK 中 JRE 的 lib 目录下的 ext 目录中
*   系统类加载器（System ClassLoader）：负责在 JVM 启动时加载来自 Java 命令的 class 文件，以及 classpath 环境变量所指定的 jar 包和类路径（我们自定义的类就是通过它加载的）

对象
--

*   **对象是该类事物的具体表现形式，具体存在的个体**，如：学生是一个类，那么，班长就是一个对象

### 匿名对象

_匿名对象是指没有名字的对象，只创建对象但是不用变量来接收_

```
//匿名对象举例
new student();
new student().show();
```

**匿名对象的应用场景**：

1.  该方法仅调用一次的时候
2.  匿名对象可以作为实际参数传递

**匿名对象的优点**：匿名对象创建的方式能够减少栈帧的分配和指向，且在调用完毕后能够被 GC 机制（垃圾回收机制）快速的回收

方法
--

### 方法概述

*   方法是完成特定功能的代码块，Java 中的方法就是 C 语言中的函数
*   在 Java 中，所有的方法都必须在类的内部定义
*   如下代码中，像这里的 e 出现在方法名前面的叫隐式参数，可以用 this 指示；像这里的 5 出现在方法名后面括号中的数值叫显式参数

```
Employee e = new Employee("xl"...);
e.raiseSalary(5);
```

*   如果方法需要返回一个可变对象的引用，首先应该对它进行克隆（clone，指存放在另一个新位置上的对象副本）再返回，而不是直接返回可变对象本身

```
class Employee
{
	...
	public Date getHireDay()
	{
		return (Date)hireDay.clone();
	}
	...
}
```

*   方法可以访问所属类任何对象的私有特性，而不仅限于隐式参数
*   按值调用：方法接收的是调用者提供的值。按引用调用：方法接收的是调用者提供的变量地址
*   方法可以修改按引用传递的变量值，但是不能修改按值传递的变量值
*   方法不能修改基本数据类型的参数（即数值型或布尔型）
*   方法可以改变对象参数的状态
*   方法不能让一个对象参数引用一个新的对象
*   方法签名只包括方法名和参数类型，不包括返回值类型，通过方法名来区分不同的方法
*   不要使用 finalize 方法来进行清理，这个方法原本要在垃圾回收器清理对象之前调用，但是如果使用这个方法就不能确定到底什么时候调用了，而且该方法已经被废弃
*   只访问对象而不修改对象的方法称为访问器方法，相反的有更改器方法

### Java 中值传递和引用传递

*   **按值传递**：值传递是指在调用方法时将实际参数复制一份传递到方法中，这样在方法中如果对参数进行修改，将不会影响到实际参数
    
*   **按引用传递**：引用传递就是直接把内存地址传过去，也就是说引用传递时，操作的其实都是源数据，有可能影响原数据，除了基本类型的参数以外，其它的都是引用传递，比如：Object，二维数组，List，Map 等
    
*   java 中所有的参数传递都是传递变量所代表的值的副本，因此，Java 中的对象引用还是按值传递的，并不是按引用传递
    

### 方法的内存分配与变化

*   方法只定义不调用是不会执行的，并且在 JVM 中也不会给方法分配 “运行所属” 的内存空间，只有在调用方法时才会动态的给这个方法分配所属的内存空间
*   JVM 内存划分上有这三块主要的内存空间：**方法区内存、栈内存、堆内存**
*   方法代码片段属于. class 字节码文件的一部分，字节码文件在类加载的时候被放到了方法区当中，所以 JVM 中的三块主要的内存空间中方法区内存最先有数据——方法代码片段
*   栈内存中分配方法运行的所属内存空间
*   方法在调用的瞬间，给该方法分配内存空间，在栈中发生压栈动作，方法调用结束之后，给该方法分配的内存空间全部释放，此时发生弹栈动作
*   局部变量运行阶段内存在栈中分配  
    ![](https://img-blog.csdnimg.cn/20210105105011191.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70#pic_center)
*   堆内存中的数据使用完毕后就变成了垃圾，但是并没有立即回收，会在垃圾回收器空闲的时候回收

### 方法重载

*   _方法重载（overload）：在同一个类中，允许存在一个以上的同名方法，只要它们的参数个数或者参数类型不同即可_
*   方法重载的特点：1、与方法返回值无关，只看方法名与参数列表；2、在调用时，Java 虚拟机通过参数列表的不同自动区分同名方法，这一过程被称为重载解析

### 方法重写

*   _方法重写（override）_：在子类中出现和父类中一模一样的方法声明，其也被称为方法覆盖或方法复写
*   方法重写的作用：当子类需要父类的功能，而功能主体子类有自己特有的内容时，这就可以重写父类中的方法，这样既沿袭了父类的功能，又定义了子类特有的内容（在子类中重写方法时如果想用父类中的方法则需使用 super 关键字调用，不然只有子类中重写的功能）
*   父类中的私有方法不能被重写，因为父类的私有方法子类根本无法继承
*   子类重写父类方法时，访问权限不能更低，即大于或等于，最好权限保持一致

### main 方法的格式讲解

```
public static void main(String[] args)
{
	.....
}
```

*   **public**：公共的，访问权限最大的修饰符，由于 main 方法是被 JVM 调用，所以权限要足够大
*   **static**：静态的，不需要创建对象，方便 JVM 调用
*   **void**：被 JVM 调用，不需要给 JVM 返回值
*   **main**：被 JVM 识别，程序的执行入口
*   **String[] args**：早期是为了接收键盘录入的数据所设置的参数，现在用 Scanner 了

构造器
---

1.  构造器是一种特殊的方法（构造方法），用来构造并初始化对象
2.  构造器与类同名，每个类可以有一个以上的构造器，构造器分无参构造和带参构造
3.  构造器没有返回值
4.  构造器总是伴随着 new 操作符一起调用
5.  对于一个类来说，当你没有写无参构造方法时，系统会默认给出（因为所有类都继承 Object 类），写了无参构造方法后系统就不会给了，但两者效果一样，**唯独当你只写了带参构造方法时，那么，这个类就没有无参构造方法了**

**在构造器中防止初始化字段为空，有两种方法：**

1.  “宽容性”，这种方法是当检测到传入进来的值为空（null）时，便会用一个不为空的值赋值，如下代码：

```
//构造方法
public Employee(String name)
{
	this.name = Objects.requireNonNullElse(name, "空名字");
}
```

2.  “严格型”，这种方法是当检测到传入进来的值为空时将自动终止程序，并抛出异常，这种方法的优点：1、异常报告会提供这个问题的描述；2、异常报告会准确地指出代码出错所在的位置，方便改错，如下代码抛出异常并提示 “名字不能为空”

```
public Employee(String name)
{
	Objects.requireNonNUll(name, "名字不能为空");
	this.name = name;
}
```

变量
--

### Java 中的变量类型

![](https://img-blog.csdnimg.cn/2021010518290191.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

### 成员变量与局部变量

两者区别：

1.  **在类中位置不同**：成员变量在方法外。局部变量在方法内或者方法声明上
2.  **在内存中的位置不同**：成员变量在堆内存中。局部变量在栈内存中
3.  **生命周期不同**：成员变量随着对象的创建而存在，随着对象的消失而消失。局部变量随着方法的调用而存在，随着方法调用完毕而消失
4.  **初始化值不同**：成员变量有默认的初始值（被 final 修饰的实例变量必须手动赋值，不能采用系统默认值）。局部变量没有默认的初始值，必须在定义赋值后才能使用

**注**：局部变量名可以与实例变量名相同，在方法被调用时采用就近原则

访问控制权限修饰符
---------

*   访问控制权限修饰符是用来控制元素访问范围的
*   访问控制权限修饰符包括：

<table><thead><tr><th>访问权限修饰符</th><th>功能</th></tr></thead><tbody><tr><td>public</td><td>对外部完全可见</td></tr><tr><td>protected</td><td>对本包和所有子类可见</td></tr><tr><td>缺省（不写修饰符）</td><td>对本包可见</td></tr><tr><td>private</td><td>仅对本类可见</td></tr></tbody></table>

*   访问控制权限修饰符可以修饰类、实例变量、方法…
*   访问控制权限修饰符不能修饰局部变量
*   当希望某个数据只给子类使用时，就可以用 protected 修饰
*   访问控制权限修饰符的范围：  
    private < 缺省 < protected < public

封装
--

*   封装：**隐藏对象的属性和实现细节，仅对外提供公共访问方法**
*   封装是一种信息隐藏技术, 在 java 中通过关键字 private 实现封装
*   封装的好处：1、提高了代码的复用性和安全性；2、保证内部结构的安全
*   封装的原则：屏蔽复杂，暴露简单

### this 关键字

*   this 关键字指向的是当前类的对象的引用，用来区分同名称的成员变量和局部变量
*   this 只能在类中的非静态方法中使用，静态方法和静态代码块中绝对不能出现 this，并且 this 只和特定的对象关联，而不和类关联，同一类的不同对象有不同的 this
*   this 关键字有两个含义：1、指示隐式参数的引用；2、调用该类的其它构造器

static 关键字
----------

*   static（静态关键字），可以修饰成员变量和成员方法
*   static 关键字的特点：1、随着类的加载而加载；2、优先于对象存在；3、**被类的所有对象共享**（判断是否使用静态关键字 static 的条件）；4、可以通过类名调用（推荐使用）
*   **static 方法**：static 方法也叫作静态方法，由于静态方法不依赖于任何对象就可以进行访问，因此对于静态方法来说是没有 this 关键字的使用的，因为 this 关键字要依附于对象，_在静态方法中不能访问类的非静态成员，但是，在非静态成员方法中是可以访问静态成员方法或静态变量的_
*   **static 变量**：static 变量也叫作静态变量或类变量，静态变量与非静态变量的区别在于：静态变量被所有对象共享，在内存中只有一个副本，它当且仅当在类初次加载时会被初始化；非静态变量是对象所拥有的，在创建对象的时候被初始化，在内存中存在多个副本，且各对象拥有的副本互不影响。static 成员变量的初始化顺序按照定义的顺序进行  
    **注：**
*   Java 中的 static 关键字不会影响到变量或者方法的作用域，在 Java 中能够影响访问权限的只有访问权限修饰符
*   静态成员变量虽然独立于对象，但是仍然可以通过对象进行访问（只要访问权限足够）
*   static 是不允许用来修饰局部变量的
*   可以理解为静态元素与对象没有关系，它属于类
*   静态元素中不可以使用 this、super 关键字
*   静态变量存储在方法区中的静态区

final 关键字
---------

*   final 关键字可以用来修饰类、方法和变量
*   **修饰类**：当用 final 修饰一个类时表明这个类不能被继承，final 类中的成员变量并不是默认 final 修饰的，可以根据需要设为 final，但 final 类中的所有方法却默认 final 修饰
*   **修饰方法**：对于重写问题而言，当父类中的某个方法被 final 修饰时，就表明父类中的这个方法不能被子类重写，也就是禁止子类重写此方法（主要目的是防止该方法的内容被修改）  
    **注**：重写的前提是子类可以从父类中继承此方法，如果父类中 final 修饰的方法同时又被 private 修饰，此时不会产生重写与 final 的矛盾，因为子类根本就没有继承这个方法，这个方法被私有化了，既然没有继承何来的重写，final 就无作用了，所以当父类中的某个方法的修饰符上同时有 private 和 final 时，在子类中依然可以出现同样声明的方法，因为这被视为在子类中重新定义了新的方法
*   **修饰变量**：被 final 修饰的变量就变成了常量，常量不能被重新赋值，只读不可写，Java 中定义常量时一般会加上 static 修饰，因为常量是不变的，任何对象拥有的都一样，如果一直 new 一样的东西就会浪费内存  
    **注**：被定义为 final 的成员变量必须在构造对象时就被初始化，并且以后不能再修改
*   final 修饰基本数据类型时是值不能被改变，而 final 修饰引用类型数据时是地址值不能被改变，但是该对象的内容是可以变的
*   final 修饰的实例变量必须手动赋值不能采用系统默认值
*   父类中的 final 方法可被子类继承，但是不能被子类重写
*   final 修饰的引用指向的对象无法被垃圾回收器回收

**注**：当变量被 final 修饰后，这个变量就变成了常量，既然是常量，那么它在内存中存储的就只是数值了，与之前的变量内存就无关系了，即当变量消失时，常量不会消失，依旧是那个数值在运算，所以，**若想某个数据不会因变量消失而消失，就将它修饰为常量**

代码块
---

在 Java 中使用 { } 括起来的代码被称为代码块，根据其位置和声明的不同可以分为：**局部代码块、构造代码块、静态代码块、同步代码块**

*   **局部代码块**：其又叫普通代码块，在方法中出现，限定变量生命周期，主要用于解决当前方法中变量名重复的问题。若想要在一个方法中多次使用同一个变量名，并且互不影响，这时就可以将该变量放入不同局部代码块当中，因局部代码块中的变量生命周期只限于该代码块中
*   **构造代码块**：在类中方法外出现，多个构造方法中相同的代码存放到一起，每次调用构造都执行，只要创建对象就会执行构造代码块，主要作用是对对象进行初始化
*   **静态代码块**：在类中方法外出现，加了 static 修饰符，最先被执行，且对于一个类的多个对象只执行一次，其主要作用是对类进行初始化，随着类的加载而执行，与创不创建对象无关
*   **同步代码块**：在方法中出现，使用 synchronized 关键字修饰，在多线程环境下，对共享数据的读写操作是需要互斥进行的，否则会导致数据的不一致性

_以上代码块执行顺序_：

```
静态代码块-->构造代码块-->构造方法-->局部代码块
```

继承
--

*   继承：多个类中存在相同属性（成员变量）和行为（成员方法）时，将这些内容抽取到单独一个类中，那么多个类就无需再定义这些属性和行为了，只要继承那个类即可
    
*   通过 extends 关键字可以实现类与类的继承
    

```
class 子类名 extends 父类名{}
```

*   单独的类称为父类、基类或超类，子类也叫派生类，父类中的内容是多个子类重复的内容
*   **继承的好处**：1、提高了代码的复用性，多个类相同的成员可以放到同一个类中；2、提高了代码的维护性，如果功能的代码需要修改，只需要修改父类这一处即可；3、让类与类之间产生了关系，这是多态的前提（这也是继承的缺点），使得类的耦合性增强
*   **开发的原则**：低耦合、高内聚
*   **继承的缺点**：1、破坏了封装，子类与父类之间紧密耦合，子类依赖父类的实现，造成子类缺乏独立性；2、支持扩展，但是往往以增强系统结构的复杂度为代价；3、不支持动态继承，在运行时子类无法选择不同的父类；4、子类不能改变父类的接口
*   **继承的特点**：1、Java 只支持单继承，不支持类的多继承，一个类只能有一个父类，不可以有多个父类；2、Java 支持多层继承（继承体系）

```
class A{}
class B extends A{}
class C extends B{}
```

*   子类只能继承父类中所有非私有的成员方法和成员变量
*   子类不能继承父类的构造方法，但是可以通过 super 关键字去访问父类的构造方法
*   不要为了部分功能而去继承
*   在 Java 中，所有的继承都是公共继承
*   继承绝对不会删除任何字段或方法
*   **Object 类是 Java 中所有类的父类，如果某个类没有明确地指出父类，那么 Object 类就被认为是这个类的父类，这个类就默认访问 Object 类的无参构造**

**在子类中访问一个变量的执行顺序**：首先在子类的局部范围中找，然后在子类成员范围中找，最后在父类成员范围中找（不能访问到父类的局部范围），如果还是没有就报错

### super 关键字

*   super 有两个含义：1、调用父类的方法；2、调用父类的构造器
*   调用父类成员变量

```
super.成员变量
```

*   调用父类的构造方法（使用 super 调用构造器的语句必须是子类构造器的第一条语句）

```
super(参数)
```

*   调用父类的成员方法

```
super.成员方法
```

**注：**

*   super 不是一个对象的引用，不能将值 super 赋给另一个对象变量，它只是一个指示编译器调用父类方法的特殊关键字
*   this 代表本类对应的引用，通过其操作本类的成员，super 代表父类存储空间的标识

### 继承中构造方法的关系

*   子类中所有的构造方法默认都会访问父类中的无参构造方法，因为子类会继承父类中的数据，可能还会使用父类的数据，所以子类初始化之前一定要先完成父类数据的初始化（先进行父类的初始化再进行子类的初始化，这叫分层初始化）
*   子类每一个构造方法的第一条语句都是 super()，这是系统默认的，写不写都有，但如果父类没有无参构造方法，这时在子类中系统就不会自动调用父类的无参构造了，需手动调用父类的构造方法，不然会报错

### 继承使用场景

采用假设法：如果有两个类 A、B，只要它们符合 A 是 B 的一种或者 B 是 A 的一种（A is B）或（B is A）这样的关系，就可以考虑使用继承

### 继承的设计技巧

1.  通过父类定义子类时，只需要在子类中指出子类与父类的不同之处即可，将通用的字段和方法（不管是否是抽象的）都放在父类（不管是不是抽象类）中，而更特殊的方法就放在子类中

多态
--

*   多态：**一个对象变量可以指示多种实际类型的现象（某一个对象在不同时刻表现出来的多种状态）**
*   多态的使用前提：1、要有继承关系；2、要有方法重写；3、要有父类引用指向子类对象

```
父类名 f = new 子类名();
```

*   多态的好处：1、提高了代码的维护性；2、提高了代码的扩展性
*   **向上转型**

```
fu f = new zi();
```

*   **向下转型**

```
zi z = (zi)f;//要求该f必须是能够转换为zi的
```

**注**：在进行以上两种转型之前应当对两对象之间进行检查，这是编程的好习惯，instanceof 操作符：检查对象之间是否能成功地进行转换  
例：

```
/*
	Manager类继承了Employee类
*/
Employee[] staff = new Employee[3];
Manager boss = new Manager();

if(staff[1] instanceof Manager)
{
	boss = (Manager)staff[1];
}
```

### 多态中的成员访问特点

*   成员变量：编译看父类，运行看父类
*   成员方法：**编译看父类，运行看子类**（由于只有成员方法存在方法重写，所以它运行看子类）
*   静态方法：编译看父类，运行看父类（静态和类相关，算不上重写，所以访问的还是父类的）
*   **动态绑定（后期绑定）**：在运行时能够自动的选择适当的方法，java 中的动态绑定是默认行为，_动态绑定是多态得以实现的重要因素_
*   **静态绑定（前期绑定）**：在程序执行前已经被绑定，即在编译过程中就已经知道这个方法是哪个类的方法，此时由编译器获取其它连接程序实现。在 Java 中，final、private、static 修饰的方法以及构造函数都是静态绑定的，不需程序运行，不需具体的实例对象就可以知道这个方法的具体内容。

抽象类
---

*   **抽象**：所谓抽象就是不是一种具体的事物而是一类事物的总和，如人分男人和女人，那么男人和女人相对于人来说就是具体的，人就是抽象的
*   **抽象类**：被 abstract 修饰的类叫抽象类，抽象类没有实体的东西，其无法直接创建对象（不能被实例化），因为调用抽象方法无意义，如果父类为抽象类，那么子类只有重写了父类中的所有方法抽象方法后才可以创建对象，否则该子类还是一个抽象类，因为假如子类没有对抽象类的所有方法重写，那么子类也就会继承了抽象类中的抽象方法，**只要有抽象方法的类就一定是抽象类，但抽象类不一定有抽象方法**
*   **抽象类的思想**：强制子类重写抽象方法
*   **抽象类的作用**：_降低接口实现类对接口的实现难度，将接口中不需要使用的方法交给抽象类实现，这样接口实现类只需要对要使用的方法进行重写_
*   **抽象方法**：被 abstract 修饰的方法叫抽象方法，其没有方法体，且抽象方法必须存在于抽象类中  
    **注**：抽象方法是没有方法体，没有方法体不代表空方法体

```
public abstract void eat(){...}//这叫空方法体，会报错
public abstract void eat();//这才叫无方法体
```

*   抽象类不可被实例化
*   抽象类是有构造器的
*   抽象类可以没有抽象方法
*   抽象类的使用场景一般在运用多态时比较适用
*   abstract 不能与这几个关键字共用：_private_（私有的方法子类是无法继承的，但是 abstract 又要求子类需要实现抽象方法，这是矛盾的）、_final_（类、方法被 final 修饰后不能被继承和重写，矛盾）、_static_（通过类名访问抽象方法是没有意义的，因为抽象方法没有方法体）
*   抽象类中的抽象方法是强制要求子类做的事情，非抽象方法是子类继承的事情，提高代码的复用性

接口
--

*   **接口**：接口是 Java 语言中的一种引用类型，它是抽象方法的集合，如果说类的内部封装了成员变量、构造方法和成员方法，那么接口的内部主要就是封装了方法
*   接口用关键字 interface 修饰

```
public interface 接口名{}
```

*   接口不是类，它是另外一种引用数据类型
*   接口不能创建对象，但是可以被实现，一个实现接口的类需要实现接口中所有的抽象方法，否则它就是抽象类
*   类与接口的关系为实现关系，即类实现接口，该类可以称为接口的实现类或接口的子类，实现用 implements 关键字修饰

```
class 类名 implements 接口名{}
```

*   接口不能定义构造方法（因为接口的作用主要是为了扩展功能，并不具体存在，没必要初始化）且接口中只有常量（隐式修饰，public static final）
*   接口不能创建对象，只能通过其实现类来使用
*   一个接口可以有多个方法且接口中所有的方法必须是抽象方法，默认修饰符 public abstract（隐式修饰），如果需要定义具体方法实现，则此时方法需要使用 default 修饰
*   接口不是被类继承而是被类实现
*   一个接口能继承另一个接口且接口支持多继承

```
public interface 接口1 extends 接口2, 接口3{}
```

*   接口中不能含有静态代码块以及静态方法（这里编译器不会报错，只是在实际开发中这样做是没有意义的）
*   一个类可以实现多个接口
*   接口中的方法都是公有的
*   接口是隐式抽象的，当声明一个接口的时候不必使用 abstract 修饰
*   接口中每一个方法是隐式抽象的，声明同样不需要 abstract 关键字
*   接口的作用是降低耦合度和扩展功能

**注**：开发中实现接口的类的类名命名格式：接口名 + Impi

*   **接口与抽象类的区别**：抽象类中定义的是该继承体系的共性功能，而接口中定义的是该继承体系中的扩展功能（特性功能）
*   **当引用类型作形式参数或返回值时**：  
    类：需要的是该类的对象  
    抽象类：需要的是该抽象类的子类对象（多态）  
    接口：需要的是该接口的实现类对象（多态）

简单修饰符归纳
-------

*   类的修饰符可有：public、缺省、final、abstract  
    **注**：成员内部类可有 private 和 static 修饰符，其余的普通类不行，因为成员内部类可以看作是外部类的成员
    
*   成员变量的修饰符可有：private、缺省、protected、public、static、final
    
*   构造方法的修饰符可有：private、缺省、protected、public
    
*   成员方法的修饰符可有：private、缺省、protected、public、static、final、abstract
    

内部类
---

*   **内部类**：一个类定义在另一个类里面或一个方法里面，这样的类称为内部类，内部类一般包括：_成员内部类、局部内部类、匿名内部类、静态内部类_
*   内部类和外部类之间没有继承关系

直接访问内部类成员的语法格式：

```
外部类名.内部类名 对象名 = new 外部类名().new 内部类名();
```

### 成员内部类

*   成员内部类是最普通的内部类，位于另一个类的内部
*   成员内部类可以无条件的访问外部类的所有成员变量和成员方法（包括 private 成员和静态成员）
*   当成员内部类拥有和外部类同名的成员变量或方法时，默认情况下访问的是内部类的成员（就近原则），若要访问外部类的同名成员，语法格式为：

```
外部类名.this.成员变量
外部类名.this.成员方法
```

*   在外部类如果要访问成员内部类的成员就必须先创建一个内部类的对象，再通过指向这个对象的引用来访问
*   内部类是依附于外部类存在的，如果要创建内部类的对象，前提是必须存在一个外部类的对象

### 局部内部类

*   局部内部类是定义在一个方法或者一个作用域里面的类，它和成员内部类的区别在于局部内部类的作用范围只限于方法内或该作用域内
*   局部内部类可以无条件的访问外部类的所有成员变量和成员方法（包括 private 成员和静态成员）
*   局部内部类就像是方法里面的一个局部变量一样是不能有 public、protected、private 以及 static 修饰的

### 匿名内部类

*   匿名内部类是没有名字的内部类且它只能使用一次（和匿名对象相似），通常用来简化代码
*   **匿名内部类的实质是对象（可将匿名内部类当作对象使用），并不是类，它是一个类或子类或实现接口类的一个对象，是一个继承了该类或实现了该接口的子类匿名对象**
*   匿名内部类不能有访问修饰符和 static
*   匿名内部类使用条件：必须继承一个父类或实现一个接口
*   匿名内部类是唯一一种没有构造方法的类，因此它的使用范围非常有限，大部分匿名内部类用于接口回调

**注**：一般来说，匿名内部类用于继承其他类或实现接口，并不需要增加额外的方法，只是对继承方法的实现或重写，语法格式：

```
new 类名或者接口名(){重写方法}//可以理解为一个对象
```

### 静态内部类

*   静态内部类是被 static 修饰的内部类
*   当外部类被加载的时候，静态内部类是不会被加载的
*   当使用静态内部类中的成员时，静态内部类才会被加载且仅仅加载一次，不会有线程安全的问题
*   与静态成员变量不一样的是静态内部类是不能通过外部类对象访问的
*   静态内部类不能使用外部类的非静态成员变量和方法，只能访问外部类的静态成员

**静态内部类的唯一访问语法格式**：

```
外部类名.内部类名 对象名 = new 外部类名.内部类名();
```

### JVM 的类加载规则

1.  static 类型的变量和方法在类加载的时候就会存在于内存中
2.  要想使用某个类的 static 变量或方法，那么这个类就必须要加载到 Java 虚拟机中
3.  非静态内部类并不随外部类一起加载，只有实例化外部类之后才会加载

**注**：现在考虑这个情况：外部类并没有实例化，内部类还没有加载，这时候如果调用内部类的静态成员或方法，内部类还没有加载却试图在内存中创建该内部类的静态成员，这是明显矛盾的，所以**非静态内部类不能有静态成员变量或静态方法（这里就和非静态方法不一样了）**

Java 中的 String
--------------

*   在 Java 中字符串（String）属于对象，并不是基础的数据类型
*   字符串直接赋值的方式是先到字符串常量池（方法区中）里面去找，如果有就返回，没有就创建对象并返回

```
//以下两者的区别
String s1 = new String("hello");//创建2个或1个对象，new操作符是一定要创建对象的
String s2 = "hello";//创建1个或0个对象
```

*   String 作参数传递时，虽然它是引用类型，但是效果和基本类型作参数传递是一样的，要将它看作基本类型

### Java 中的 StringBuffer 和 StringBuilder

*   **它们与 String 不同的是 StringBuffer 和 StringBuilder 类的对象能够被多次的修改，并且不产生新的未使用对象（除截取功能外）。**
*   StringBuffer 和 StringBuilder 相同点：1、两个类都是用来解决大量字符串拼接时而产生的中间对象问题；2、都需要实例化创建对象；3、都可以看作可变长度字符串，初始化容量都为 16
*   StringBuffer 和 StringBuilder 不同点：StringBuffer 是线程安全的（数据安全），运行速度较慢，StringBuilder 是非同步的（不安全），效率高，运行速度较快

**三者使用场景**

*   String：适用于少量的字符串操作的情况
*   StringBuilder：适用于单线程下在字符缓冲区进行大量操作的情况（多数情况下使用）
*   StringBuffer：适用于多线程下在字符缓冲区进行大量操作的情况

**以下说明用 StringBuilder 类举例，对于 StringBuffer 类同等适用**  
![](https://img-blog.csdnimg.cn/20210111102212696.png)

StringBuilder 的构造方法：

```
StringBuilder();
StringBuilder(int size);//指定初始容量的字符串缓冲区（不一定是实际长度）
StringBuilder(String str);//指定字符串内容的字符串缓冲区
```

StringBuilder 类的常见功能（除截取功能外，其余功能返回 StringBuilder 本身）：

```
1、添加功能
public StringBuilder append(String str);//可以把任意类型添加到字符串缓冲区里
public StringBuilder insert(int offset, String str);//在指定位置把任意类型的数据插入到字符串缓冲区里

2、删除功能
public StringBuilder deleteCharAt(int index);//删除指定位置的字符
public StringBuilder delete(int start, int end);//删除从指定位置开始到指定位置结束的这一范围的内容

3、替换功能
public StringBuilder replace(int start, int end, String str);

4、翻转功能
public StringBuilder reverse();

5、截取功能
public String subString(int start);//从start开始到末尾
public String subString(int start, int end);//从start到end
```

**注**：StingBuilder 类中的截取方法不再是返回本身了，而是重新开辟空间

**String 与 StringBuilder 相互转换**

*   String 转 StringBuilder

```
1、通过构造方法
StringBuilder s1 = new StringBuilder("字符串");

2、通过append()
StringBuilder s3 = new StringBuilder();
s3.append("字符串");
```

*   StringBuilder 转 String

```
StringBuilder builder = new StringBuilder("字符串");

1、通过构造方法
String str = new String(builder);

2、通过toString()
String str = builder.toString();
```

**String 和 int 的相互转换**

*   String 转 int

```
Integer.parseInt("数字字符串");
```

*   int 转 String

```
String.valueof(int型数据);
```

增强 for
------

**Java 中的增强 for（for each 循环）是一种很强的循环结构，可以用来依次处理数组中的每一个元素，不必考虑下标的问题**

```
for(int element : a)//这里的a是一个数组名或集合
{
	System.out.println(element);//输出每一个元素
}
```

*   增强 for 的循环变量将会遍历数组中的每一个元素而不需要使用下标值
*   for each 循环的局限性：**该循环只能遍历整个数组，每个元素都会用到且循环内部没有下标处理**
*   增强 for 的目标不能为 null，所以要在使用前考虑做判断
*   增强 for 其实是用来替代迭代器的

包装类
---

*   包装类类型：为了对基本数据类型进行更多更方便的操作，Java 就针对每一种基本类型数据提供了对应的类类型，即**将基本类型转化为对象操作**

<table><thead><tr><th>基本类型</th><th>引用类型（类）</th></tr></thead><tbody><tr><td>byte</td><td>Byte</td></tr><tr><td>short</td><td>Short</td></tr><tr><td>int</td><td>Integer</td></tr><tr><td>long</td><td>Long</td></tr><tr><td>float</td><td>Float</td></tr><tr><td>double</td><td>Double</td></tr><tr><td>char</td><td>Character</td></tr><tr><td>boolean</td><td>Boolean</td></tr></tbody></table>

**Integer 类中常用的方法**：

```
1、String转int
public static int parseInt(String s);//字符串s必须为由数字组成的字符串，字母的不行

2、进制转换(radix的范围：2<= radix <= 36)
public static String toString(int i, int radix);//i表示被转换的数（十进制数），radix表示进制数
```

**注**：

*   包装类都是被 final 修饰的，因此不能派生它们的子类
*   自动装箱规范要求 boolean、byte、char<= 127
*   介于 - 128 和 127 之间的 short 和 int 被包装到固定的对象中，不会创建新的对象  
    ![](https://img-blog.csdnimg.cn/20210111111924453.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)
*   如果在一个条件表达式中混合使用 Integer 和 Double 类型，Integer 值会拆箱，提升为 double 再装箱为 Double
*   装箱和拆箱是编译器要做的工作而不是虚拟机的，编译器在生成类的字节码时会插入必要的方法调用，虚拟机只是执行这些字节码

**Character 类中常用的方法**：

```
1、判断给定的字符大小写
public static boolean isUpperCase(char ch);//大写返回true，小写返回false
public static boolean isLowerCase(char ch);//大写返回false，小写返回true

2、判断给定的字符是否是数字
public static boolean isDigit(char ch);

3、把给定的字符转成大小写
public static char toUpperCase(char ch);
public static char toLowerCase(char ch);
```

Math 类
------

Math 类常用方法：

```
1、取绝对值
public static int abs(int a);

2、向上取整
public static double ceil(double a);

3、向下取整
public static double floor(double a);

4、取最大值
public static int max(int a, int b);

5、a的b次幂
public static double pow(double a, double b);

6、取随机值
public static double random();//返回值范围[0.0, 1.0)

7、四舍五入
public static int round(float a);

8、正平方根（开方）
public static double sqrt(double a);
```

Random 类
--------

*   Random 类作用：产生随机数的类

**Random 类的构造方法**：

```
Random();//默认种子，每次产生的随机数不同
Random(long seed);//指定种子，每次种子相同，随机数就相同
```

**Random 类常用方法**：

```
int nextInt();//返回int范围内的随机数
int nextInt(int n);//返回[0, n)范围内的随机数
int nextDouble();//随机获得一个0-1的double类型数据，括号里不填
int nextFloat();//随机获得一个0-1的float的类型数据
int nextBoolean();//随机获得true或false
```

System 类（系统类）
-------------

**System 类常用方法**：

```
1、运行垃圾回收器
public static void gc();

2、退出JVM
public static void exit(int status);//status - 退出状态。

3、获取当前时间的毫秒值
public static long currentTimeMillis();

4、复制数组
public static void arraycopy(Object src, int srcpos, Object dest, int destpos, int length);
参数：
	src：源数组
	srcpos：源数组中的起始位置
	dest：目标数组
	destpos：目标数组中的起始位置
	length：要复制的数组元素的数量
```

BigInteger 类
------------

*   **BigInteger 类是针对大整数的运算**
*   BigInteger 类的构造方法（以下只举一种）

```
public BigInteger(String val);//字符串val必须是数字字符串
```

*   BigInteger 类中常用的成员方法

```
1、加法
public BigInteger add(BigInteger val);

2、减法
public BigInteger subtract(BigInteger val);

3、乘法
public BigInteger multiply(BigInteger val);

4、除法
public BigInteger divide(BigInteger val);

5、返回商和余数的数组，该数组中只有两个元素：商array[0]、余数array[1]
public BigInteger[] divideAndRemainder(BigInteger val);
```

BigDecimal 类
------------

*   **用于浮点数运算，避免丢失精度**
*   BigDecimal 类的构造方法（以下只举一种）

```
public BigDecimal(String val);//字符串val必须是数字字符串
```

*   BigDecimal 类中常用的方法

```
1、加法
public BigDecimal add(BigDecimal augend);

2、减法
public BigDecimal subtract(BigDecimal subtrahend);

3、乘法
public BigDecimal multiply(BigDecimal multiplicand);

4、除法
public BigDecimal divide(BigDecimal divisor);

5、对除法运算结果的操作
public BigDecimal divide(BigDecimal divisor, int scale, int roundingMode);
参数：
	divisor：被除数
	scale：小数点后位数
	roundingMode：舍取模式，一般用四舍五入模式（BigDecimal.ROUND_HALF_UP）
```

Date 类
------

*   **Date 类是日期类，可以精确到毫秒**
*   Date 类的构造方法

```
public Date();//根据当前的默认毫秒值创建对象
public Date(long date);//根据给定的毫秒值创建对象,data是毫秒值，日期是从1970年1月1日0:0：0开始计算，data加上这个时间即可
```

*   Date 类中常用的方法

```
1、获取时间，以毫秒为单位返回
public long getTime();

2、设置时间
public void setTime(long time);
```

DateFormat 类
------------

*   **DateFormat 类是针对日期进行格式化和针对字符串进行解析的类，但是该类是抽象类，所以使用其子类 SimpleDateFormat**
*   SimpleDateFormat 类构造方法

```
public SimpleDateFormat(String pattern);//指定日期的格式（如：yyyy-MM-dd HH:mm:ss）
public SimpleDateFormat();//默认格式表示日期
```

*   SimpleDateFormat 类的常用方法

```
1、Date转String（格式化）
public final String format(Date date);

2、String转Date（解析）
public Date parse(String source);
```

Calendar 类
----------

*   **Calendar 类是日历类，它是一个抽象类，其封装了所有的日历字段值，通过统一的方法根据传入不同的日历字段可以获取值**
*   Calendar 类中常用的方法

```
1、获取一个日历对象
Calendar rightNow = Calendar.getIntstance();

2、返回给定日历字段的值，日历字段中的每个日历字段都是静态的成员变量，并且是int型
public int get(int field);

3、根据给定的日历字段和对应的时间来对当前的日历进行操作
public void add(int field, int amount);

4、设置当前日历的年月日
public final void set(int year, int month, int date);
```

集合
--

**数组和集合类同是容器，区别在于：1、数组虽然也可以存储对象（对象数组），但长度是固定的，集合长度是可变的；2、数组可存储基本数据类型，但集合只能存储对象的内存地址（引用），且集合可存储不同类型的对象**

**集合继承体系图**：  
![](https://img-blog.csdnimg.cn/20210112181045438.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

*   ArrayList：底层数据结构是动态数组，默认初始化容量为 10（底层先创建了一个长度为 0 的数组，当添加第一个元素的时候，初始化容量为 10），自动扩容（扩容到原容量的 1.5 倍），支持随机访问，查询快，增删慢，非同步，线程不安全，效率高
*   Vector：底层数据结构是动态数组，查询快，增删慢，同步，线程安全，效率低
*   LinkedList：底层数据结构是双向链表，不支持随机访问，查询慢，增删快，非同步，线程不安全，效率高

### Collection

*   Collection 中的常用功能（以下功能的结果遵循谁调用这个方法谁就改变）

```
1、添加功能
boolean add(Object obj);//添加一个元素
boolean addAll(Collection c);//添加一个集合的元素

2、删除功能
void clear();//移除所有元素
boolean remove(Object o);//移除一个元素
boolean removeAll(Collection c);//移除一个集合的元素，只要有一个元素被移除就返回true

3、判断功能
boolean contains(Object o);//判断集合中是否包含指定元素
boolean containsAll(Collection c);//判断集合中是否包含指定的集合元素，只有包含所有元素才叫包含，才返回true
boolean isEmpty();//判断集合是否为空

4、长度功能
int size();//这里获取的是元素的实际个数，不是集合的容量

5、交集功能
/*
	设有两个集合A、B
	A.retainAll(B);
	若A、B之间有交集就把交集保存到集合A中，若无交集，那么集合A就为空，
	至于返回结果则取决于保存交集的A集与保存之前的集合内容是否有变化，
	有变化就返回true，没有变化就返回false
*/
boolean retainAll(Collection c);

6、集合转数组
Object[] toArray();//转型后的数组中每一个元素都是Object类型的
```

### 迭代器

**集合的迭代也叫集合的遍历，集合的迭代是通过迭代器完成的，迭代器是依赖于集合而存在的，也就是有集合才有迭代器**

*   迭代器（集合的专用遍历方式）

```
Iterator<E> iterator();
```

*   Iterator 接口中的方法：

```
Object next();//获取元素之后自动后移
boolean hasNext();//判断是否还有元素，如果仍有元素可以迭代就返回true
```

*   迭代举例

```
Collection c = new ArrayList();
方式一：
Iterator it = c.iterator();//通过集合对象获取迭代器对象
while(it.hasNext())
{
	System.out.println(it.next());
}

方式二：
for(Iterator it = c.iterator(); it.hasNext();)
{
	System.out.println(it.next());
}

总：方式一结构清晰；方式二效率更高，运行更快，因为it循环之后就变成垃圾
```

**问**：_迭代器为什么不定义成一个类，而定义成一个接口？_  
**答**：Java 中提供了很多的集合类，而这些集合类的数据结构是不同的，意味着它们的存储方式和遍历方式也各不相同，遍历一个集合应当具备判断功能和获取功能，因每种集合的方式不太一样，所以把这两个功能提取出来，这种方式就是接口，这个接口的实现类是以内部类的方式体现的

### List

*   List 集合：有序的 Collection（也称为序列），此接口的用户可以对列表中每个元素的插入位置进行精确控制，用户可以根据元素的整数索引（在列表中的位置）访问元素，并搜索列表中的元素，与 Set 不同的是 List 允许重复的元素
*   List 集合的特点：1、有序（存储和取出的元素顺序一致）；2、可重复
*   List 集合特有的遍历

```
List  c = new ArrayList();
for(int i = 0; i < c.size(); i++)
{
	System.out.println(c.get(i));
}
```

*   List 集合特有的迭代器（列表迭代器）

```
列表迭代器：ListIterator listIterator();
该迭代器继承了Iterator迭代器，所以也可直接使用hasNext()和next()

列表迭代器特有的功能：
逆向遍历：
	Object previous();//获取上一个元素
	boolean hasprevious();//判断是否有元素
正向遍历：
	Object next();
	boolean hasNext();

注：ListIterator可以实现逆向遍历，但是必须同一迭代器正向遍历之后才能进行逆向遍历，无实际意义，一般不使用
```

### LinkedList

*   LinkedList 集合特有的功能

```
1、添加功能
public void addFirst(Object o);//开头添加
public void addLast(Object o);//结尾添加

2、获取功能
public Object getFirst();//获取开头元素
public Object getLast();//获取结尾元素

3、删除功能
public Object removeFirst();//删除开头元素并返回被删除元素
public Object removeLast();//删除结尾元素并返回被删除元素
```

### Map

*   Map 集合：Map 集合中键和值的关系——映射，可以通过键来获取值
*   Map 集合的特点：将键映射到值的对象，一个映射不能包含重复的键，每个键最多只能映射到一个值（无序不重复）
*   Map 集合与 Collection 集合的区别：1、Map 集合存储元素是成对出现的（键值对），Map 集合的键是唯一的，值是重复的，Collection 集合存储元素是单独出现的，Collection 的 Set 是唯一的，List 是可重复的；2、Map 集合的数据结构针对键有效，跟值无关，Collecton 集合的数据结构针对元素有效
*   给定一个键和一个值就可以将该值存储在一个 Map 对象中，之后可通过键来访问对应的值
*   当访问的值不存在的时候，方法就会抛出一个 NoSuchElementException 异常
*   当对象的类型和 Map 里元素类型不兼容时，方法就会抛出一个 ClassCastException 异常
*   当在不允许使用 Null 对象的 Map 中使用 Null 对象时，方法就会抛出一个 NullPointerException 异常
*   **Map 集合中常用的功能：**

```
1、添加功能
/*
（key表示键，value表示值）如果键是第一次存储就直接存储元素并返回null，
如果键不是第一次存储就用现在的值把以前的值替换掉并返回以前的值
*/
v put(k key, v value);

2、删除功能
void clear();//移除所有的键值对元素
v remove(Object key);//根据键删除键值对元素并把值返回

3、判断功能
boolean containsKey(Object key);//判断集合中是否包含指定的键
boolean containValue(Object value);//判断集合是否包含指定的值
boolean isEmpty();//判断集合是否为空

4、长度功能
int size();//返回集合中键值对的对数

5、获取功能
v get(Object key);//根据键来获取值
Set<K> keySet();//获取集合中所有键的集合
Collection<V> values();//获取集合中所有值的集合
Set<Map.Entry<K,V>> entrySet();//返回的是键值对对象的集合
```

*   **Map 集合的遍历**  
    ![](https://img-blog.csdnimg.cn/20210113113825176.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

Hashtable 与 HashMap 的区别：

*   Hashtable：线程安全，效率低，不允许 null 键和 null 值，初始容量为 11，扩容是：原容量 * 2+1
*   HashMap：线程不安全，效率高，允许 null 键和 null 值

### 哈希表的数据结构

![](https://img-blog.csdnimg.cn/20210113155125860.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)  
**注**：

*   **如果一个类的 equals() 方法重写了，那么它的 hashCode() 方法必须重写**
*   **放在 HashMap 集合 Key（键）部分的和放在 HashSet 集合中的元素需要同时重写 hashCode() 方法和 equals() 方法**
*   **为了提高检索效率，在 JDK8 之后，如果哈希表的单向链表中元素大于等于 8 个 并且 数组长度大于等于 64 时，单向链表这种数据结构才会变成红黑树数据结构，如果数组长度小于 64 则会先将数组进行一次扩容（2 倍），如果扩容之后还没有达到长度 64 则继续比较下一个节点，链表不会转成红黑树，直到 table 数组长度大于等于 64 时单向链表才会变成红黑树，当红黑树上的节点数量小于 6 时，会重新把红黑树变成单向链表**
*   HashMap 的默认初始化容量是 16（建议是 2 的倍数），加载因子是 0.75（当哈希表的元素超过总容量的 75% 时，哈希表将自动开始扩容（原容量 * 2）

### TreeSet

**TreeSet 集合底层实际上是一个 TreeMap，也就是一个二叉树，放到 TreeSet 集合中的元素等同于放到 TreeMap 集合的 Key（键）部分了，TreeSet 集合中的元素无序不重复，可以按照元素的大小顺序自动排序**

**重点：**  
TreeSet 集合自动排序的特点是通过实现 java.lang 包下 Comparable 接口或 java.util 包下的 Comparator 接口来完成的，即要指定比较规则。如 String、Integer 等已经默认实现了 Comparable 接口，所以 TreeSet 中的 String、Integer 就不用再指定比较规则了，而放到 TreeSet 或 TreeMap 集合 key 部分的自定义元素要想做到排序就必须指定比较规则，有如下两种方式：

1.  自定义元素实现 Comparable 接口中的 compareTo() 方法，在 compareTo() 方法中指定比较规则，这时 TreeSet 或 TreeMap 集合的构造方法是无参构造  
    ![](https://img-blog.csdnimg.cn/20210114183613333.png)  
    ![](https://img-blog.csdnimg.cn/20210114184024152.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)
    
2.  在构造 TreeSet 或 TreeMap 集合时，用匿名内部类的方式实现比较器 Comparator 接口中的 compare() 方法（也可以单独建一个比较器类实现 Comparator 接口），在 compare() 方法中指定规则，这时 TreeSet 或 TreeMap 集合的构造方法是带参构造  
    ![](https://img-blog.csdnimg.cn/20210114184115907.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)
    

说明：compareTo() 方法的返回值：

*   返回值 0 表示相同，value 会覆盖
*   返回值大于 0，会继续在右子树上找（左小右大）
*   返回追小于 0，会继续在左子树上找（左小右大）

_问：Comparable 和 Comparator 怎么选择_  
答：当比较规则不会发生改变的时候，或者说当比较规则只有一个的时候建议使用 Comparable 接口，如果比较规则有多个，并且需要多个比较规则之间频繁切换，建议使用 Comparator 接口

### Collections

**Collections 是针对集合进行操作的工具类，其中的方法都是静态的**

Collection 与 Collections 的区别：

*   Collection：是单列集合的顶层接口，有子接口 List 和 Set
*   Collections：是针对集合操作的工具类

Collections 类中的常用方法：

```
1、排序，默认情况下是自然排序
public static <T> void sort(List<T> list);

2、二分查找
public static <T> int binarySearch(List<?> list,T key);

3、最大值（根据元素的自然顺序）
public static <T> T max(Collection<?> coll);

4、最小值
public static <T> T min(Collection<?> coll);

5、随机转换
public static void shuffle(List<?> list);

6、反转
public static void reverse(List<?> list);

7、将线程不安全的List转换成线程安全的List（Set和Map也有类似的方法）
public static <T> List<T> synchronizedList(List<T> list);
```

泛型
--

**泛型是一种把数据类型明确的工作推迟到创建对象或者调用方法的时候才去明确的特殊的类型，也叫参数化类型，把类型当作参数一样传递**

*   泛型的格式：

```
<数据类型> 注：这里的数据类型只能是引用类型

例：ArrayList<String> array = new ArrayList<String>();//array这个集合中所有元素都是String类型的，且只能是String类型的
```

*   泛型的好处：1、把运行时期的问题提前到了编译期间；2、避免了强制类型转换；3、优化了程序设计；4、增强了程序的安全性
*   看 API，如果类、接口、抽象类后面跟有 <E> 就表示要使用泛型，一般来说在集合中使用的情况居多

### 泛型通配符

*   <?>：任意类型，如果没有明确，那么就是 Object 以及任意的 Java 类了
*   泛型如果明确时前后必须一致
*   ？表示任意的类型都可以（后面 new 的类型是任意引用类型）

```
Collection<?> c1 = new ArrayList<Object>();
Collection<?> c2 = new ArrayList<Animal>();
Collection<?> c3 = new ArrayList<Dog>();
```

*   <? extends E>：向下限定，后面 new 的类型必须是 E 及其子类

```
Collection<? extends Animal> c = new ArrayList<Dog>();//Dog继承类Animal
```

*   <? super E>：向上限定，后面 new 的类型必须是 E 及其父类

静态导入
----

**可以直接导入到静态方法的级别**

*   静态导入格式

```
import static 包名.类名.方法名;

import static java.lang.System.out;
out.println("java");
```

*   方法必须是静态的
*   当有多个同名静态方法时，就必须加前缀使用了，即用静态导入的方法是唯一的

可变参数
----

*   当定义方法的时候不确定该定义多少个参数时就使用可变参数

```
public int sum(int...a);//这里必须是三个点
```

*   可变参数本质上是一个数组
*   如果一个方法有可变参数，并且有多个参数时，可变参数必须写在最后面

```
public int sum(int b, int c, int...a);
```

*   一个方法只能指定一个可变参数

枚举
--

**枚举（enum）是一种引用数据类型，编译之后生成 class 文件，枚举中的每一个值可以看作常量**

枚举语法格式;

```
enum 枚举类型名
{
	枚举值1, 枚举值2， 枚举值3...
}
```

说明：结果只有两种情况的建议使用布尔类型，结果超过两种并且可以一枚一枚列举出来的建议使用枚举类型，如颜色、四季、星期等都可以使用枚举类型

下列程序只是为了演示枚举语法，并无实际开发意义：  
![](https://img-blog.csdnimg.cn/20210115103333408.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

异常
--

### 异常继承体系图

![](https://img-blog.csdnimg.cn/20210116110712822.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

*   **错误**：错误不是异常而是脱离程序员控制的问题，Java 程序通常不捕获错误，错误一般发生在严重故障时，它们在 Java 程序处理的范畴外
*   **编译时异常**：也叫受检异常或受控异常，编译时异常不是在编译阶段发生的（_所有的异常都发生在运行阶段_），它表示必须在编译（编写）程序的时候预先对这种异常进行处理，如果不处理编译器就报错（**直接父类为 Exception 的异常称为编译时异常**）
*   **运行时异常**：也叫未受检异常或未受控异常，Runtime Exception 的子类称为运行时异常，运行时异常在编译阶段可处理也可不处理
*   异常在 Java 中以类的形式存在，每一个异常类都可以创建异常对象
*   不管是错误还是异常都是可抛出的，所有的错误只要发生，Java 程序只有一个结果，那就是终止程序的执行，退出 JVM，因为错误是不可处理的

### **处理异常的两种方式**

1.  在方法内部使用 try…catch… 语句进行异常捕捉，可理解为异常自行处理

try…catch… 语法格式：

```
try{
	//可能出现异常的代码
}catch(异常类名 变量名){
	//针对异常的提示处理
}finally{
	//不管try内有没有异常出现，finally语句块中的语句一定执行
	//这里一般是资源的释放和关闭
}

注：
1、虽然说所有的异常类名都可写Exception，但异常类名能明确就明确，方便调错
2、try语句块中的某一行出现异常该行后面的代码不会执行，只有在try...catch...捕捉异常后，后续代码才可执行
3、当try语句块中有return时，finally中的语句也会执行，且return语句在finally之后执行，也就是最后执行
4、如果在执行finally之前JVM退出了（System.exit(0)），那么就不会再执行finally里的语句了
```

出现多个异常时：

```
方式一：针对每一个异常写一个try...catch...
	
	方式二：将异常集中在一个try中，多个catch
	try{
		...
	}catch(异常类名1 变量名){
		...
	}catch(异常类名2 变量名){
		...
	}

注：平级关系的异常谁前谁后无所谓，如果出现父子关系，那么父必须出现在子的后面，否则会报错
```

JDK8 的一个新异常处理方式

```
try{
	...
}catch(异常类名1 | 异常类名2 | ... 变量名){
	...
}

注：这个方法很简洁，特点是处理方式一致，且多个异常间必须是平级关系
```

异常对象有两个重要的方法

```
1、获取异常简单的描述信息
public String getMessage();

2、打印异常追踪的堆栈信息
public void printStackTrace();
```

例：  
![](https://img-blog.csdnimg.cn/20210116113239624.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

2.  在方法声明的位置上使用 throws 关键字，将异常抛给调用者处理（上抛），调用者也面临这两种处理方式

语法格式：

```
throws 异常类名（可以跟多个异常类名）
```

![](https://img-blog.csdnimg.cn/20210116131657813.png)

*   throws：用于方法声明后面，其后跟的是异常类名，将异常上抛给调用者处理，抛出的异常可能会发生
*   throw：手动抛异常，用在方法体内，其后跟的是异常对象名，且只能抛出一个异常对象，抛出的异常一定会发生。注意：1、当抛出的是编译时异常就必须与 throws 连用（因为编译时异常必须处理），而抛出的是运行时异常就不必与 throws 连用（因为运行时异常可处理也可不处理）。2、只要异常没有被捕捉，采用上抛的方式，此方法的后续代码不会执行

```
public static void myException() throws ClassNotFoundException
{
	Class.forName("文件路径");
	//因为异常只是被上抛，没有被处理，所以以下代码不会执行
	System.out.println("Hello");
}
```

**如果方法内部可以将异常处理就用 try，如果内部处理不了就用 throws 上抛**

### 自定义异常

分两步：

1.  编写一个类继承 Exception 或 Runtime Exception，要编写编译时异常就继承 Exception，如果编写运行时异常就继承 Runtime Exception
2.  提供两个构造方法，一个无参构造，一个带有 String 参数的构造方法

```
public class MyException extends Exception //编译时异常
{
	public MyException()
	{
		
	}
	public MyException(String s)
	{
		super(s);
	} 
}
```

### final、finally、finalize

*   final：关键字，表示最终，修饰类时类不能被继承，修饰方法时方法不能被重写，修饰变量时变量变常量
*   finally：关键字，是异常处理的一部分，用于释放资源，一般来说其中的代码肯定会执行，特殊情况：在执行到 finally 之前 JVM 退出了
*   finalize：标识符，Object 类的一个方法，用于垃圾回收

### 异常注意事项

*   子类重写父类方法时，子类的方法必须抛出相同的异常或父类异常的子类
*   如果被重写的方法没有异常抛出，那么子类的方法绝对不可以抛出异常，如果子类方法内部有异常产生，那么子类只能 try…catch…

IO 流
----

### IO 流的释义

**IO 流是数据传输的通道 / 管道，是实现数据输入和输出的基础，通过 IO 流可以完成硬盘文件的读和写**

### IO 流的分类

![](https://img-blog.csdnimg.cn/20210117202910195.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

按照流的方向进行分类（以内存作为参照物）：

*   **输入流**：数据从硬盘到内存里去叫作输入或读，可理解为读进去
*   **输出流**：数据从内存中出来到硬盘叫作输出或写，可理解为写出来

按照数据的读取方式进行分类：

*   **字节流**：按照字节的方式读取数据，一次读取一个字节 byte，等同于一次读取 8 个二进制位，这种流是万能的，什么类型的文件都可以读取，包括：文本文件、图片、声音文件、视频文件
*   **字符流**：按照字符的方式读取数据，一次读取一个字符，这种流是为了方便读取普通文本文件而存在的，但这种流不能读取：图片、声音、视频等文件，只能读取纯文本文件，也读不了 word 文件

总：在 Java 中只要类名以 “Stream” 结尾的都是字节流，以 “Reader/Writer” 结尾的都是字符流

*   字节输入流：InputStream
*   字节输出流：OutputStream
*   字符输入流：Reader
*   字符输出流：Writer

注：1、以上所有的流都实现了 Closeable 接口，表明所有的流都可以关闭，都有 close() 方法，切记用完流之后一定要关闭流。2、所有的输出流都实现了 Flushable 接口，表明所有的输出流都是可以刷新的，都有 flush() 方法，输出流在最终输出完后一定要记得 flush() 方法刷新一下，这个刷新表示将通道当中剩余未输出的数据强行输出完（清空通道），如果没有 flush() 方法可能为导致数据丢失

### 文件专属流

*   字节输入流（FileInputStream）

```
常用方法

1、返回流当中剩余的没有读到的字节数量
public int available();

2、跳过n个字节不读
public long skip(long n);

3、返回读到的字节值，每次读一个字节，读完自动后移，文件读完返回-1
public int read();

4、将读到的内容存入字节数组中，且最多读入b.length个字节，返回读到的字节总数，文件读完返回-1
public int read(byte[] b);
```

*   字节输出流（FileOutputStream）

```
常用方法

1、将指定 byte 数组中从偏移量 off 开始的 len 个字节写入此文件输出流
public void write(byte[] b, int off, int len);
```

*   字符输出流与字符输入流的常用方法与以上的区别在于把 byte 数组换成了 char 数组

文本复制：  
![](https://img-blog.csdnimg.cn/20210117222434766.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

```
用字节流完成文本复制
FileInputStream fis = null;
		FileOutputStream fos = null;
		try{
			//创建字节输入流对象
			fis = new FileInputStream("src/lianxi_io/myio_1");
			//创建字节输出流对象,true表示追加
			fos = new FileOutputStream("src/lianxi_io/myio_2", true);
			
			byte[] bytes = new byte[1024];
			int rcount = 0;
			while((rcount = fis.read(bytes)) != -1)
			{
				fos.write(bytes, 0, rcount);
			}
			//输出流刷新（刷新缓冲区）
			fos.flush();
		} catch (FileNotFoundException e){
			
			e.printStackTrace();
		} catch (IOException e){
			e.printStackTrace();
		} finally {
			//关闭流
			if(fis != null)
			{
				try{
					fis.close();
				} catch (IOException e){
					e.printStackTrace();
				}
			}
			
			if(fos != null)
			{
				try{
					fos.close();
				} catch (IOException e){
					e.printStackTrace();
				}
			}
		}
```

### 转换流

*   InputStreamReader

```
通过构造方法将字节输入流转换为字符输入流
public InputStreamReader(InputStream in);
```

*   OutputStreamWriter

```
通过构造方法将字节输出流转换为字符输出流
public OutputStreamWriter(OutputStream out);
```

**注**：当一个流的构造方法中需要一个流的时候，这个被传进来的流叫作节点流，外部负责包装的这个流叫包装流或处理流，**只需关闭包装流就行，当包装流关闭后节点流会自动关闭**

### 缓冲流

**缓冲流是为了提高数据的读写速度而存在的，因为缓冲流自带缓冲区，不需要再定义数组**

*   BufferedReader
*   BufferedWriter
*   BufferedInputStream
*   BufferedOutputStream

注：其中 BufferedReader 的特殊方法

```
一次读取一个文本行，包含该行内容的字符串，不包含任何行终止符，如果已到达文本末尾，则返回 null 
public String readLine();
```

### 数据流

**数据流中 DateOutputStream 可以将数据连同数据的类型一并写入文件中，这个文件不是普通的文本文件，用记事本打不开，只能使用 DateInputStream 去读，并且读的时候需要与写的顺序一致才可以正常取出数据**

### 标准输出流

*   printStream
*   printWriter

标准的输出流默认输出到控制台

```
System.out.println("Hello");
```

改变输出方向, 输入到指定文本中

```
PrintStream ps = new PrintStream(new FileOutputStream("src/lianxi_io/myio_1", true));
//改变输出方向
System.setOut(ps);
```

### 序列化与反序列化

*   **序列化**：Java 对象按照流的方式存入文本文件或网络中，将 Java 对象的状态保存下来的过程，通过 ObjectOutputStream 完成（对象 ----> 流数据）
*   **反序列化**：将硬盘上的流数据重新恢复到内存中，恢复成 Java 对象，通过 ObjectInputStream 完成（流数据 ----> 对象）
*   **参与序列化和反序列化的对象必须实现 serializable 接口**
*   serializable 接口只是一个标志接口，这个接口当中什么也没有，它是给 JVM 参考的，当 JVM 识别到这个接口后，就会为实现该接口的类自动生成一个序列化版本号用来标识类
*   Java 虚拟机识别一个类的时候先通过类名，如果类名一致就再通过序列化版本号
*   凡是一个类实现了 serializable 接口，建议手动给该类提供一个固定不变的序列化版本号，这样，以后这个类即使被修改了但是版本号没有变，Java 虚拟机也会认为是同一类

```
private static final long serialVersionUID= 1L;
```

*   在实现 serializable 接口的类中若不想某个成员变量被序列化，可用 transient 关键字声明

实例：

```
序列化
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
import java.io.ObjectOutputStream;
import java.io.Serializable;

public class IoTest
{
	public static void main(String[] args)
	{
		ObjectOutputStream oos = null;
		try{
			//序列化
			oos = new ObjectOutputStream(new FileOutputStream("src/lianxi_io/myio_1"));
			
			oos.writeObject(new Student("xss", 23));
			oos.writeObject(new Student("xxx", 34));
			
			oos.flush();
		} catch (FileNotFoundException e){
			e.printStackTrace();
		} catch (IOException e){
			e.printStackTrace();
		} finally {
			try{
				oos.close();
			} catch (IOException e){
				e.printStackTrace();
			}
		}
	}
}

class Student implements Serializable
{
	//手动固定序列化版本号
	private static final long serialVersionUID = 2L;
	private String name;
	private int age;
	private String address;

	public Student()
	{

	}

	public Student(String name, int age)
	{
		super();
		this.name = name;
		this.age = age;
	}

	public String toString()
	{
		return "Student []";
	}

}
```

```
反序列化
import java.io.FileInputStream;
import java.io.FileNotFoundException;
import java.io.IOException;
import java.io.ObjectInputStream;

public class lianxi
{
	public static void main(String[] args)
	{
		ObjectInputStream ois = null;
		try{
			//反序列化
			ois = new ObjectInputStream(new FileInputStream("src/lianxi_io/myio_1"));
			
			Object obj1 = ois.readObject();
			System.out.println(obj1);
			Object obj2 = ois.readObject();
			System.out.println(obj2);
		} catch (FileNotFoundException e){
			e.printStackTrace();
		} catch (IOException e){
			e.printStackTrace();
		} catch (ClassNotFoundException e){
			e.printStackTrace();
		} finally {
			try{
				ois.close();
			} catch (IOException e){
				e.printStackTrace();
			}
		}
	}

}
```

### File 类

*   **相对路径**：从当前路径开始（在 IDEA 和 Eclipse 中，默认的当前路径是项目（project）路径）
*   **绝对路径**：从盘符开始
*   File 类的概述：文件和目录路径的抽象表示形式
*   File 类的构造方法

```
1、根据一个路径得到FIle对象
public File(String pathname);

2、根据一个目录和一个子文件/目录得到File对象
public File(String parent, String child);

3、根据一个父File对象和一个子文件/目录得到对象
public File(File parent, String child);
```

*   创建功能

```
1、创建文件，如果已存在该文件就不再创建并返回false
public boolean createNewFile();

2、创建文件夹，如果已存在该文件就不再创建并返回false
public boolean mkdir();

3、创建文件夹，且是多级创建，如果父文件夹不存在就创建
public boolean mkdirs()
```

*   删除功能（Java 中的删除不走回收站）

```
删除文件或文件夹
public boolean delete();
```

*   重命名功能（如果路径相同就是重命名，路径不同就是重命名加剪切）

```
public boolean renameTo(File dest);
```

*   判断功能

```
1、判断是否是目录/文件夹
public boolean isDirectory()

2、判断是否是文件
public boolean isFile();

3、判断是否存在
public boolean exists();

4、判断是否可读
public boolean canRead();

5、判断是否可写
public boolean canWrite();

6、判断是否隐藏
public boolean isHidden();
```

*   基本获取功能

```
1、获取绝对路径
public String getAbsolutePath();

2、获取相对路径
public String getPath();

3、获取名称
public String getName();

4、获取文件大小
public long length();

5、获取最后一次修改时间，毫秒值
public long lastModified();
```

*   高级获取功能

```
1、获取指定目录下的所有文件或文件夹的名称数组
public String[] list();

2、获取指定目录下的所有文件或文件夹的File数组
public File[] listFiles();
```

多线程
---

### 名词释义

*   **程序**：为完成特定任务，用多种语言编写的一组指令的集合，即指一段静态的代码，静态对象
*   **进程**：程序的一次执行过程，或是正在运行的一个程序，是一个动态的过程
*   **线程**：进程可进一步细化为线程，是一个程序内部的一条执行路径，同时它也是程序使用 CPU 的最基本单位（进程中要同时干几件事情，每一件事情的执行路径就是线程）
*   **并行**：多个 CPU 同时执行多个任务，可理解为多个人同时做不同的事
*   **并发**：一个 CPU 同时执行多个任务，可理解为多个人做同一件事
*   **单线程**：一个进程只用一条执行路径
*   **多线程**：一个进程有多条执行路径

注：

*   线程是依赖于进程而存在的，只有运行的程序才会出现进程
*   多进程的意义在于提高 CPU 的使用率
*   多线程的意义在于提高程序的处理效率
*   不同的进程内存独立不共享
*   在内存当中多个线程共享堆内存和方法区内存，而每一个线程都有自己的栈内存，栈内存不共享，一个线程一个栈
*   **Java 程序运行原理**：Java 命令会启动 JVM，JVM 可看作是一个应用程序，等同于启动了一个应用程序，也就是启动了一个进程，该进程会自动启动一个主线程，然后主线程会调用某个类的 main 方法，所以 main 方法运行在主线程中，然后再启动垃圾回收线程用来看护主线程，JVM 至少启动了这两个线程，所以 JVM 是多线程的

### 多线程实现

**方式一**：编写一个类，直接继承 Thread 类并重写 run() 方法

```
public class lianxi_02
{
	public static void main(String[] args)
	{
		//创建线程对象
		MyThread mt = new MyThread();
		
		mt.start();//启动线程
	}
}

//自定义类继承Thread类
class MyThread extends Thread
{
	//在自定义类中重写run()方法
	public void run()
	{
		//被线程执行的代码
		...
	}
}
```

*   在继承 Thread 类的类中只有 run() 方法中的代码才会被线程执行
*   直接调用 run() 方法就是普通方法调用
*   start() 方法的作用：启动一个分支线程，在 JVM 中开辟一个新的栈空间，只要新的栈空间开出来了，start() 方法就结束了，启动成功的线程会自动调用 run() 方法，并且 run() 方法在分支栈的栈底部（压栈），这时 main() 方法在主栈的底部，所以 run() 方法与 main() 方法是平级的

**方式二**：编写一个类，实现 Runnable 接口并重写 run() 方法

```
public class lianxi_02
{
	public static void main(String[] args)
	{
		//创建线程对象
		MyThread mt = new MyThread();
		
		//通过线程对象创建Thread对象
		Thread t = new Thread(mt);
		
		t.start();//启动线程
		
		
	}
}

//自定义类实现Runnable接口
class MyThread implements Runnable
{
	//在自定义类中重写run()方法
	public void run()
	{
		//被线程执行的代码
		
	}
}
```

**在上述两种方式中方式二较为常用，因为方式二避免了 Java 单继承带来的局限性，适合多个相同程序的代码去处理同一个资源的情况，把线程同程序的代码、数据有效分离，较好的体现了面向对象的设计思想（低耦合、高内聚）**

```
1、返回当前正在执行的线程对象
public static Thread currentThread();

2、获取线程对象的名字
public final String getName();

3、更改线程对象的名字
public final void setName(String name);
```

**方式三**：实现 Callable 接口（JDK8 新特性）

```
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

/**
 * 实现线程的第三种方式：实现Callable接口
 * 
 * 这种方式的优点是：可以获取到线程的执行结果
 * 这种方式的缺点是：在获取线程结果时容易引起当前线程阻塞，效率较低
 */
public class Lianxi_02
{
	public static void main(String[] args)
	{
		MyThread1 mt = new MyThread1();
		
		//创建一个“未来类”对象
		FutureTask task = new FutureTask(mt);
		
		//创建线程对象
		Thread t = new Thread(task);
		
		t.start();
		
		
		try{
			
			//通过get()方法获取线程返回值
			System.out.println(task.get());
		} catch (InterruptedException e){
			e.printStackTrace();
		} catch (ExecutionException e){
			e.printStackTrace();
		}
		
		//get()方法会导致当前线程阻塞，所以此方法效率比较低
		//因为get()方法需要等线程结束后拿到线程返回值
		//所以main()方法这里的代码需要等get()方法结束才能执行，也就是要等以上线程结束后才执行
		System.out.println("结束了");
	}
}

//实现Callable接口
class MyThread1 implements Callable<String>
{
	
	//这里的call()方法就相当于run()方法
	public String call() throws Exception
	{
		String str = "hhhh";
		Thread.sleep(5000);
		System.out.println("2222");
		Thread.sleep(5000);
		System.out.println("3333");
		return str;
	}
	
}
```

### 线程的生命周期

线程的生命周期总共有五个状态：

1.  新建
2.  就绪
3.  运行
4.  阻塞
5.  死亡

![](https://img-blog.csdnimg.cn/20210119192358603.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NjU2MzIwMQ==,size_16,color_FFFFFF,t_70)

*   让当前线程进入休眠，进入 “阻塞状态”，放弃 CPU 时间片，让给其它线程使用，跟调用的对象无关，因为是静态只跟出现的位置有关，出现在哪个线程中，就使哪个线程睡眠（_注：静态方法看位置，实例方法就看对象_）

```
public static void sleep(long millis);
```

*   该方法会让当前线程出异常，从而达到中断线程的效果，可用它来唤醒睡眠的线程

```
public void interrupt();
```

*   让位方法，暂停当前正在执行的线程对象，并执行其他线程，注意：yield()方法不是阻塞方法，它是让线程从 “运行状态” 回到“就绪状态”，回到就绪状态的线程有可能再次抢到 CPU 时间片，所以有时让位效果不明显

```
public static void yield();
```

*   合理地终止（结束）一个线程的执行

```
public class ThreadTest
{
	public static void main(String[] args)
	{
		MyThread2 mt = new MyThread2();
		Thread th = new Thread(mt);

		th.start();
		
		//过5秒后
		try{
			Thread.sleep(5000);
		} catch (InterruptedException e){
			e.printStackTrace();
		}
		mt.run = false;//改变run属性，通过run的值来控制线程执行
		System.out.println("终止成功");
	}
}

class MyThread2 implements Runnable
{
	// 打一个布尔标记
	boolean run = true;

	public void run()
	{

		for (int i = 0; i < 10; i++)
		{
			if (run)
			{
				System.out.println(Thread.currentThread().getName() + "---->" + i);
				try{
					Thread.sleep(1000);
				} catch (InterruptedException e){
					e.printStackTrace();
				}
			} else//如果run属性为false就结束run()方法,意味着线程结束了
			{
				return;
			}

		}
	}
}
```

*   合并线程

```
public final void join();
```

```
在以下代码，合并线程的作用是：t1线程进入阻塞状态，t2线程执行，直到t2线程结束，t1线程才可以正常执行

public class Lianxi_02
{
	public static void main(String[] args)
	{
		Thread t1 = new Thread(new Myth1());
		t1.setName("t1");
		t1.start();
	}
}

class Myth1 implements Runnable
{
	public void run()
	{
		Thread t2 = new Thread(new Myth2());
		
		t2.setName("t2");
		//启动t2线程
		t2.start();
		
		//合并t2
		try{
			t2.join();//t1进入阻塞，t2执行
		} catch (InterruptedException e){
			
			e.printStackTrace();
		}
		
		//t1的线程代码
		for(int i = 0; i < 5; i++)
		{
			System.out.println(Thread.currentThread().getName() + "---->" + i);
		}
	}
}

class Myth2 implements Runnable
{
	public void run()
	{
		//t2的线程代码
		for(int i = 0; i < 5; i++)
		{
			System.out.println(Thread.currentThread().getName() + "---->" + i);
		}
	}
}

执行结果：
t2---->0
t2---->1
t2---->2
t2---->3
t2---->4
t1---->0
t1---->1
t1---->2
t1---->3
t1---->4
```

### 线程的优先级

*   线程默认优先级是 5
*   线程最高优先级是 10
*   线程最低优先级是 1

```
1、返回线程对象的优先级
public final int getPriority();

2、更改线程的优先级
public final void setPriority(int newPriority);
```

**线程优先级高仅仅表示线程获取到 CPU 时间片的概率高**

### 线程的调度模型

*   **抢占式调度模型**：优先级越高的线程抢到 CPU 时间片的概率就越大，Java 采用的就是抢占式调度模型
*   **均分式调度模型**：平均分配 CPU 时间片，每个线程占有的 CPU 时间片时间长度一样

### 线程安全

判断一个程序是否可能会有线程安全问题：

1.  是否是多线程环境
2.  是否有共享数据
3.  是否有多个线程操作共享数据

可以理解为：**当有多个线程同时操作同一数据对象时（线程并发），就容易导致数据状态错误的情况，这时的数据就不安全了**

以下代码体现了线程安全问题

```
/**
 * 线程安全示例：
 * 多个用户同时从同一个账户中取钱
 *
 */
public class Lianxi_02
{
	public static void main(String[] args)
	{
		//创建一个账户对象（共享数据）
		Account ac = new Account(10000);
		
		//创建两个线程对象（多线程环境）
		Thread t1 = new Thread(new User(ac, "用户1"));
		Thread t2 = new Thread(new User(ac, "用户2"));
		
		t1.start();
		t2.start();
	}
}

//账户类
class Account
{
	
	private double money;
	
	
	public Account(double money)
	{
		this.money = money;
	}
	
	public double getMoney()
	{
		return this.money;
	}
	
	public void setMoney(double money)
	{
		this.money = money;
	}
	
	//取款（操作同一账户）
	public void Withdrawal(double money)
	{
		//取之前的余额
		double before = this.money;
		//取之后的余额
		double after = before - money;
		
		//这里让线程睡眠1s，就一定会出现线程安全问题
		try{
			Thread.sleep(1000);
		} catch (InterruptedException e){
			
			e.printStackTrace();
		}
		//设置取之后的余额
		this.setMoney(after);
		
	}
	
	
}

//用户类
class User implements Runnable
{
	private Account ac;
	private String name;
	
	public User(Account ac, String name)
	{
		this.name = name;
		this.ac = ac;
	}
	public void run()
	{
		ac.Withdrawal(5000);
		System.out.println(this.name + "已取款完成，余额为" + ac.getMoney());
	}
}
```

Java 提供了线程同步机制（synchronized）用于解决线程安全问题，其思想是：把多条语句操作共享数据的代码包装成一个整体，让某个线程在执行的时候，其他线程不能执行

**线程同步实际上就是让线程不能并发了，必须排队执行**

synchronized 的三种用法：

1.  同步代码块（灵活）

```
synchronized(这里填的是想要同步的线程（也就是想要排队的线程）所共享的对象) {
	//需要同步的代码块（这部分的代码块越少程序执行效率就越高）
}
```

```
//取款（操作同一账户）
public void Withdrawal(double money)
	{
		synchronized(this) {//这里的锁对象是账户对象，在这个类中就是this
			//取之前的余额
			double before = this.getMoney();
			//取之后的余额
			double after = before - money;
			
			try{
				Thread.sleep(1000);
			} catch (InterruptedException e){
				
				e.printStackTrace();
			}
			
			//设置取之后的余额
			this.setMoney(after);
		}
			
	}
```

2.  在实例方法上使用 synchronized，表示共享对象一定是 this，且同步代码块是整个方法体（为了保护实例变量的安全），使用有局限性，但简化了代码

```
//取款（操作同一账户）
	public synchronized void Withdrawal(double money)
	{
			//取之前的余额
			double before = this.getMoney();
			//取之后的余额
			double after = before - money;
			
			try{
				Thread.sleep(1000);
			} catch (InterruptedException e){
				
				e.printStackTrace();
			}
			
			//设置取之后的余额
			this.setMoney(after);
			
	}
```

3.  在静态方法上使用 synchronized，表示锁对象是类锁（字节码文件对象），类锁永远只有一把（为了保护静态变量的安全）

注：

*   局部变量永远都不会存在线程安全问题，因为局部变量在栈中不共享，一个线程一个栈
*   实例变量在堆内存中，静态变量在方法区内存中，堆内存和方法区内存都是多线程共享的，所以可能存在线程安全问题
*   同步机制虽然可以解决数据安全问题，但其缺点在于当线程相当多时，因为每个线程都会去判断同步上的锁对象，极其耗费资源，无形中会降低程序的运行效率

**synchronized 在开发中最好不要嵌套使用，可能会导致死锁（指两个或两个以上的线程在执行的过程中，因争夺资源产生的一种相互等待现象）**，

以下代码是死锁示例

```
public class Lianxi_02
{
	public static void main(String[] args)
	{
		Object o1 = new Object();
		Object o2 = new Object();
		
		Thread t1 = new Myth1(o1, o2);
		Thread t2 = new Myth2(o1, o2);
		
		t1.start();
		t2.start();
	}
}

class Myth1 extends Thread
{
	private Object o1;
	private Object o2;
	
	public Myth1(Object o1, Object o2)
	{
		this.o1 = o1;
		this.o2 = o2;
	}
	
	public void run()
	{
		synchronized(o1) {
			try{
				Thread.sleep(1000);
			} catch (InterruptedException e){
				
				e.printStackTrace();
			}
			synchronized(o2) {
				
			}
		}
	}
}

class Myth2 extends Thread
{
	private Object o1;
	private Object o2;
	
	public Myth2(Object o1, Object o2)
	{
		this.o1 = o1;
		this.o2 = o2;
	}
	
	public void run()
	{
		synchronized(o2) {
			try{
				Thread.sleep(1000);
			} catch (InterruptedException e){
				e.printStackTrace();
			}
			synchronized(o1) {
				
			}
		}
	}
```

**解决线程安全问题的方案**：

1.  尽量使用局部变量代替实例变量和静态变量
2.  如果必须是实例变量，那么可以考虑创建多个对象，一个线程一个对象，这样实例变量的内存就不共享了
3.  如果不能使用局部变量，对象也不能创建多个，这个时候就只能选择 synchronized 同步机制了

### 守护线程

Java 语言中线程分为两大类：

1.  用户线程（如主线程 main 方法）
2.  守护线程（后台线程，如垃圾回收线程）

守护线程的特点：**一般的守护线程是一个死循环，所有的用户线程只要结束，守护线程就自动结束**

将该线程标记为守护线程或用户线程，当正在运行的线程都是守护线程时，Java 虚拟机退出。

```
java.lang.Thread中的方法

public final void setDaemon(boolean on);//true表示守护线程，false表示用户线程
```

### 定时器

定时器的作用：间隔特定的时间，执行特定的程序

```
import java.util.Date;
import java.util.Timer;
import java.util.TimerTask;

public class ThreadTest
{
	public static void main(String[] args)
	{
		//创建定时器对象
		Timer ti = new Timer();
		
		//创建定时任务对象
		TimerTask task = new MyThread();
		
		//任务第一次执行的时间
		Date firstTime = new Date();
		
		//任务task从时间date开始执行，每隔2000ms执行一次
		ti.schedule(task, firstTime, 2000);
		
	}
}


//定时任务类
class MyThread extends TimerTask
{
	//指定定时任务run()代码块
	public void run()
	{
		System.out.println("hhhh");
	}
}
```

### Object 中的 wait 方法和 notify 方法

wait() 和 notify() 不是线程对象的方法，是 Java 中任何一个 Java 对象都有的方法，因为这两个方法是 Object 类中自带的

*   wait()：让对象上活动的线程进入等待状态，并释放对象锁

```
public final void wait();
```

*   notify()：唤醒对象上等待的单个线程（若有多个线程等待，则随机选择一个线程唤醒），不释放锁

```
public final void notify();
```

*   notifyAll()：唤醒对象上等待的所有线程，不释放锁

```
public final void notifyAll();
```

注：

*   唤醒并不表示线程可以立马执行，还要抢夺 CPU 时间片
*   这些方法都与线程有关，所以一般用在锁对象上，通过锁对象来控制线程

**sleep() 与 wait() 的区别**：sleep() 只能通过线程对象调用，且必须指定睡眠时间，不释放锁。wait() 方法可以通过任意对象调用，且可指定时间，也可不指定时间，释放锁

### 获取文件绝对路径

采用以下的代码可以拿到一个文件的绝对路径，前提是文件必须在当前类路径下（在当前 src 下），这种写法无论在哪个系统上都可获得绝对路径，是通用的

```
String path = Thread.currentThread().getContextClassLoader()
.getResource("从当前类路径开始的文件路径（相对路径）").getPath();
		
//Thread.currentThread();表示获取当前线程对象
//getContextClassLoader();表示获取当前线程的类加载器对象
//getResource();获取资源，当前线程的类加载器默认从类的根路径下加载资源


直接返回流
InputStream path = Thread.currentThread().getContextClassLoader()
.getResourceAsStream("从当前类路径开始的文件路径（相对路径）");
```

资源绑定器
-----

Java.util 包下提供了一个资源绑定器，便于获取属性配置文件（.properties）中的内容，使用以下方法的前提是配置文件必须在当前类路径下，且此方法只适用于配置文件，注意：**在写路径时路径后的扩展名不能写**

```
ResourceBundle bundle = ResourceBundle.getBundle("db");//不能写成db.properties
		
String driver = bundle.getString("driver");
```

反射
--

**反射就是通过字节码文件对象把 java 类中的各种成分（变量、方法、构造方法）映射成一个个 java 对象，实际上是通过 class 对象反向获取该类的信息，即通过类的字节码文件动态的解析类**

获取 Class 对象的三种方式（在运行期间，一个类只有一个 class 对象产生）：

```
方式一：会导致类加载，类加载静态代码块执行
Class c = Class.forName("带有包名的完整类名");

方式二：会执行静态代码块
Class c = 对象.getClass();

方式三：java语言中任何一种类型，包括基本数据类型都有.class属性 不会执行静态代码块（不会静态初始化）
Class c = 任何类型.class;
```

**以下所有方法中若要获取私有成员时就在 Declared 之后调用解除私有限定（安全检查管理器）方法**

```
public void setAccessible(boolean flag);
flag为true时表示关闭检查，可调用私有
flag为false时表示打开检查，不可调用私有
```

通过 class 对象获取构造方法对象

```
java.lang.reflect.Constructor<T>

获取批量的构造方法对象
public Constructor<?>[] getConstructors();//所有公有的构造方法
public Constructor<?>[] getDeclaredConstructors();//获取所有的构造方法（包括私有、受保护、默认、公有）


获取单个指定的构造方法对象
//Class<?>... parameterTypes表示参数类型的字节码，如String.class、int.class

public Constructor<T> getConstructor(Class<?>... parameterTypes);//获取单个指定的公有构造方法
public Constructor<T> getDeclaredConstructor(Class<?>... parameterTypes);//获取单个指定不限修饰符的构造方法

创建新对象
public T newInstance(Object... initargs);//括号里的是填实际参数
```

通过 class 对象获取成员变量对象

```
java.lang.reflect.Field

获取批量的成员变量对象
public Field[] getFields();//获取公有的成员变量
public Field[] getDeclaredFields();//获取所有成员变量，包括：私有、受保护、默认、公有

通过变量名获取单个指定的成员变量对象
public Field getField(String name);//获取指定公有的成员变量
public Field getDeclaredField(String name);//获取单个指定成员变量、不限修饰符

获取变量的值，如果是私有就需要关闭安全检查
public Object get(Object obj);//括号里表示对象,返回该对象的某个变量的值

给获取的变量赋值
public void set(Object obj, Object value);//obj表示变量所在的对象，value表示要为变量赋的值
```

通过 class 对象获取成员方法对象

```
java.lang.reflect.Method

获取批量的成员方法对象
public Method[] getMethods();//获取公有的成员方法，包含了父类的公有成员方法
public Method[] getDeclaredMethods();//获取所有的成员方法，包含了私有成员方法，不包括继承的

获取单个指定成员方法对象
public Method getMethod(String name, Class<?>... parameterTypes);//获取公有的指定成员方法，name是方法名，后面填的是形参类型字节码
public Method getDeclaredMethod(String name, Class<?>... parameterTypes);//获取所有的成员方法

调用该成员方法
public Object invoke(Object obj, Object... args);//obj表示要调用方法的对象，args表示调用方法时传递的实际参数
```

```
获取类的父类对象
public Class<? super T> getSuperclass();
```

```
获取类实现的所有接口对象
public Class<?>[] getInterfaces();
```

**反射的核心是：JVM 在运行时才动态加载类或调用方法 / 访问属性，它不需要事先（写代码的时候或编译期）知道运行对象是谁**

### 反射的优点

*   可扩展性特性：应用程序可以通过使用它们的完全限定名称创建可扩展性对象的实例来使用外部的、用户定义的类。
    
*   类浏览器和可视化开发环境：类浏览器需要能够枚举类的成员。可视化开发环境可以受益于利用反射中可用的类型信息来帮助开发人员编写正确的代码。
    
*   调试器和测试工具：调试器需要能够检查类的私有成员。测试工具可以利用反射来系统地调用定义在类上的可发现集 API，以确保测试套件中的高水平代码覆盖率。
    

### 反射的缺点

*   性能开销：由于反射涉及动态解析的类型，因此无法执行某些 Java 虚拟机优化。因此，反射操作的性能比非反射操作慢，应避免在对性能敏感的应用程序中频繁调用的代码段中使用。
    
*   安全问题：反射调用方法时可以忽略权限检查，因此可能会破坏封装性而导致安全问题。
    
*   内部暴露：由于反射允许代码执行非反射代码中非法的操作，例如访问私有字段和方法，使用反射会导致意想不到的副作用，这可能会使代码功能失调并可能破坏可移植性. 反射代码打破了抽象，因此可能会随着平台的升级而改变行为。
    

注解
--

Java 注解是附加在代码中的一些元信息，用于一些工具在编译、运行时进行解析和使用，起到说明、配置的功能。注解不会也不能影响代码的实际逻辑，仅仅起到辅助性的作用。

**注解 Annotation 是一种引用数据类型，编译后生成. class 文件**

注解定义语法

```
[修饰符列表] @interface 注解类型名{
	
}
```

注解使用语法

```
@ 注解类型名
```

*   @Override 这个注解只能注解方法，这个注解是给编译器参考的，和运行阶段没有关系，凡是 java 中的方法带有这个注解的，编译器都会进行编译检查，如果这个方法不是重写父类的方法，编译器就会报错
*   **用来标注 “注解类型” 的注解称为元注解**
*   @Target 注解是一个元注解，用来标注 “被标注的注解” 可以出现在哪些位置上

```
@Target(ElementType.METHOD)//被标注的元素只能出现在方法上
@Target(ElementType.ANNOTATION_TYPE)//被标注的元素只能出现在注解类型上
@Target(ElementType.TYPE)//被标注的元素只能出现在类上
@Target(ElementType.FIELD)//被标注的元素只能出现在字段上
@Target(ElementType.PARAMETER)//被标注的元素只能出现在参数上
@Target(ElementType.CONSTRUCTOR)//被标注的元素只能出现在构造方法上
@Target(ElementType.LOCAL_VARIABLE)//被标注的元素只能出现在局部变量上
@Target(ElementType.PACKAGE)//被标注的元素只能出现在包上
@Target(ElementType. MODULE)//被标注的元素只能出现在模块上
```

*   @Retention 注解是一个元注解，用来标注 “被标注的注解” 最终保存在哪里

```
@Retention(RetentionPolicy.SOURCE)//被标注的元素只被保存在java源文件中
@Retention(RetentionPolicy.CLASS)//被标注的元素只被保存在class文件中
@Retention(RetentionPolicy.RUNTIME)//被标注的元素只被保存在class文件中，并且可以被反射机制所读取
```

*   @Deprecated 注解用来标注已过时的元素

注解中定义属性

```
属性类型 属性名();//表示该属性名只能被赋值该属性类型的数据

public @interface MyAnnotation
{
	int value();
	String name();
	String address() default "";//给address属性赋默认值，在该注解使用时可省略不写
}
```

*   如果一个注解当中有属性，那么在使用该注解时必须给该注解中的属性赋值（除非该属性使用 default 指定默认值就可省略赋值）
*   如果一个注解的属性名为 value 且只有这一个属性或其余属性有默认值时，那么在使用该注解的这个属性时，属性名（value）可以省略不写，但属性值必须要有

注解使用

```
@ 注解类型名(属性名=属性值, 属性名=属性值......)

@MyAnnotation(value = 9, name = "xxx", address = "dddd")
class Person
{
	@MyAnnotation(value = 9, name = "xxx" )//因属性address有默认值可省略
	public void run()
	{
		
	}
}
```

*   注解当中的属性可以是这些类型：byte、short、int、long、float、double、boolean、char、String、class、枚举以及以上每种类型的数组类型
*   在使用注解中数组型的属性时如果属性值只有一个值，大括号 { } 可省略不写

反射注解

```
判断这个注解是否在此类上
//括号里填注解类型的字节码，
public boolean isAnnotationPresent(Class<? extends Annotation> annotationClass);//返回true表示在此类上有此注解，false表示没有

获取该注解对象
public <A extends Annotation> A getAnnotation(Class<A> annotationClass);//返回该注解类型，可能需强转
```

面向对象思想设计原则
----------

_这些设计原则都是为了提高代码的维护性、扩展性、复用性、低耦合高内聚_

*   **单一职责原则**：“高内聚、低耦合”，功能细化，每个类应该只有一个功能，对外只提供一种功能，而引起类变化的原因应该只有一个，所有的设计模式都应该遵循这一原则
*   **开闭原则**：“一个对象对扩展开放对修改关闭”，对类的改动是通过增加代码进行的，而不是修改现有代码，借助抽象和多态，把可能变化的内容抽象出来，从而使抽象的部分是相对稳定的，而具体的实现则是可以改变和扩展的
*   **里氏替换原则**：“在任何父类出现的地方都可以用它的子类来替代”，同一个继承体系中的对象应该有共同的行为特征
*   **依赖注入原则**：“要依赖于抽象，不要依赖于具体实现”，在应用程序中，所有的类如果使用或依赖于其他的类，则应该依赖这些其他类的抽象类，而不是这些其他类的具体类，为了实现这一原则，就要我们在编程的时候针对抽象类或接口编程，而不是针对具体实现编程
*   **接口分离原则**：“不应该强迫程序依赖它们不需要使用的方法”，一个接口不需要提供太多的行为，一个接口应该只提供一种对外的功能，不应该把所有的操作都封装到一个接口中
*   **迪米特原则**：“一个对象应当对其他对象尽可能少的了解”，降低各个对象之间的耦合度，提高系统的可维护性，在模块之间应该只通过接口编程，而不理会模块的内部工作原理，它可以使各个模块耦合度降到最低，促进软件的复用

设计模式
----

*   **简单工厂模式**：又叫静态工厂方法模式，它定义一个具体的工厂负责创建一些类的实例  
    _优点_：客户端不需要负责对象的创建，从而明确了各个类的职责（功能）  
    _缺点_：这个静态工厂类负责所有对象的创建，如果有新的对象增加，或者某些对象的创建方式不同，就需要不断的修改工厂类，不利于后期的维护
*   **工厂方法模式**：工程方法模式中抽象工厂类负责定义创建对象的接口，具体对象的创建工作由继承抽象工厂的具体类实现  
    _优点_：客户端不需要负责对象的创建，从而明确了各个类的职责，如果有新的对象增加，只需要增加一个具体的类和具体的工厂类即可，不影响已有的代码，后期维护容易，增强了系统的扩展性  
    _缺点_：需要额外的编写代码，增加了工作量
*   **单例设计模式**：单例设计模式就是要确保类在内存中只有一个对象，该实例必须自动创建，并且对外提供  
    _优点_：在系统内存中只存在一个对象，因此可以节约系统资源，对于一些需要频繁创建和销毁的对象，单例模式无疑可以提高系统的性能  
    _缺点_：没有抽象层，因此扩展很难，职责过重，在一定程度上违背了单一职责原则

Java 小知识
--------

（此处归纳比较琐碎的知识点）

*   字符串中的 “+” 就是把两个字符串拼接在一起

```
System.out.println("ab" + "c" + 4 + 6);//结果是：abc46
System.out.println(4 + 6 + "abc");//结果是：10abc
```

*   java 中的真是 true，假是 false，它们都是布尔类型的，不是 C 语言中的 0 和 1
*   java 中的关键字都是小写的
*   如下代码：f1 其实是通过一个 double 类型转换过来的，可能会有精度损失，f2 本身就是一个 float 类型，不会有精度损失，所以建议采用第二种写法（在数据后面加 F\f 后缀），同样的，在定义 long 类型变量的时候要加 L 后缀，byte 和 short 没有对应的后缀，double 其实也有后缀 D\d

```
float f1 = (float)12.345;
float f2 = 12.345F;
```

*   在 java 虚拟机中，大部分的指令都不支持 byte、char、short，没有任何指令支持 boolean，编译器在编译期间或者运行期间将 byte、char、short、boolean 类型的数据扩展为相应的 int 类型数据，因此，**对于大多数 byte、char、short 和 boolean 类型数据的操作，实际上都是使用相应的 int 型作为运算类型的，但是对于 float、double 类型数据的操作还是浮点型，不是 int 型，所以不必强转**，如下代码：

```
byte b1 = 3, b2 = 4, b3;
b3 = b1 + b2;//这是错误的，应改为b3 = (byte)(b1 + b2);
b3 = 3 + 4;//这是对的，因为3和4是常量，常量运算是先把结果计算出来，然后看是否在byte的范围内（-128~+127），如果在就不报错
```

*   变量的运算结果只有在运行时才能确定，而常量运算结果在编译时就确定了
*   Java 中的 char 占 2 个字节，而单个汉字也占 2 个字节，所以 Java 中的 char 可以存储一个中文汉字
*   在 Java 语言中，像 "+= “、”-=“、”/="… 这些扩展的赋值运算符其实隐含了一个强制类型转换，例：s+=1; 不等价于 s = s+1，而是等价于 s = (s 的数据类型)(s+1);
*   位运算符是针对二进制的运算，其中位异或运算符（^）特点是：_一个数据对另一个数据位异或两次，该数据保持不变_

```
int a = 10;
int b = 20;
System.out.println(a^b^b);//10
System.out.println(a^b^a);//20
```

*   在 Java 语言中，break 不仅有跳出单层循环的功能，还有跳出多层循环的功能

```
wc : for(int i = 0; i < 3; i++)
{
	nc : for(int j = 0; j < 4; j++)
	{
		if(j == 2)
		{
			break wc;
		}
	}
}
```

*   Java 中的字面值就是 C 语言中的常量
*   对象变量（对象引用变量）并没有实际包含一个对象，它只是存储了某个对象在堆内存中的引用（地址）
*   new 操作符的返回值是一个引用
*   在一个 Java 文件中，文件名必须与 public 类的名字相同，只有一个公共类，但可以有任意数目的非公共类
*   如果可以从变量的初始值推导出它们的数据类型，那么可以用 var 关键字声明局部变量而无需指定数据类型，注意：var 关键字只适用于方法中的局部变量

```
var a = 10;
等价于
int a = 10;
```

*   调用构造器的语句只能作为另一个构造器的第一条语句出现
*   在 Java 中，只有基本数据类型不是对象，例如：数值、字符、布尔类型都不是对象
*   Java 中能直接调用系统时间并显示

```
import java.util.Date;
System.out.printf("%tc", new Date());
```

Eclipse 中常用的快捷键
---------------

*   main 方法

```
main + Alt + /
```

*   输出语句

```
syso + Alt + /
```

*   起变量名

```
Alt + /
```

*   格式化

```
Ctrl + shift + f
```

*   导包

```
Ctrl + shift + o
```

*   注释

```
单行注释：Ctrl + /
多行注释：Ctrl + shift + /
取消多行注释：Ctrl + shift + \
```

*   代码上下移动，选中代码 Alt + 上 / 下箭头
*   查看源码，选中类名（F3 或 Ctrl + 鼠标左键）
*   快速创建类的无参构造

```
Alt + shift + s + c
```

*   快速创建类的带参构造

```
Alt + shift + s + o
```

*   快速创建类属性访问方法（get/set）

```
Alt + shift + s + r
```

结语
--

以上就是我对 JavaSE 部分的大致总结了，后续会有一定补充，那经过对这部分的学习呢，其实感觉 Java 入门并不难（虽然只学了一丢丢，哈哈哈），只是它的知识体系有点复杂，需要注意的细节蛮多，只要有足够的耐心和毅力，Java 入门冒得问题的，纪念一下（2021.1.23）第一次写博客（在这方面需要学习的东西还有很多），加加油！最后感谢大家的浏览，蟹蟹。