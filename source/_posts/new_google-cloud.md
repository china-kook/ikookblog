---
title: 谷歌云搭建服务最新教程
date: 2018-11-25
tags:
- 工具
- Google
- 网络
- 科学上网
categories: 技术栈
thumbnail: https://meto.chinakook.com/Google-cloud-service-3.jpg
---

废话少说，开搞。

首先，准备一个可以临时使用的科学上网服务和一个谷歌账号，还有你的信用卡，然后点这里 [https://cloud.google.com](https://cloud.google.com) 登录你的谷歌账号，再点击首页的免费试用。如下图：

<center>
![谷歌云注册](https://meto.chinakook.com/%E8%B0%B7%E6%AD%8C%E4%BA%91%E6%B3%A8%E5%86%8C.jpg)
</center>

填写你的信息，国家都可以，我填写的是美国，不过可能都无所谓。但是下一步的步骤，请仔细认真按真实情况填写，尤其是信用卡那里，你的真实姓名拼音，还有信用卡的到期日和验证码，必须填写无误，不然再验证会很麻烦。

最后点击「开始免费试用」系统就会验证你的信用卡信息，同时，会在你的信用卡扣除一美元，这一美元很快就会退回来，用来验证信用卡。

验证通过之后会创建一个名叫「My First Project」的项目，不要更改你的项目名，也不要删除和新建项目，所有的 VM 实例都在这个项目里创建，可以避免扣除我们信用卡的钱。因为这个项目会和我们的结算账号关联。

然后，点击左上角导航按钮再点击「结算」可以看到我们的赠金。可以看到项目与这个赠金的结算账户关联起来了，如果你自己删除或者新建项目，可能会导致新建的项目会关联到你的信用卡，从而导致你扣款。

<center>
![](https://meto.chinakook.com/%E8%B5%A0%E9%87%91.jpg)
</center>

下面，点击左上角导航按钮，再选择「Computer Engine」再点击「VM 实例」，如下：

<center>
![](https://meto.chinakook.com/1543140705225.jpg)
</center>

再点击「创建实例」，就会出现下面的界面：

<center>
![](https://meto.chinakook.com/1543140966653.jpg)
</center>

注意查看图中红框，「区域」选择台湾、香港、东京、新加坡等均可，速度都可以。「机器类型」选择微型即可，够用，最便宜。「映像」选择 CentOS 6 和 Debian 9 都可以，搭建过程有不同，下面会说，但是建议 Debian 9 ，搭建过程更简单。最后一定要勾选「防火墙」那里，允许 HTTP 和 HTTPS 流量。点创建等待创建即可。

创建完成后，如下图，你的是一个实例。

<center>
![](https://meto.chinakook.com/1543141405965.jpg)
</center>

点击 SSH 连接服务器，然后会弹出一个黑窗口，进行搭建。如下：

<center>
![](https://meto.chinakook.com/1543141548587.jpg)
</center>

----

开始搭建，严格按照下面的步骤来即可，完全没问题，我就不截图了。

根据刚才创建实例时选择的映像不同，步骤有所不同（推荐 Debian 9）

**注意：如果使用的是 Debian9 只用从第 5 步开始（当然 sudo -i 这一步还是要的），只需 2 步就可以搭建好，不用装 BBR 加速器，速度也非常的快！如果是 CentOS，从第一步开始。**

步骤 1-4 是安装 BBR 加速器部分，步骤 5-6 是 shadowsocksR 部分

1：
```
sudo -i
```
最前面显示root@xxxx

2：
```
wget -N --no-check-certificate https://raw.githubusercontent.com/FunctionClub/YankeeBBR/master/bbr.sh && bash bbr.sh install
```

如果出现蓝底窗口按 TAB 键选 NO，如果没有直接往下走即可。

选择重启 Y

这里会断开连接，大家可以关掉窗口再重新打开或几秒钟后在界面随便按几个字母，便会提示重新连接。

3：
```
sudo -i
```
最前面显示root@xxxx

4：
```
bash bbr.sh start
```

5：
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh && chmod +x shadowsocksR.sh
```

6：
```
./shadowsocksR.sh
```

输入 shadowsocks 密码，也就是你连接科学上网服务的密码。

输入端口号

其他一路回车（也可自行选择混淆协议，但还是建议直接回车，强烈建议。）

等待几分钟，最后会出现 shadowsocks 信息，利用这些信息就可以上网了，如下：

<center>
![](https://meto.chinakook.com/1543144043567.jpg)
</center>

对了，如果命令行窗口（黑窗口）什么信息都没有，按一下键盘就会出现上图的信息了。将上面的信息复制出来保存起来，以便之后连接，然后就可以将这个窗口关闭了。

最后，需要设置防火墙规则，只设置一次即可，防火墙规则是账号级别的，可以作用于所有 VM 实例。点击左上角导航按钮，再选择「VPC 网络」然后点击「防火墙规则」。然后分别设置名为「default-allow-http」和「default-allow-https」的规则为如下即可：

<center>
![](https://meto.chinakook.com/1543144581499.jpg)
</center>

然后，你就可以在你的手机或者电脑上配置自由上网了。享受自由网络吧，谷歌云的速度非常快，youtube 4k 完全无压力，速度杠杠的。



<br>ikook
2018.11.25

