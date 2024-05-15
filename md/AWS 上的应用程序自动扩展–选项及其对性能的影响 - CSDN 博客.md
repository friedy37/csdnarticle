> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/dnc8371/article/details/106701341?spm=1001.2101.3001.6650.2&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-2-106701341-blog-132447717.235%5Ev43%5Epc_blog_bottom_relevance_base9&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-2-106701341-blog-132447717.235%5Ev43%5Epc_blog_bottom_relevance_base9&utm_relevant_index=3)

扩展软件应用程序是至关重要的，以避免由于网站的客户群或需要处理大量[数据集](https://so.csdn.net/so/search?q=%E6%95%B0%E6%8D%AE%E9%9B%86&spm=1001.2101.3001.7020)的应用程序等增加而导致工作负载增加的性能瓶颈。云服务提供商通常是访问其他应用程序的最佳方法随需应变的资源，可根据应用程序的负载变化来扩大或缩小。

### 1. 什么是可伸缩性？

可伸缩性是解决方案可以通过添加计算和存储资源的一种有能力的方式来处理增加的工作负载或事务的特性。 如果您当前的解决方案可同时支持 100 万用户，那么具有高度可扩展性的软件将通过添加额外的资源而对数十亿用户有效。 为了处理更多负载，有两种类型的缩放比例：垂直缩放比例和水平缩放比例

#### 1.1 垂直缩放（或向上缩放）

在这种类型的扩展中，您将添加更多具有更高容量的高级硬件，例如更多的 RAM，强大的处理器等，以增加应用程序的负载。 垂直扩展的问题在于，容量可以增长多少始终受到限制。 由于硬件成本，这种类型的缩放非常昂贵，并且花费时间来获得新的硬件。 如果要快速扩展应用程序以增加负载，则这种扩展类型不是一个好选择。

#### 1.2 水平缩放（或横向扩展）

在这种类型的扩展中，可以将更多服务器添加到现有容量中，以增加应用程序的负载。 应用程序增加的负载通过负载均衡器分布在群集中的所有服务器上。 如果您想快速增长软件并且成本不高，则这种类型的扩展是最佳选择。

通过配置更改即可轻松扩展 Cloud Environments 中的应用程序，配置更改会根据性能监控指标自动将其他服务器添加到群集中。

通过配置更改即可轻松扩展 Cloud Environments 中的应用程序，配置更改会根据性能监控指标自动将其他服务器添加到群集中。 在本文中，我们将讨论可用于在 [AWS](https://so.csdn.net/so/search?q=AWS&spm=1001.2101.3001.7020) Cloud Environment 中自动缩放 AWS EC2 Auto Scaling 组的不同 Autoscaling 选项。

### 2. 什么是自动缩放？

自动缩放是云计算环境中的一项功能，当使用情况指标达到配置的阈值时，该功能会自动从实例群集中添加或删除虚拟机等计算资源。 自动缩放或动态缩放功能可确保将新的计算资源无缝地添加到群集中，以满足需求峰值，并在需求下降时终止实例。

![](http://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamF2YWNvZGVnZWVrcy5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMTkvMDIvQXV0by1zY2FsaW5nLnBuZw?x-oss-process=image/format,png) AWS 自动扩展

### 3. 为什么需要自动缩放？

无论应用程序上的负载如何，自动缩放都有助于获得更好和一致的性能。 自动缩放还可以通过在需求减少时自动终止资源来帮助降低成本。

通过自动缩放，您可以配置在满足需求阈值时要添加或删除的服务器数量。 另外，您可以配置可以添加到群集的最大服务器数量。 不应将任何数据存储在属于 Autoscaling 组的实例上，而是将数据持久保存到分布式存储系统中。

### 4. 自动缩放组件

请遵循[此处](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg-ec2-wizard.html)概述的步骤[，](https://docs.aws.amazon.com/autoscaling/ec2/userguide/create-asg-ec2-wizard.html)以便从 AWS 控制台创建 Autoscaling 组。 以下是自动缩放的主要组成部分。

**_EC2 实例_** ：EC2 是 Amazon Web Services（AWS）云环境中用于运行应用程序的虚拟服务器。 EC2 实例是从 AMI（Amazon Machine Images）创建的。

**_Auto Scaling 组（ASG）_ ：** ASG 是具有相似特征的 EC2 实例的集合，并且是从同一 AMI 创建的。 使用自动缩放功能，可以根据负载动态添加或从自动缩放组中删除实例。 Autoscaling 组通过执行定期的运行状况检查来维护所需的实例数。 如果发现任何不正常的实例，ASG 会终止该不正常的实例并启动新实例。

**_启动配置_** ：启动配置是 ASG 用于启动 EC2 实例的模板。 在[启动配置中，](https://docs.aws.amazon.com/autoscaling/ec2/userguide/LaunchConfiguration.html)您需要指定 AMI Id，实例类型，密钥对，安全组等。您可以使用相同的启动配置来创建多个自动伸缩组。

**_伸缩标准_ ：**伸缩标准配置指示 ASG 有关何时以及如何伸缩。

### 5. AWS 上不同类型的 Auto Scaling？

以下是 AWS 云环境上可用的三种不同类型的自动扩展选项：

#### 5.1 反应式自动缩放

在 “ _反应式缩放” 中_ ，您定义缩放标准以根据需求的变化进行缩放。 根据平均 CPU 消耗或 EC2 实例的内存使用情况（基于 [Cloud Watch](https://aws.amazon.com/cloudwatch/) 指标）等，对 Auto Scaling 组（ASG）中的 Amazon EC2 实例进行缩放。例如，如果您不希望 ASG 的 CPU 使用率超过 80％，您可以设置缩放标准以在达到此阈值时自动缩放。 当达到配置的阈值时，将添加新的 EC2 实例或从 ASG 中删除现有的 EC2 实例。

#### 5.2 主动自动缩放

主动式自动伸缩是一种机制，它基于对 ASG 流量周期性峰值的历史观察，调度 EC2 实例以实现可预测的负载变化。 例如，如果您的视频应用在黄金时段（例如 6pm – 9 pm）使用率较高，则可以安排自动缩放以在 6 pm 之前添加其他实例，并在 9 pm 之后终止其他实例。

要创建主动式自动伸缩组，您需要创建一个计划操作，该操作应在该操作应生效的开始时间，最小，最大和所需容量上进行。 计划操作告诉 ASG 在指定时间执行横向扩展或纵向扩展操作。

请按照[以下](https://docs.aws.amazon.com/autoscaling/ec2/userguide/schedule_time.html)步骤创建主动或计划自动缩放。

#### 5.3 预测性自动缩放

在 AWS re：Invent 2018 即将发布之前，AWS 推出了 AWS EC2 最受期待的功能 _[Predictive Scaling](https://aws.amazon.com/about-aws/whats-new/2018/11/introducing-predictive-scaling-for-amazon-EC2-in-aws-auto-scaling/) 。_ 借助 Predictive Scaling EC2 实例，可以在流量变化之前扩展容量。

预测性自动缩放基于训练有素的机器学习（ML）算法，该算法可与时间序列数据一起使用。 这款经过训练的 ML 算法根据实际 EC2 使用情况中的数据以及从 AWS 观察中得出的数十亿个数据点，预测预期的流量和 EC2 使用情况。 该模型至少需要一天的历史数据才能开始进行预测； 每 24 小时进行一次重新评估，以创建下一个 48 小时的预测。 ML 模型随着从 Autoscaling 组生成的实际使用情况数据中学习而变得越来越好。

只需单击即可启用预测性自动缩放。 通过主动扩展，可以避免 EC2 资源的过度配置，这将减少 EC2 成本。 可以按预测比例设置缓冲区，因此新启动的实例可以在准备好在预测时间处理流量之前进行预热。 使用预测缩放功能没有任何成本。 预测性自动缩放有助于优化 EC2 成本，非常适合负载峰值为周期性的应用。

配置预测伸缩计划：

![](http://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamF2YWNvZGVnZWVrcy5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMTkvMDIvUHJlZGljdGl2ZS1TY2FsaW5nLVNpemVkLnBuZw?x-oss-process=image/format,png) 预测缩放配置  
来源： [AWS Blog](https://aws.amazon.com/blogs/aws/new-predictive-scaling-for-ec2-powered-by-machine-learning/)

您可以同时使用预测缩放和动态缩放。 预测性伸缩有助于进行预测，而动态伸缩则有助于基于云监视指标进行横向扩展。 您可以根据预先填充的指标或自定义指标进行预测。

基于 CPU 使用率指标的样本预测。  

![](http://imgconvert.csdnimg.cn/aHR0cHM6Ly93d3cuamF2YWNvZGVnZWVrcy5jb20vd3AtY29udGVudC91cGxvYWRzLzIwMTkvMDIvQ1BVLVByZWRpY3Rpb24tUmVzaXplZC5wbmc?x-oss-process=image/format,png) 预测扩展：CPU 利用率  
来源： [AWS Blog](https://aws.amazon.com/blogs/aws/new-predictive-scaling-for-ec2-powered-by-machine-learning/)

**注意** ：在_美国东部（弗吉尼亚北部），美国东部（俄亥俄州），美国西部（俄勒冈），欧洲（爱尔兰）和亚太地区（新加坡）_地区可以使用预测性自动缩放

### 6. 总结

自动缩放是一项强大的功能，可以在应用程序负载变化时解决应用程序中的性能瓶颈。 当对应用程序的需求较少时，通过终止 Autoscaling 组中的实例，这也有助于节省成本。 预测性自动缩放功能可通过利用历史车队使用度量标准来帮助预测前方的负载并相应地缩放车队，而无需人工干预。

> 翻译自: [https://www.javacodegeeks.com/2019/02/application-auto-scaling-on-aws-options-and-impact-on-performance.html](https://www.javacodegeeks.com/2019/02/application-auto-scaling-on-aws-options-and-impact-on-performance.html)