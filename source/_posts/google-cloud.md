---
title: 利用谷歌云免费搭建你想要的服务
date: 2018-01-04
tags:
- 工具
- Google
- 网络
- 科学上网
categories: 技术栈
thumbnail: https://meto.chinakook.com/blog-images/180104%E9%A2%98%E5%9B%BE.jpeg
---

由于众所周知的原因，在国内不能够在网络上自由的浏览信息，但是有没有解决方法呢？<!--more-->肯定是没有啊，身处国门之内，要学会遵守规则不要踩踏红线。

明确说明，**这篇文章只是教给大家如何利用谷歌云「学习」搭建一个免费的服务器，学习搭建服务**这个技术。至于利用谷歌云做什么，与本文及本人无关。

要想利用谷歌云搭建服务有两个前提条件：

1. 拥有其中一张信用卡：Visa、MasterCard、JCB；
2. 有一个可以临时「自由访问」的网络。

这两个条件都是硬性条件，缺一不可。信用卡，可以在某宝淘，临时注册用，也就 20 来块，不易搜索，大家用心寻找应该能找到，需要提醒的是：超过 20 块的不要买，更高价格就更不用说了，完全可以找到 20 以下的，某宝还是有不良商家的；临时「自由访问」网络，这个在“百毒”上可以搜索到，比如那个带颜色的灯，可以免费使用，如果实在找不到，那就再找找。

首先，要拥有一个谷歌账户，只要可以「自由访问」网络便可注册，这里就不赘述了，谷歌全家桶都使用这一个账户登录，谷歌云也不例外。

打开谷歌云：[https://cloud.google.com/](https://cloud.google.com/)，登录你的谷歌账户然后点击免费试用。

<center>![](https://meto.chinakook.com/blog-images/0.jpeg)</center>

然后如下所示：

<center>![](https://meto.chinakook.com/blog-images/1.jpeg)</center>

地区请选择**美国**，当然任性选择中国我也没辙，只是有什么问题就自己受着吧。继续之后出现如下信息：

<center>![](https://meto.chinakook.com/blog-images/2.jpeg)</center>

账号选择个人，然后填写「名称和地址」，不知道怎么填？我教你。在浏览器打开：[http://t.cn/Rt85282](http://t.cn/Rt85282)，会随机生成一个美国公民的身份，然后按照提示填写即可。需要注意的是，如果有去广告插件先把该站点加入白名单。随机生成的身份如下：

<center>![](https://meto.chinakook.com/blog-images/3.jpeg)</center>

不要填写图中的信息，自己去生成。

然后填写「付款方式」中的「信用卡卡号」，当然是填写淘到的卡号了。如果自己有支持的信用卡的话，直接用就可以了，就是直接填写自己的信用卡卡号，不会扣费，到期之后也不会。谷歌不会这么干，某些公司会，你懂！！！

<center>![](https://meto.chinakook.com/blog-images/4.png)</center>

如果你是在某宝上买的虚拟信用卡，「持卡人姓名」填写上面生成的名字即可。如果你是使用自己的信用卡，请填写自己的姓名。

然后点击开始免费试用，再进入「我的控制台」，会创建一个默认项目，项目名称是自己生成的，不用我们管，创建之后如下：

<center>![](https://meto.chinakook.com/blog-images/05.jpeg)</center>

点击左上角按钮，然后点击「结算」查看谷歌赠送给的 $300 是否到位了。

<center>![](https://meto.chinakook.com/blog-images/6.jpeg)</center>

我的用过了，所以是这样的，刚注册会显示剩余的赠金：$300，剩余天数：365。

然后点击：计算 - Compute Engine - VM 实例 - 创建实例。如下：

<center>![](https://meto.chinakook.com/blog-images/7.png)</center>


<center>![](https://meto.chinakook.com/blog-images/8.png)</center>

按照下图中标注的信息填写，其他默认即可。

<center>![](https://meto.chinakook.com/blog-images/9.jpeg)</center>

正在创建：

<center>![](https://meto.chinakook.com/blog-images/10.png)</center>

创建完成：

<center>![](https://meto.chinakook.com/blog-images/11.png)</center>

创建完成之后，「外部 IP」就是服务器的地址，我这里不适合给你们看。因为我之前创建过一个实例，所以会显示两个，大家如果第一次，肯定是一个。

然后去测试一下实例的速度如何，当然也可以不测试，基本是没问题的。测试地址：[http://t.cn/Ry2GtDf](http://t.cn/Ry2GtDf)。下图中框起来的地方，大家选择离自己所在地最近的即可。

<center>![](https://meto.chinakook.com/blog-images/12.jpeg)</center>

可见速度杠杠的，只要均在 100 毫秒之内，说明就没问题，如果超出就删除这个实例，重新建一个实例试试。

配置服务器，这一步非常关键，非常关键，非常关键。务必仔细操作。

首先，连接 SSH 服务器，如下所示：

<center>![](https://meto.chinakook.com/blog-images/13.png)</center>

<center>![](https://meto.chinakook.com/blog-images/14.png)</center>

之后提到的所有关于代码的部分均在类似下图窗口中输入：

<center>![](https://meto.chinakook.com/blog-images/15.jpeg)</center>

1.输入：sudo -i（注意，sudo 之后有个空格），回车。

2.输入下列代码（注意，这里的代码为一行，中间切不可有回车）：

```
wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/YankeeBBR/master/bbr.sh && bash bbr.sh install
```

输入之后回车。然后耐心等待，直到出现第三步中的窗口。

3.出现如下窗口：

<center>![](https://meto.chinakook.com/blog-images/16.jpeg)</center>

按键盘上的 **Tab** 键，选择 <No>，然后会跳回刚才的窗口：

<center>![](https://meto.chinakook.com/blog-images/17.png)</center>

然后输入 **y**，回车。可以等待重启，或者直接关闭该窗口，重新打开，不记得怎么打开就往上翻。

4.输入：sudo -i（和第一步一样）

5.输入：bash bbr.sh start

6.输入以下代码（注意，代码中间没有回车）：

```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh && chmod +x shadowsocksR.sh
```

7.输入：./shadowsocksR.sh

出现下图所示内容，则证明上面的工作成功。

<center>![](https://meto.chinakook.com/blog-images/18.png)</center>

8.设置密码和端口。在上面所示窗口中输入密码，随便，自己记住就可以，回车；然后会提示输入端口，也是随便，只要在 1-65535 之间就行，我设置的是 789。

9.设置完密码和端口，会提示输入编码方式、混淆方式等，这里直接默认就好，一路回车。如下图所示（图中有提示，认真看）：

<center>![](https://meto.chinakook.com/blog-images/019.png)</center>

10.在上一步骤回车之后，大约需要等待 5、6 分钟，这个过程是在配置服务器，耐心等待就好，千万不要关闭窗口，更不要关闭浏览器，更更不能关闭电脑，马上就完工，现在放弃就可惜了。

11.出现以下画面，嗯，恭喜，你成功了。当然，先别记着关闭，复制红色部分到你的电脑中，之后会用到的。然后就可以关闭这个 SSH 窗口了。

<center>![](https://meto.chinakook.com/blog-images/20.png)</center>

配置防火墙规则，这是最后的设置了。

1.点击边栏中：网络 - VPC 网络 - 防火墙规则。

<center>![](https://meto.chinakook.com/blog-images/21.png)</center>

2.设置协议端口：

<center>![](https://meto.chinakook.com/blog-images/22.jpeg)</center>

把端口号设置成刚才我们自己规定的端口号，我的是 789。修改时输入：tcp:789; udp:789，注意，分号“；”后面紧跟一个空格。只设置图中圈红的两个，这两个必须设置，不要漏掉，其余默认。

到此，谷歌云搭建完毕。

搭建完就可以在你的设备上使用了，全平台支持，只需要下载对应的客户端。Mac、Windows、Android 的客户端可以在 GitHub 上搜索 shadowsocks 自行查找。iOS 的客户端需要 App Store 登录国外 ID，然后搜索 Shadowrocket 或者 Wingy。这些客户端如何使用自行搜索，我不知道怎么使用，你懂。

这个速度怎么样呢，反正看某 tube 视频网站的 4k 视频毫无压力，能说明速度如何了吗？

今天的文章主要和大家交流**如何搭建服务器，其他任何目的都没有**。那为什么要以谷歌云为例子呢？因为它可以免费使用一年啊。学会这篇文章之后，再搭建类似服务的服务器时，比如在国内的阿里云、腾讯云上搭建；在自己买的国外服务器上搭建，原理是一模一样的，流程基本一样。对了，话说亚马逊也有免费一年的优惠。

----

写这篇文章我是忐忑的，我是不安的，考虑了很长时间才动笔，大约在一个多月之前就开始思考了。虽然只讨论技术，但毕竟有些不妥之处，希望大家珍重。

现在终于写完了，这篇文章从下午 4 点钟开始下笔，一直写到 8 点多钟，期间要通过操作模拟流程，比较麻烦，也比较辛苦，希望大家能够多多支持，能够分享转发一下让更多人学习。留言、转发都是对我的支持。

我也知道这篇文章可能不会存在太久，但也希望能发挥它的作用。

**需要再次声明的是，本文只讨论搭建服务这项技术，请不要用作其他任何商业用途，否则后果自负。**


<br>ikook
2018.01.04
