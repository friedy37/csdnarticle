> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/kingtok/article/details/104744671?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-104744671-blog-129628250.235%5Ev43%5Epc_blog_bottom_relevance_base9&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-104744671-blog-129628250.235%5Ev43%5Epc_blog_bottom_relevance_base9&utm_relevant_index=1)

#### AWS Auto Scaling

*   *   *   [一. 什么是 AWS Auto Scaling](#_AWS_Auto_Scaling_2)
        *   [二. 工作原理图](#__7)
        *   [三. Auto Scaling 的优势](#__Auto_Scaling_9)
        *   [四. Auto Scaling 的关键组件](#_Auto_Scaling__22)
        *   [五. Auto Scaling 启动配置](#_Auto_Scaling__41)
        *   *   [1. 从现有 EC2 实例去启动](#1_EC2_42)
            *   [2. 从公有的 EC2 实例去启动](#2_EC2_49)
        *   [六. 启动 AutoScaling](#_AutoScaling_64)
        *   [制作不易, 转载请标注~~](#_89)

#### 一. 什么是 AWS Auto Scaling

*   **AWS Auto Scaling** 可以监控您的应用程序并自动调整容量，从而以尽可能低的成本来保持稳定、可预测的性能。使用 AWS Auto Scaling，您可以在几分钟内为多项服务中的多个资源轻松设置应用程序扩展。该服务可以提供一个简单而功能强大的用户界面，让您可以为 **Amazon EC2 实例**和 **Spot 队列**、**Amazon ECS 任务**、**Amazon DynamoDB 表**和**索引**以及 **Amazon Aurora 副本等资源**制定扩展计划。AWS Auto Scaling 可以提供建议，让您能够优化性能、成本或实现二者的平衡，从而使扩展变得简单。如果您已经在使用 Amazon EC2 Auto Scaling 来**动态扩展** Amazon EC2 实例，那么现在可以将其与 AWS Auto Scaling 结合使用，为其他 AWS 服务扩展其他资源。有了 AWS Auto Scaling，您的应用程序就始终能在合适的时间获得合适的资源。
    
*   您可以通过 AWS 管理控制台、命令行界面 (CLI) 或软件开发工具包轻松开始使用 AWS Auto Scaling。使用 AWS Auto Scaling 不会产生额外费用。您仅需支付运行应用程序所需的 AWS 资源费用和 Amazon CloudWatch 监控费用。
    

#### 二. 工作[原理图](https://so.csdn.net/so/search?q=%E5%8E%9F%E7%90%86%E5%9B%BE&spm=1001.2101.3001.7020)

![](https://img-blog.csdnimg.cn/20200309005822575.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)

#### 三. Auto Scaling 的优势

*   **提高容错能力**  
    Auto Scaling 可以检测到实例何时运行状况不佳并终止实例，然后启动新实例以替换它。  
    您还可以配置 Auto Scaling 以使用多个可用区。如果一个可用区变得不可用，则 Auto  
    Scaling 可以在另一个可用区中启动实例以进行弥补。
    
*   **提高可用性**  
    Auto Scaling 组可帮助确保应用程序始终拥有合适的容量以满足当前流量需求。
    
*   **加强成本管理**  
    Auto Scaling 可以按需要动态地增加或降低容量。您只需为使用的 EC2 实例付费，在实际  
    需要的时候启动实例，在不需要的时候终止实例，从而节约成本。
    

#### 四. Auto Scaling 的关键组件

*   **组**  
    您的 EC2 实例整理到组 中，从而当作一个逻辑单位进行扩展和管理。当  
    您创建一个组时，您可以指定其中 EC2 实例的最小数量、最大数量以及  
    所需数量。
    
*   **启动配置**  
    组使用启动配置 作为其 EC2 实例的模板。创建启动配置时，您可以为实  
    例指定诸如 AMI ID、实例类型、密钥对、安全组和块储存设备映射等信  
    息。
    
*   **扩展计划**  
    扩展计划 告知 Auto Scaling 进行扩展的时间和方式。例如，您可以根据  
    指定条件的发生（动态扩展）或根据时间表来制定扩展计划。
    

![](https://img-blog.csdnimg.cn/20200309010425138.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**使用自动扩容技术可为我们更精确计算产品设施投入, 使我们不用去关心容量问题**

#### 五. Auto Scaling 启动配置

##### 1. 从现有 EC2 实例去启动

**打开 EC2 实例面板右键选中**  
![](https://img-blog.csdnimg.cn/20200309010944912.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**选择新的组**  
![](https://img-blog.csdnimg.cn/20200309011532504.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**这样基于 EC2 的启动配置就完成了**

##### 2. 从公有的 EC2 实例去启动

**选择创建一个新的启动配置**  
![](https://img-blog.csdnimg.cn/20200309011843762.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**选择下一步**  
![](https://img-blog.csdnimg.cn/20200309011955393.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**设置名称**  
![](https://img-blog.csdnimg.cn/20200309012032139.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**设置存储, 添加一个 4g 的卷**  
![](https://img-blog.csdnimg.cn/20200309012122715.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**配置安全组, 默认先不用配置**  
![](https://img-blog.csdnimg.cn/2020030901222619.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**选择密钥对**  
![](https://img-blog.csdnimg.cn/20200309012335193.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**配置创建成功**  
![](https://img-blog.csdnimg.cn/20200309012407998.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)

#### 六. 启动 AutoScaling

演示一个最基本的 Demo 案例来实现

**1. 创建 AutoScaling 组**  
![](https://img-blog.csdnimg.cn/20200309012826223.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**2. 选择启动配置, 点击下一步**  
![](https://img-blog.csdnimg.cn/20200309012946398.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**3. 创建 Auto Scaling 组**  
![](https://img-blog.csdnimg.cn/20200309013231310.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
**4. 创建案例策略**

*   创建警报, 实现在 CPU 平均阈值 >=70% 持续 1 分钟时增加组的大小, 之后选择添加一个实例  
    ![](https://img-blog.csdnimg.cn/20200309015033328.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)
*   创建减少实例警报 Demo, 当 CPU 利用率 <=10% 持续 1 分钟时减少一个实例  
    ![](https://img-blog.csdnimg.cn/20200309015429306.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
    **5. 审核配置**  
    ![](https://img-blog.csdnimg.cn/2020030901560523.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
    **6. 查看创建好的实例**  
    ![](https://img-blog.csdnimg.cn/20200309015848476.png)  
    **7. 当 cpu 使用率 <=10% 时持续 1 分钟实例就会自动关闭**  
    ![](https://img-blog.csdnimg.cn/20200309020352910.png)  
    **8. 也可选手动扩展, 点击编辑保存即可扩展**  
    ![](https://img-blog.csdnimg.cn/20200309020551419.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)  
    **9. 计划扩展, 可以按照需要进行周期性的扩展**  
    ![](https://img-blog.csdnimg.cn/20200309020726683.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2tpbmd0b2s=,size_16,color_FFFFFF,t_70)

#### 制作不易, 转载请标注~~