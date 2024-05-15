> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [blog.csdn.net](https://blog.csdn.net/weixin_40679698/article/details/127444899?spm=1001.2101.3001.6650.1&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-127444899-blog-123817625.235%5Ev43%5Epc_blog_bottom_relevance_base9&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7ERate-1-127444899-blog-123817625.235%5Ev43%5Epc_blog_bottom_relevance_base9&utm_relevant_index=2)

作者想要实际测试一下深度学习的效果，在买带 GPU 的电脑还是用[云服务](https://so.csdn.net/so/search?q=%E4%BA%91%E6%9C%8D%E5%8A%A1&spm=1001.2101.3001.7020)之间果断选择后者。一个是目前只是想浅浅尝试一下，短期使用还是比买一台电脑划算；一个是念书时习惯了超算的便利，包括天河、曙光、学校以及各实习单位的大型机。AWS 是全球最大的云服务器供应商，所以直接选择它了，当然也可以选用国内外其它的平台（可能会有更适合的平台，不在介绍范围内）。

本文详细记录了 **“AWS 注册 --> 配额申请 --> 实例创建 --> 固定 IP 绑定 --> 自动定时关闭设置 --> 登陆 -->VScode 远程连接”** 的整个流程，供有需要的小伙伴参考。

### 1 注册 AWS 账户

这个过程参考 clarmy 的文章[《手把手教你在 AWS 上搭一个属于自己的博客网站》](https://mp.weixin.qq.com/s/Oa1W7Dv02i1X89SiDzecEA)。同时熟悉一下实例的概念，以及创建实例的过程。

### 2 创建 AWS instance（实例）

#### 2.1 p2 实例的配额申请

考虑到深度学习很多时候需要 GPU，推荐使用 p2.xlarge 实例（不同实例的说明参考[这里](https://aws.amazon.com/cn/ec2/instance-types/)，P2 实例适用于通用 GPU 计算应用程序），收费跟区域有关，这里我选择的是 us-west-2 区域，每小时 0.98$（可以闲鱼上搜一下 [aws](https://so.csdn.net/so/search?q=aws&spm=1001.2101.3001.7020) 礼卡优惠券或者账号之类）。

为什么选 us-west-2 区域呢？因为不是每个区域都可以创建 p2 实例的，而且后续需要使用固定 IP 的时候，不是所有区域都支持这项服务，因此需要提前查好。

账户默认是没有 p2 实例的配额的，配额查询点[这里](https://docs.aws.amazon.com/zh_cn/general/latest/gr/aws_service_limits.html?id=docs_gateway)。

按照[教程](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-on-demand-instances.html#vcpu-limits-request-increase)进行配额申请：

1.  进入 aws support 的 create case 界面；
    
2.  选择 service limit increase, 填写表单，
    
3.  表单内容示例如下： ![](https://img-blog.csdnimg.cn/img_convert/e94cb834df7560417dff5ed63c5e5af0.png)
    

我填写的 case description 如下图，可以参考。不过最后要再加一段，Since p2.xlarge is equipped with 4 vCPUs and 1 GPU，I may need all the resources approved, that is, increase the vCPU limit to 4. 不然像我的就是给开了 p2 但是 vCPU 的限额是 1，还是无法开启 4 个 CPU 的实例。这个过程不太快，有邮件联系之后要及时回复询问进展。 ![](https://img-blog.csdnimg.cn/img_convert/06dfac318ca89997852fd2fb793b936d.png)

#### 2.2 创建 p2 实例

*   配额申请成功之后，选择 EC2，创建实例，AMI 选择时搜索 deep learnig，选 pytorch ubuntu 的即可。这个镜像直接安装好了所需的一些基本软件，python、conda、cuda、pytorch 等等。 ![](https://img-blog.csdnimg.cn/img_convert/93f1b17a76c940319e1269cb99be6bfa.png) ![](https://img-blog.csdnimg.cn/img_convert/2db9f57323d93055e4f34a2d7bcb4643.png)
    
*   实例选择 p2.xlarge；然后生成一个密钥，要注意保存好，后面登陆的时候要用。 ![](https://img-blog.csdnimg.cn/img_convert/bd00a74559998136889d34c2ad7fcb26.png)
    
*   网络设置这里放开 80 端口的防火墙，这样浏览器才能访问我们的网站，具体操作是点击下方的 “add security group rule”，然后在新的配置框中把“端口范围” 设为 80。 ![](https://img-blog.csdnimg.cn/img_convert/385c8b478585612d6845c5f98af5ddcd.png)
    
*   存储大小可以自己设置，有 30G 免费容量。
    
*   在右侧边的 summary 中确认一下信息，点 lauch instance 即可。
    
*   返回控制台，可以发现有一个实例，勾选之后，可以查看详情，其中公网 IP 就是我们登陆服务器时需要使用的 IP 地址。 ![](https://img-blog.csdnimg.cn/img_convert/7f743ee1fb4af1d4d16f95c995c8d121.png) 但这个公网 IP 是动态的，每次关闭了重开就会变化，比较麻烦。所以下一小节介绍 Elastic IP address 的申请，并将其分配到这个实例上。
    

#### 2.3 [固定 IP 地址关联](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/elastic-ip-addresses-eip.html#working-with-eips)

EC2 窗口中选择 Elastic IP，点右上角 allocate elastic IP address，创建好之后选择分配好的地址，在右上角 Actions 里面选择 Associate Elastic IP address，选择刚才创建的 instance 就好。 ![](https://img-blog.csdnimg.cn/img_convert/b38f161599f942bab9d4239de8a9645c.png) ![](https://img-blog.csdnimg.cn/img_convert/f57051ed964f1d569b5ef1445806166e.png) 回到实例的界面，会看到公网地址变成这个固定的 IP 地址。

### 3 登陆服务器

选中实例，右击 connect，找到合适的登陆方式。 ![](https://img-blog.csdnimg.cn/img_convert/6f95b56fcc73904ebef74d36ac2b3410.png) ![](https://img-blog.csdnimg.cn/img_convert/c0c93bcd2716f09fa163f7de850d50e8.png) 其中 ssh 登陆的方法总是：找到密钥的位置，修改权限，输入`ssh -i test.pem ubuntu@你自己的公网IP）`即可。默认用户名是 ubuntu。

不熟悉 linux 的朋友在登陆这块还是可以参考 [clarmy 的文章](https://mp.weixin.qq.com/s/Oa1W7Dv02i1X89SiDzecEA)。

### 4 设置自动定时关闭以免经费燃烧🔥

这一节介绍实例的每日定时关闭操作，如果每次都能记得关闭，不需要可以直接跳过第四节，记性不好如我，就需要这个功能。

#### 4.1 [为 Lambda 函数创建 IAM policy 和执行角色](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create-console.html#access_policies_create-json-editor)

*   搜索 lambda，点击右上角的 create policy，点进去之后选 jason，把下面这段话复制粘贴进去，然后一直选 next，review 的时候起一个名字之后点击 create policy 即可。
    

```
{ "Version": "2012-10-17", "Statement": [ { "Effect": "Allow", "Action": [ "logs:CreateLogGroup", "logs:CreateLogStream", "logs:PutLogEvents" ], "Resource": "arn:aws:logs:*:*:*" }, { "Effect": "Allow", "Action": [ "ec2:Start*", "ec2:Stop*" ], "Resource": "*" } ] }
```

![](https://img-blog.csdnimg.cn/img_convert/6ce57de746671e9075abcaebea9e6ff1.png)

*   为 Lambda 创建 IAM 角色。 搜索 roles，选择 create roles， 在 trusted entity type 下选择 aws service，use case 下选择 lambda，点击下一步 ![](https://img-blog.csdnimg.cn/img_convert/f3e77f131f6a80b56c00d19b568bfe8a.png) 选择刚才创建的 policy，点击下一步，role name 自己取一个名称，我这里叫 xiaowu_scheduler，点击 create roles，就可以看到名为 xiaowu_scheduler 的角色了。
    

#### 4.2 创建关闭 EC2 实例的 Lambda 函数

*   搜索 lamba，点击右上角 create function，选择 author from scratch（从头开始创作），自己确定一个函数名称，如 "StopEC2Instances"，Runtime 选择 python 3.9， permission 下面展开更改原定设置执行角色，选择使用现有角色，选择刚刚创建的 IAM 角色。 ![](https://img-blog.csdnimg.cn/img_convert/d0868581d43eaffa637e22aa9fe5149a.png)
    
*   选择创建函数，在 code 的 code source 下粘贴如下函数，要把区域和实例 id 改成自己的，点击 deploy。
    

```
import boto3 region = 'us-west-2' instances = ['i-12345cb6de4f78g9h', 'i-08ce9b2d7eccf6d26'] ec2 = boto3.client('ec2', region_name=region) def lambda_handler(event, context):   ec2.stop_instances(InstanceIds=instances)   print('stopped your instances: ' + str(instances))
```

![](https://img-blog.csdnimg.cn/img_convert/c4c89f8296dfd94ef8e7a93290a5fe76.png)

*   在 lamda 的 function 下选择刚创建的函数并点击 test，可以看到 log 记录，也可以查看实例是否被关闭，从而判断是否执行成功。 ![](https://img-blog.csdnimg.cn/img_convert/5282ffd17d4207589371cb5c5cacbd26.png)
    

#### 4.3 创建触发 Lambda 函数的 EventBridge 规则

*   搜索 EventBridge，点击 create rule，选择固定时间执行，我这里想要每天北京时 20 时进行关闭，换算成 UTC 时间要 - 8 小时。 ![](https://img-blog.csdnimg.cn/img_convert/70e2832a09d04ee85e556ba6f5803075.png) 之后一路选择 next，target 下选择 aws service，select a target 选择刚才创建的 lambda 函数，create 之后就大功告成，每天晚 8 点就会自动关闭实例了。
    

### 5 VSCode 远程连接服务器

VSCode 真是无敌好用的编辑器，也支持 jupyter notebook 和 terminal 的调试。 我这里网上搜了一个 [vscode 远程连接服务器写 Jupyter Notebook 的教程](https://www.jianshu.com/p/e8f377f498df)供大家参考。我这里也简述一下：在左边 remote explorer 点 ssh 那里左上角的加号，在弹出来的 ssh command 里面输入`ssh ubuntu@你的公网IP`, 右下角弹出的 edit config file 那里点确定，之后修改一下 config file，把 pem 文件加进去，就可以正常连接啦。