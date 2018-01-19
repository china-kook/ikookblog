---
title: Git 学习总结
date: 2016-10-15
tags:
    - Git
    - 常用技术
categories: 技术栈
thumbnail: https://meto.chinakook.com/3M4PTI5DD40X.jpg
---

Git是什么？ Git是目前世界上最先进的分布式版本控制系统（没有之一）。

<!--more-->

作为一个开发者，Git 的使用基本上是必备技能了。关于 Git 的教程网上很多，我就不展开写 Git 教程了，文末会有推荐的教程链接。本文涵盖 Git 的介绍、安装和常用的命令。

### 什么是 Git？

Git 是目前世界上最先进的分布式版本控制系统，是由 Linux 发明者 Linus 开发的一款新时代的版本控制系统。 

**那什么是版本控制系统呢？**

网络定义：版本控制（Revision control）是维护工程蓝图的标准作法，能追踪工程蓝图从诞生一直到定案的过程。此外，版本控制也是一种软件工程技巧，借此能在软件开发的过程中，确保由不同人所编辑的同一代码文件案都得到同步。是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。 

简单来讲，版本控制系统就是在开发过程中对我们的代码进行管理的系统。比如：为了防止代码的丢失，我们会把本地和服务器都放置一份或者多份，这时候版本控制系统就可以使本地和远程同步； 在多人协作完成一个项目时，我们需要对一份代码进行更改和管理，这时候不影响别人工作就可以同步别人的代码；代码出现 bug，对代码进行紧急的管理或者还原等等。

### Git 的安装

Git 是一个版本控制系统，所以我们必须下载安装才能使用。Mac 系统是自带 Git 的，为了避免特殊情况，这里也说一下 Mac 下的安装方式。

**Linux**

通过一条「sudo apt-get install git」命令就可以直接完成 Git 的安装，非常简单。

可以通过命令「git --version」查看版本，如：「git version 2.14.1」

**Mac OS X**

两种安装方式。

1.安装 homebrew，然后通过 homebrew 安装 Git，具体方法请参考 homebrew 的文档：[http://brew.sh/](http://brew.sh/)

2.从 AppStore 安装 Xcode，Xcode 集成了 Git，不过默认没有安装，需要运行 Xcode，选择菜单“Xcode”->“Preferences”，在弹出窗口中找到“Downloads”，选择“Command Line Tools”，点“Install”就可以完成安装了。

**Windows**

Windows 系统是默认没有安装 Git，也没有内置 Git 安装包的。需要手动下载安装。访问下载 Git 安装包：[https://git-for-windows.github.io/](https://git-for-windows.github.io/)。下载完成后默认安装即可（可以修改一下安装路径）。 

安装完成，在开始菜单里找到“Git”->“Git Bash”打开，出现一个类似命令行窗口的软件，就说明Git安装成功。

顺便说一句，Windows 是对开发最不友好的系统了，劝大家有机会果断放弃，我相信会为你的决定感到高兴的。

安装完成后，还需要最后一步设置，在命令行输入：
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

### Git 常用命令归纳

**常用操作：**
```
$ git init：初始化一个仓库。 

$ git add <file>：把文件添加到仓库。(注意：是添加到仓库，需要执行提交操作才能把文件放到仓库。本操作实际上就是把文件修改添加到暂存区) 

$ git commit : 把文件提交到仓库。 

$ git status：查看工作区的状态。 

$ git diff：查看修改的内容 

$ git log：查看日志 

$ git log --pretty=oneline：查看排版的日志 

$ git reset --hard commit_id：回退到以前的版本。Git 中用 HEAD 表示当前版本，上一版本为HEAD^，上上版本为HEAD^^，假如为往上100版本，则可表示为：HEAD~100。 

$ git reflog：查看命令历史。可用来确定要回到未来的哪个版本。 

$ git reset HAED file：把暂存区的修改撤销掉，重新放回工作区。 

$ git checkout --file：丢弃工作区的修改。git checkout 其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。 

$ git rm file：删除一个文件。
```

**远程操作：**
```
$ git remote add origin git@github.com:GitHubName/repo-name.git：关联一个 GitHub 远程库。通用结构：git remote add origin git@server-name：path/repo-name.git。 

$ git push -u origin master：第一次向远程库推送 master 分支的所有内容。 

$ git push origin master：向远程库推送最新修改。 

$ git pull：抓取远程的新提交，保持本地和远程同步。 

$ git pull origin master：把 master 分支的最新状态抓取到本地。 

$ git remote -v：查看远程库信息。 

$ git clone git@github.com:GitHubName/repo-name.git：将 github 项目 clone 到本地，被 clone 的项目将作为远程库。

$ git checkout -b branch-name origin/branch-name：在本地创建和远程分支对应的分支，名称最好一致。 

$ git branch --set-upstream branch-name origin/branch-name：建立本地分支和远程分支的关联。 

$ git push origin <tagname>：推送某个标签到远程。 

$ git push origin --tags：一次性推送全部尚未推送到远程的本地标签。 

$ git push origin：refs/tags/<tagname>：删除远程标签。(先删除本地的标签)
```

**分支操作：**
```
$ git branch：查看所有分支 

$ git branch <name>：创建分支 

$ git checkout <neme>：切换分支 

$ git checkout -b <name>：创建+切换分支 

$ git merge <name>：合并某个分支都当前分支 

$ git branch -d <name>：删除分支 

$ git merge --no-ff -m "描述" <name>：记录分支情况的合并分支方法。
```

**stash 操作：**
```
$ git stash：储藏当前工作状态 

$ git stash list：查看储藏的工作列表。 

$ git stash apply：恢复工作状态，但恢复后stash的内容并不删除。 

$ git stash drop：删除最近一次stash的内容 

$ git stash clear：清空所有的stash内容。 

$ git stash pop：恢复工作状态并删除相关stash内容。
```

**标签操作：**
```
$ git tag <name>：新建一个标签。 

$ git tag -a <tagname> -m "描述"：新建标签并指定标签信息。 

$ git tag -s <tagname> -m "描述"：PGP签名标签。 

$ git tag：查看所有标签。 

$ git tag -d <tagname>：删除一个本地标签。 

$ git push origin <tagname>：推送某个标签到远程。 

$ git push origin --tags：一次性推送全部尚未推送到远程的本地标签。 

$ git push origin :refs/tags/<tagname>：删除远程标签。(先删除本地的标签)
```

以上只是 Git 常用的命令。Git 极其强大，命令繁多，我只是总结了一些较为常用的命令。但是，以上命令就足够我们平常使用了。


### GitHub

我们学习了 Git 之后，怎么才能充分使用这项技能呢？ 答案是 GitHub。

GitHub 是世界上最大的开(同)源(性)社区。我相信程序员没有不知道 GitHub 的了，熟练使用 GitHub 同样是程序员的必备技能。当然，Git 并不只是在 GitHub 上使用。我们在工作以后团队之间的合作、代码的管理基本上都是使用 Git。 

那么，Git 与 GitHub 之间有什么联系呢？ 

Git 是一款免费、开源的分布式版本控制系统。不管是学习 GitHub，还是以后想从事编程行业，Git 都可以算是必备技能了。 

GitHub 主要提供基于 Git 的版本托管服务，也就是说现在 GitHub 上托管的所有项目代码都是基于 Git 来进行版本控制的，所以 Git 只是 GitHub 上用来管理项目的一个工具而已，GitHub 的功能远不止于此。所以建议去系统学习一下 GitHub。

GitHub 的学习资料见下。

### 总结
由于我只是学习了 Git 的基础，所以对 Git 只是初步的了解。Git 的功能非常强大，本文只是罗列出了一些常用命令。Git 绝不是两天就可以完全掌握的，但是可以学会 Git 的基本使用。常用的 Git 命令本文基本涵盖，并且工作中常用的命令就那么十几条，掌握好这十几条命令，就基本可以得心应手的使用 Git。

我是通过「廖雪峰」前辈的教程来学习的 Git，教程链接同样在下面。他的这份教程非常好，没有任何基础的人一样可以看得懂，这也就是我不写 Git 教程的原因了，因为没有必要，我不觉得我会比廖前辈写的好，不敢造次，但帮助盆友们做一些小总结还是可以的，也可以方便自己查看。

### 学习资料

**Git 学习资料：**

廖雪峰 Git 教程：[http://t.cn/zQ6LFwE](http://t.cn/zQ6LFwE)
ProGit 中文版：[https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2)
Git 简易指南：[http://rogerdudler.github.io/git-guide/index.zh.html](http://rogerdudler.github.io/git-guide/index.zh.html)

**GitHub 学习资料：**

这里只附上 stormzhang 的教程，是一个系列，还算比较全面，值得学习。我就是通过这份教程学习的 GitHub，网上的教程也不少，大家可以自行 Google。

GitHub 系列教程：
[从0开始学习 GitHub 系列之「初识 GitHub」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650661735&idx=1&sn=9aceac07d272e9202d1b5294f857a5ff&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「加入 GitHub」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650661762&idx=1&sn=8282241cf7414030f4e1d315a173beb1&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「Git速成」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650661788&idx=1&sn=b7c54f9b13f4e30fe151905f11c02800&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「向GitHub 提交代码」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650661821&idx=1&sn=c6116ed82bff2d083bb152fbd8cbc38d&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「Git 进阶」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650661929&idx=1&sn=69e00516a30723c5a20af3c7a84173a4&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「团队合作利器 Branch」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650661978&idx=1&sn=2f5329f5b2bfda7050822cc5e3a4f03f&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「如何发现优秀的开源项目」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650662079&idx=1&sn=65605f0d9bd741d38f0b179980dc09f1&scene=21#wechat_redirect)
[从0开始学习 GitHub 系列之「GitHub 常见的几种操作」](http://mp.weixin.qq.com/s?__biz=MzA4NTQwNDcyMA==&mid=2650662303&idx=1&sn=3df7cba7cd85b33a82b4c05bb12cfff5&chksm=87d138c0b0a6b1d6140da9bab6e58c6e2b258de6118175d31c1ac467b3c58bc1a7c0b1a7db9b&scene=0#wechat_redirect)

大家也可以关注我的微信公众号「ikook」，然后后台回复「GitHub」即可获取该系列教程的 pdf 版。微信扫以下二维码即可关注。



<br/>ikook
2016.10.15


