---
title: Oracle Database 12c安装教程(Windows版)
date: 2016-12-11
tags:
    - Oracle
    - 数据库
categories: 技术栈
thumbnail: https://meto.chinakook.com/unsplash3.jpg
---

> 自己在安装过程中踩了好多坑，记录一下。

<!--more-->

# 前言：
 首先，要说的是为了安装Oracle Database我花费了大量的时间，在安装过程中出现了各种各样的问题。在此记录一下，以便自己总结并方便查询，同时也为各位广大朋友提供借鉴。
# Oracle数据库：
Oracle Database，又名Oracle RDBMS，或简称Oracle。是甲骨文公司的一款关系数据库管理系统。它是在数据库领域一直处于领先地位的产品。可以说Oracle数据库系统是目前世界上流行的关系数据库管理系统，系统可移植性好、使用方便、功能强，适用于各类大、中、小、微机环境。它是一种高效率、可靠性好的 适应高吞吐量的数据库解决方案。
# 安装：
 - ### 准备
  - 下载安装包：
首先下载Oracle Database 12c的Servers和Client压缩包到本地。这里只贴上win64位的连接地址。其他版本自行访问[Oracle Database 软件下载](http://www.oracle.com/technetwork/cn/database/enterprise-edition/downloads/index.html)进行下载。
Servers(服务器端)：
[winx64_12102_database_1of2.zip](http://120.52.72.22/download.oracle.com/c3pr90ntc0td/otn/nt/oracle12c/121020/winx64_12102_database_1of2.zip)
 [winx64_12102_database_2of2.zip](http://download.oracle.com/otn/nt/oracle12c/121020/winx64_12102_database_2of2.zip?AuthParam=1481383491_65acf9e1231a462986564765ba630da3
)
Client(客户端)：
[winx64_12102_client.zip](http://download.oracle.com/otn/nt/oracle12c/121020/winx64_12102_client.zip?AuthParam=1481383698_446c62928f2c93843bc7e18812ca548b)
-  解压下载好的两个压缩文件：
将两个压缩包解压到同一个目录下，即“database”；

![datebase文件夹](https://meto.chinakook.com/blog-images/ping.png)


- ### Servers安装
 - 以管理员的身份运行”setup.exe”进行安装：
软件会加载并初步校验系统是否可以达到了数据库安装的最低配置,如果达到要求,就会直接加载程序并进行下一步的安装;
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping2.png)
 - “配置安全更新”窗口：
取消“我希望通过My Oracle Support接受安全更新”，单击“下一步”；
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping3.png)此时可能遇到的问题：在[INS-30131] 执行安装程序验证所需的初始设置失败
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping4.png)
问题原因及解决办法：
1.问题：用户文件中含有中文（如你的账户名字包含汉字   C:\Users\张三）
  解决办法：打开计算机管理——本地用户和组——用户——Administrator（右键属性）——账户已禁用（取消勾选）——确定
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping5.png)到此，就可以切换到Administrator用户，在Administrator用户下安装。
2.问题：未共享C盘
解决方法：打开计算机管理——共享文件夹——共享（右键“新建共享”）——下一步——（文件路径填）C:\——下一步——是——共享名C$——下一步——选中（“管理员有完全访问权限；其他管理员只有读写权限”）——完成——完成。由于大部分人都不是这个原因，这里就不上图了，并且网上有很多。
 - “安装选项”窗口
选择“创建和配置数据库”，单击“下一步”；
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping6.png)
 - 选择”桌面类”还是”服务器类”
选择”服务器类”可以进行高级的配置,我这里选择”桌面类”,单击”下一步“，大多数情况下是选择“桌面类”，原因操作说明很清楚；
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping7.png)
 - 创建oracle管理用户
这步是其他版本没有的,这个的作用就可以更安全的管理orcl,主要是防止登录win系统勿删了oracle文件，这里选择第二个”创建新windows用户“，输入用户名和口令，专门管理oracle文件的，单击”下一步“；
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping8.png)
 - “典型安装”窗口(安装位置)
选择Oracle的基目录，选择“企业版”和“默认值”并输入统一的密码为：Oracle12c，单击“下一步”;
注意：Oracle为了安全起见，要求密码强度比较高，你输入的密码Oracle认为不能复制,我试过了，即使简单的数字字母组合Oracle也认为是不符合).Oracle建议的标准密码组合为：小写字母+数字+大写字母，这回就合格了，当然字符长度还必须保持着Oracle 12c数据库要求的范围之内。
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping9.png)
 - “执行先决条件检查”窗口
上一步设置好了后,将进行检查，在“执行先决条件检查”窗口中，单击“下一步”；
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping10.png)
 - 上一步检查没有问题后
会生成安装设置概要信息,可以保持这些设置到本地,方便以后查阅,在这步确认后,单击”安装”,数据库通过这些配置将进行整个的安装过程:注意:在安装过程中,最好将杀毒软件,安全卫士什么的都强行关闭,安装成功后重启电脑就可以了.
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping11.png)
 - 安装过程中
这里是一个漫长的等待过程，切勿不小心关闭了程序，或者断电，电脑重启。
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping12.png)
 - 创建数据库实例
“Database Configuration Assistant”界面,特别的长时间等待，大约半个钟头，需耐心等待；
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping13.png)
 - 数据库实例安装成功后，会弹出口令管理,进入口令管理
选择“口令管理”，查看并修改以下用户：
**（1）普通管理员：SYSTEM（密码："自己填写"）**
**（2）超级管理员：SYS（密码：“自己填写”）**
修改完成后，单击“确定”。 这里的口令也是需要符合oracle口令规范的，参考前面设置数据库实例口令设置方式。
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping14.png)
 - 安装完成
会出现如下界面，单击“关闭”即可。
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping15.png)
 至此Servers安装完毕。

- ### Client安装：
Client安装非常简单，有了Servers的安装我相信Client肯定能自己装好，毕竟连我这么笨的人都装好了。因此就不再赘述了。
需要说明的是，在Servers安装中说到可能会遇到**“在[INS-30131] 执行安装程序验证所需的初始设置失败”**的问题，如果是第一种情况的话，Client也要使用Servers安装时的方法，在Administrator用户下安装。安装完成后再切换回原来用户模式下，再禁用Administrator即可。

- ### 检查是否安装成功：
可在安装后软件中找到“SQL Plus”，后以管理员身份运行。
输入用户名和口令，在保证用户名和口令正确的情况下，查看是否连接，连接后输入select sysdate from dual;
打印出当前系统日期则说明安装完全成功。
![Paste_Image.png](https://meto.chinakook.com/blog-images/ping16.png)
- ### 说明：
以上就是Oracle Database 12c windows64位安装教程。其中部分内容来自网络借鉴。

<br>ikook
2016.12.11
