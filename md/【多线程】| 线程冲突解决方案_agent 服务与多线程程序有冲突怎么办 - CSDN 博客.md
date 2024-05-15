> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/m0_58847451/article/details/130787852?utm_medium=distribute.pc_relevant.none-task-blog-2~default~baidujs_utm_term~default-1-130787852-blog-109064962.235^v43^pc_blog_bottom_relevance_base9&spm=1001.2101.3001.4242.1&utm_relevant_index=4)

#### 目录

*   [🦁 线程同步](#__1)
*   *   [1. 什么是线程冲突？](#1_3)
    *   [2. 什么是线程同步？](#2_15)
    *   [3. 解决线程同步的方案](#3_23)
    *   *   [3.1 语法结构](#31_29)
        *   [3.2synchronized 使用](#32synchronized_41)
*   [🦁 synchronized 详细用法](#_synchronized_66)
*   *   [1. 使用 this 作为线程锁对象](#1_this_70)
    *   *   [1.1 语法结构：](#11__74)
        *   [1.2 使用说明](#12__92)
    *   [2. 使用字符串作为线程对象锁](#2__180)
    *   *   [2.1 语法结构](#21__184)
        *   [2.2 使用说明](#22__194)
    *   [3. 使用 Class 作为线程对象锁](#3_Class_249)
    *   *   [3.1 语法结构](#31__259)
        *   [3.2 使用说明](#32__274)
    *   [4. 使用自定义对象作为线程对象锁](#4__382)
    *   *   [4.1 语法结构](#41__386)
        *   [4.2 使用说明](#42__396)
*   [🦁 conclusion](#_conclusion_444)

🦁 [线程同步](https://so.csdn.net/so/search?q=%E7%BA%BF%E7%A8%8B%E5%90%8C%E6%AD%A5&spm=1001.2101.3001.7020)
-------------------------------------------------------------------------------------------------------

![](https://img-blog.csdnimg.cn/89e211d5e08c4e0a890e6949a1ef0eb2.png)

### 1. 什么是线程冲突？

> **同一进程内的线程是共享同一内存空间的，所以在多个线程的进程里，线程是可以同时操作这个进程空间的数据的，这样就容易造成线程冲突的情况。**

> 举个小李子：一个房子里（代表一个进程），只有一个厕所（代表一个资源）。屋子里面有两个人 A 和 B（代表两个线程），共用这个厕所。一天 A 去上厕所了，一上就仨小时。到第三个小时的时候，B 实在忍不住了，直接就开门进去把在里面玩手机的 A 轰了出来。然后 A 就被赶出来了，嘴里骂骂咧咧……

这里说明了什么呢？？？我们前面说了进程间线程是按照[时间片](https://so.csdn.net/so/search?q=%E6%97%B6%E9%97%B4%E7%89%87&spm=1001.2101.3001.7020)轮询的方式执行的，A 执行了三个小时，换到 B，可是 A 还没有执行完成啊！！！厕所里面的数据还在运作，就被 B 给搅浑了。。。。。那怎么成（虽说 A 不厚道）！！！这就是**线程冲突**。

> 如何来解决这个问题呢？？？？（后面揭晓！）

> 只需记住：“**将并发任务转为串行任务就迎刃而解了**”

### 2. 什么是线程同步？

多个线程`访问同一个对象`，并且某些线程还想修改这个对象。 这时候，我们就需要用到 “线程同步”。 **线程同步其实就是一种等待机制，多个需要同时访问此对象的线程进入这个对象的等待池形成队列，等待前面的线程使用完毕后，下一个线程再使用。**

> 按这个说法，只要 A 能让 B 持续在厕所外面等待 A 并且即使有想冲进去的想法也奈何不了 A 的时候，是不是就解决了这个冲突？？？
> 
> 那么 A 是不是把门给锁上就好了？只要 A 还没执行完，B 就需要在外面等待 (你看，这不就是并行变串行？)。。。（现实生活不建议，缺德。。）

### 3. 解决线程同步的方案

那么在 Java 中，我们如何实现这个同步呢？？？

Java 语言提供了专门机制以解决这种冲突，有效避免了同一个数据对象被多个线程同时访问造成的这种问题。这套机制就是 **synchronized 关键字**

#### 3.1 语法结构

```
synchronized(锁对象){ 
　　 同步代码
 }
```

右三部分组成，synchronized、锁对象、{}。其中

锁对象：**决定了让哪些线程有互斥的效果。**

#### 3.2synchronized 使用

它有两种用法：

*   **要么加在方法的前面**（方法声明）
*   **要么写成一个代码块（回想 static 代码块）**

1.  方法声明：放在访问控制符 (public) 之前或之后。（不建议）

```
public  synchronized  void accessVal(int newVal);
```

2.  synchronized 块：这里还是以前面的例子为例，厕所是 A 和 B 同时操作的对象，所以`synchronized`就应该以厕所为锁对象。

```
synchronized(W.C.){
	doSomething();
}
```

> tips:
> 
> `若将一个大的方法声明为synchronized 将会大大影响效率。synchronized 块可以让我们精确地控制到具体的“成员变量”，缩小同步的范围，提高效率`。

🦁 synchronized 详细用法
--------------------

现在来看看 synchronized 锁对象还能如何定义？

### 1. 使用 this 作为线程锁对象

**在所有线程中相同对象中的 synchronized 会互斥**

#### 1.1 语法结构：

有两种：

```
synchronized(this){ 
　　  //同步代码 
　  }
```

```
public synchronized void accessVal(int newVal){

//同步代码

}
```

#### 1.2 使用说明

```
/**
 * 定义程序员类
 */
class Programmer{
  private String name;
  public Programmer(String name){
    this.name = name;
   }
  /**
   * 打开电脑
   */
   public void computer(){
     synchronized(this){
      try {
        System.out.println(this.name + " 接通电源");
        Thread.sleep(500);
        System.out.println(this.name + " 按开机按键");
        Thread.sleep(500);
        System.out.println(this.name + " 系统启动中");
        Thread.sleep(500);
        System.out.println(this.name + " 系统启动成功");
       } catch (InterruptedException e) {
        e.printStackTrace();
       }   
     }
   }
  /**
   * 编码
   */
  synchronized public void coding(){
      try {
        System.out.println(this.name + " 双击Idea");
        Thread.sleep(500);
        System.out.println(this.name + " Idea启动完毕");
        Thread.sleep(500);
        System.out.println(this.name + " 开开心心的写代码");
       } catch (InterruptedException e) {
        e.printStackTrace();
       }
     }
}


/**
 * 打开电脑的工作线程
 */
class Working1 extends Thread{
  private Programmer p;
  public Working1(Programmer p){
    this.p = p;
   }
  @Override
  public void run() {
    this.p.computer();
   }
}


/**
 * 编写代码的工作线程
 */
class Working2 extends Thread{
  private Programmer p;
  public Working2(Programmer p){
    this.p = p;
   }
  @Override
  public void run() {
    this.p.coding();
   }
}
```

```
public class TestSyncThread {
  public static void main(String[] args) {
    Programmer p = new Programmer("Lion");
    new Working1(p).start();
    new Working2(p).start();
   }
}
```

这里程序员类中如果不加 **synchronized(this)**，那么就会测试类中两个线程就会并发执行，又开电脑，又开 IDEA，这是不可能的，必须先打开电脑再打开 IDEA。加入 synchronized(this) 就代表了**当前对象如果是同一个对象，则会将并发变为串行**。

### 2. 使用字符串作为线程对象锁

**所有线程在执行 synchronized 时都会同步。**（也就是不同的对象也会进行线程互斥）

#### 2.1 语法结构

```
synchronized(“字符串”){ 
　　  //同步代码 
　  }
```

> 这里的字符串可以任意填写，空串也行。。。

#### 2.2 使用说明

我们依然引用上面的例子，在程序员类添加一个方法，如下：

```
/**
   * 去卫生间
   */
  public void wc(){
    synchronized ("t") {
      try {
        System.out.println(this.name + " 打开卫生间门");
        Thread.sleep(500);
        System.out.println(this.name + " 开始排泄");
        Thread.sleep(500);
        System.out.println(this.name + " 冲水");
        Thread.sleep(500);
        System.out.println(this.name + " 离开卫生间");
       } catch (InterruptedException e) {
        e.printStackTrace();
       }
     }
   }
}

/**
 * 去卫生间的线程
 */
class WC extends Thread{
  private Programmer p;
  public WC(Programmer p){
    this.p = p;
   }
  @Override
  public void run() {
    this.p.wc();
   }
}
```

我们在测试的时候，创建两个不同的程序员

```
public class TestSyncThread {
  public static void main(String[] args) {
    Programmer p1 = new Programmer("A");
    Programmer p2 = new Programmer("B");
    new WC(p1).start();
    new WC(p2).start();
   }
}
```

这时候他们并不会一起上厕所，而是一个上完另一个才去上。

### 3. 使用 Class 作为线程对象锁

> tips：
> 
> `此Class非彼class`！！！——> **前者是一个类，后者是 Java 的一个关键字**（有兴趣可以去查查看，没骗你哦！）
> 
> **Class 类型的对象是 Java 中的一个特殊对象，每个类在 JVM 中都有一个对应的 Class 对象，用于描述该类的结构。** 当我们使用 Class 对象作为锁时，可以保证同一时刻只有一个线程可以访问该 Class 类型对象所同步的代码块.

在所有线程中，拥有相同 Class 对象中的 synchronized 会互斥

#### 3.1 语法结构

```
// 推荐
synchronized(XX.class){ 
　　  //同步代码 
　  }
```

跟前面不一样，这里的 **synchronized** 加在**静态方法的前面**，表示它所在类以 class 模板作为线程对象锁，因为静态方法不能使用 this

```
synchronized public static void accessVal()
```

#### 3.2 使用说明

> 场景：同一部门的员工去领奖金互斥，不同部门的员工去领奖金并行。

还是复用上面的代码, 添加一个销售部门，并且都添加一个领取奖金的方法（领奖金都是一个一个领的，不会一群人同时领）和相关的线程类。

```
/**
 * 定义销售员工类
 */
class Sale{
  private String name;
  public Sale(String name){
    this.name = name;
   }
  /**
   * 领取奖金
   */
   public void money(){
      synchronized(Sale.class){
       try {
        System.out.println(Thread.currentThread().getName() + " 被领导表扬");
        Thread.sleep(500);
        System.out.println(Thread.currentThread().getName() + " 拿钱");
        Thread.sleep(500);
        System.out.println(Thread.currentThread().getName() + " 对公司表示感谢");
        Thread.sleep(500);
        System.out.println(Thread.currentThread().getName() + " 开开心心的拿钱走人");
       } catch (InterruptedException e) {
        e.printStackTrace();
       }
     }
   }
}
// 在程序员的代码里面也添加同样的方法表示领取奖金。这里使用不一样的写法
/**
   * 领取奖金
   */
   public synchronized static void money(){
       try {
        System.out.println(Thread.currentThread().getName() + " 被领导表扬");
        Thread.sleep(500);
        System.out.println(Thread.currentThread().getName() + " 拿钱");
        Thread.sleep(500);
        System.out.println(Thread.currentThread().getName() + " 对公司表示感谢");
        Thread.sleep(500);
        System.out.println(Thread.currentThread().getName() + " 开开心心的拿钱走人");
       } catch (InterruptedException e) {
        e.printStackTrace();
       }
     }
}


/**
 * 程序员领取奖金线程
 */
class ProgrammerMoney extends Thread{
  private Programmer p;
  public ProgrammerMoney(Programmer p){
    this.p = p;
   }
  @Override
  public void run() {
    this.p.money();
   }
}

/**
 * 销售部门领取奖金线程
 */
class SaleMoney extends Thread{
  private Sale p;
  public SaleMoneyThread(Sale p){
    this.p = p;
   }
  @Override
  public void run() {
    this.p.money();
   }
}
```

测试：

```
public class TestSyncThread {
  public static void main(String[] args) {
    Programmer p = new Programmer("张三");
    Programmer p1 = new Programmer("李四");
    new ProgrammerMoney(p).start();
    new ProgrammerMoney(p1).start();
    Sale s = new Sale("张晓丽");
    Sale s1 = new Sale("王晓红");
    new SaleMoney(s).start();
    new SaleMoney(s1).start();
   }
}
```

可以发现：p 和 p1 互斥，s 和 s1 互斥，但是 p 类型的对象和 s 类型的对象并发进行。

> tips:
> 
> **同一时刻只有一个线程可以运行 run() 方法中 synchronized 块中的代码**。
> 
> 需要注意的是，**在使用 Class 对象作为线程对象锁时，需要确保所有线程都使用同一个 Class 对象锁，否则无法保证同步性**。

### 4. 使用自定义对象作为线程对象锁

**在所有线程中，拥有相同自定义对象中的 synchronized 会互斥**

#### 4.1 语法结构

`只有一种结构`

```
synchronized(自定义对象){ 
　　  //同步代码 
}
```

#### 4.2 使用说明

```
public class MyClass {
    private final Object lock = new Object();

    public void myMethod() {
        synchronized (lock) {
            // 同步块中的代码
        }
    }

    public static void main(String[] args) {
        MyClass obj = new MyClass();

        Thread thread1 = new Thread(new MyThread(obj));
        Thread thread2 = new Thread(new MyThread(obj));

        thread1.start();
        thread2.start();

        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}

class MyThread implements Runnable {
    private MyClass obj;

    public MyThread(MyClass obj) {
        this.obj = obj;
    }

    public void run() {
        obj.myMethod();
    }
}
```

在上面的代码中，我们定义了一个 MyClass 类，其中包括一个 myMethod() 方法和一个 lock 对象，lock 对象作为自定义对象锁。

在 myMethod() 方法中，我们使用 synchronized 关键字来实现同步，将 lock 对象作为同步锁。在 main() 方法中，我们创建了两个线程并启动它们，这两个线程共享的锁对象是 MyClass 实例中的 lock 对象，因此在同一时刻只有一个线程可以运行 myMethod() 方法中 synchronized 块中的代码。

需要注意的是，**使用自定义对象作为线程对象锁时，需要确保所有线程都使用同一个锁对象，否则无法保证同步性。此外，为了避免出现死锁情况，同步块中的代码应该尽量简短，以免占用锁时间过长。**

🦁 conclusion
-------------

使用 synchronized 处理线程同步时，有四种锁对象类型

1.  this 关键字，代表当前对象，使用它表示在所有线程中，同一个对象执行的不同操作会发生互斥（同时打开电脑和打开 IDEA）
2.  字符串：表示不同线程在执行同一个操作时，也会发生互斥
3.  Class 类对象模板：表示使用同一对象模板的实例执行某一操作时会发生互斥，不同对象模板实例执行同一操作还是会并发。
4.  自定义对象：表示线程间共享的锁对象是同一个自定义对象时，会发生互斥。

> tips：  
> 使用 synchronized 时，最好还是写成 synchronized 块的形式，把主要互斥的代码放到 synchronized 块里，提高速率。