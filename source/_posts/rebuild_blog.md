---
title: 重建 Blog
date: 2017-01-06
tags:
    - hexo
    - 常用技术
    - 生活
categories: 技术栈
thumbnail: https://meto.chinakook.com/unsplash4.jpg
---

> 重新搭建起个人blog：[https://ikookblog.com](https://ikookblog.com)

<!--more-->

## **起因**
由于参加全国软件测试大赛，导致11月份和12月上半月没时间写博客，都在弄测试和被老师拉去辅导同学。比赛之后想要写篇博客记录下的，可是由于期间重装了笔记本系统，导致博客崩塌。只怪自己一时疏忽忘记备份配置文件。。让我哭会吧，只能重新折腾了。又由于要期末考试了，一学期基本没有上课、根本没听课的我，只能临时抱佛脚了。所以打算先放一放blog 的事，一心复习。

##  Material
恩，事情都有两面性。虽然由于自己的失误导致不得不重新折腾blog，但是如果没有这件事，好像自己会错过使用这么好的主题的机会，那就是—— Material。这个主题给我的第一印象就是好看，简洁，爽。简洁又不失个性。我自己本身对Google非常来感，对Google推出的设计语言Material Design情有独钟，MD给我的感觉就是比iOS好看的多。交互上的设计，视觉上的设计等，让我相信Android会发展的更好，Android程序员再也不用去想如何去做一个iOS风格的Android App了。

今天的主题不是Android，是Material，所以来说说[Material](https://material.viosey.com/)。该主题是由一位在校大学生写了，我只能说: 服！16年下半年才上线的吧，具体时间我也不清楚，好像是国庆节后。该主题遵循Material Design设计风格，并且非常简洁大方，又不失可观赏性。喜欢的可以加入到Material阵营了，目测该主题要火。GitHub地址为：[hexo-theme-material](https://github.com/viosey/hexo-theme-material)，作者博客地址: [Viosey's Blog](https://blog.viosey.com/)。

## **填坑**
今天顺便把以前遗留的一个坑给填上了。GitHub上博客的仓库主页空荡荡，没有README。并且GitHub建议填写README。如果把README.md放入到 source 文件夹，```hexo g``` 生成时会被解析成 html 文件，放到 public 文件夹，生成时又会自动删除。在GitHub添加时，在本地```hexo g -d```也会自动删除(删除的原因和以上说的一样)。

试了很多办法，查了好久，终于解决。

解决方法很简单，在 source 目录下新建文件```README.mdown```，在里面写README即可。```hexo g``` 会把它复制到 public 文件夹，且不会被解析成 html。

## **结语**
就写这么多，关于如何搭建blog，网上一搜一大些，教程多的数不过来。hexo官方文档也有说明，每个主题也都有相应说明。这里就不做这些无用功了。再说明一下，本人以前的主题是Next，该主题很好用，并且很简洁。

**推荐几篇较为完整的教程:**

- [Hexo 3.1.1 静态博客搭建指南](https://note.leodev.me/2016/09/01/Hexo-3-1-1-Staic-Blog-Build-Guide/)
- [小白独立搭建博客-Github-Pages和Hexo简明教程](https://lijianchang.xyz/2016/03/16/%E5%B0%8F%E7%99%BD%E7%8B%AC%E7%AB%8B%E6%90%AD%E5%BB%BA%E5%8D%9A%E5%AE%A2-Github-Pages%E5%92%8CHexo%E7%AE%80%E6%98%8E%E6%95%99%E7%A8%8B/)
- [基于Hexo框架+GitHub Pages搭建个人博客](https://dukecuichen.com/2016/04/08/%E5%9F%BA%E4%BA%8EHexo%E6%A1%86%E6%9E%B6-GitHub-Pages%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)
- [Material Theme官方文档](https://material.viosey.com/)


<br>ikook
2017.01.06