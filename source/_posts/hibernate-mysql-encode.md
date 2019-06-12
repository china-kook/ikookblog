---
title: Hibernate 插入中文乱码
date: 2018-03-14
tags:
- Hibernate
- MySQL
categories: 技术栈
thumbnail: https://meto.chinakook.com/blog-images/180314.jpeg
---


近些日子在折腾 Hibernate，遇到一个小问题：向 MySQL 数据库插入中文数据的时候会发现乱码，乱码形式表现为“?”。看到第一反应是：这还不简单，MySQL 建表时使用的是默认字符集，改成「UTF-8」不就得了。那就改啊，改完之后测试，顿时感觉心凉了一下。提示错误信息：

> org.hibernate.exception.GenericJDBCException: could not execute statement

我擦，这是什么鬼？刚开始玩 Hibernate 的我一脸懵逼，还能怎么办，Google 啊。

按照网上的解决办法就是在 Hibernate 核心配置文件中的数据库连接 url 后面添加如下代码：

> ?useUnicode=true&amp;characterEncoding=utf-8 

再次测试，结果还是上面的错误信息，这就尴尬了。再查，发现我的 MySQL 数据库没有更改默认字符集，MySQL 的默认字符集是“latin1”（鬼知道 MySQL 设计者为什么弄它作为默认字符集）。开整。

可以通过在终端进入 MySQL 然后输入：show variables like '%char%'; 查看字符集。
<center> 
![](https://meto.chinakook.com/blog-images/180314-01.jpeg)
</center>

图中标注的地方是更改之后，更改之前应该是「latin1」。想要更改 MySQL 的编码，就需要修改 MySQL 配置文件：my.cnf。修改配置文件之前一定要将 MySQL 进程关闭，一定要，不然会出现麻烦。

将 MySQL 安装目录下的my.cnf文件复制到/etc目录下（如果 MySQL 安装目录没有 my.cnf 文件，则直接在/etc中新建一个名为 my.cnf 的文件）

my.cnf 文件内容如下：
<center>
![](https://meto.chinakook.com/blog-images/180314-02.jpeg)
</center>

在 my.cnf 文件中添加图中标注的内容。完整内容在我的公众号后台回复「my.cnf」获取。对了，Mac 下是 my.cnf 文件，windows 对应的配置文件名是 my.ini

更改完重启 MySQL 测试，心想这下应该可以了吧，然而，还是出现那个错误信息。别慌，Hibernate 要操作的数据库是更改默认编码之前创建的，所以去更改下待操作的数据库的字符集（一开始只更改了表的字符集）。再测试，OK。

所以问题的根本在于数据库的编码。那折腾半天 MySQL 默认编码干啥？直接更改待操作数据库的字符集不就得了？更改 MySQL 默认编码之后再创建新的数据库，就不用再去手动设置字符集，省去了以后的麻烦，也算自己没白折腾。


<br>ikook
2018.03.14
