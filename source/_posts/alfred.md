---
title: Alfred 每次开机运行提示「访问通讯录」问题
date: 2017-11-06
tags:
- 工具
- Alfred
categories: 软件说
thumbnail: https://meto.chinakook.com/blog-images/alfred.jpg
---

> 在忍受了许久「alfred 破解版」开机询问是否访问通讯录问题之后，终于忍不住了。
 
<!--more-->

自从用上「MacOS」之后就各种玩软件。用了软件，好用的东西很多，当然被我卸载的也很多。其中，Alfred 是我不会卸载的软件之一。

由于，学生一枚（隐喻，穷屌丝），没办法只能用破解版，就像我「MacOS」一样，是黑的 —— 黑苹果。因为是破解版，随之而来的就有一些烦人的问题，Alfred 也一样，它每次开机的时候，都会提示是否允许访问通讯录。

![](https://meto.chinakook.com/blog-images/alfred1.png)

这个问题我忍受了很久，大约有将近一个月吧，我去，我绑不住了，搞他。其实很简单。

在终端输入一下命令，解决。

```s
$ sudo codesign -f -d -s - /Applications/Alfred\ 3.app/Contents/Frameworks/Alfred\ Framework.framework/Versions/A/Alfred\ Framework
```

想要下载「Alfred 破解版」扫描下方二维码关注公众号，后台回复：**Alfred** 即可获取。


<br>ikook
2017.11.06