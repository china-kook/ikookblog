---
title: Kotlin-开始
date: 2017-06-16
tags:
    - kotlin
categories: 技术栈
thumbnail: https://meto.chinakook.com/blog-images/kotlin01.png
---

> Kotlin 从入门到放弃--开始

<!--more-->

## 什么是 Kotlin
简单来说，Kotlin 是一门由「JetBrains」开发的基于 JVM 的静态类型编程语言，它 100% 兼容 Java。

它可以用于：
- 服务器开发
- Android 开发
- 前端开发
- 本地执行程序

这是要全栈的节奏啊，它的目标应该就是要成为一门全栈编程语言。
### 维基百科介绍
Kotlin 是一种在 Java 虚拟机上运行的静态类型编程语言，它也可以被编译成为 JavaScript 源代码。它主要是由俄罗斯圣彼得堡的 JetBrains 开发团队所发展出来的编程语言，其名称来自于圣彼得堡附近的科特林岛。2012 年 1 月，著名期刊《 Dr. Dobb's Journal 》中 Kotlin 被认定为该月的最佳语言。虽然与 Java 语法并不兼容，但 Kotlin 被设计成可以和 Java 代码相互运作，并可以重复使用如 Java 集合框架等的现有 Java 类库。
#### 历史
2011 年 7 月，JetBrains 推出 Kotlin 项目，这是一个面向 JVM 的新语言，它已被开发一年之久。JetBrains 负责人Dmitry Jemerov 说，大多数语言没有他们正在寻找的特性，Scala 除外，他指出了 Scala 的编译时间慢这一明显缺陷。Kotlin 的既定目标之一是像 Java 一样快速编译。

2012 年 2 月，JetBrains 以 Apache 2 许可证开源此项目，Jetbrains 希望这个新语言能够推动 IntelliJ IDEA 的销售。

Kotlin v1.0 于 2016 年 2 月 15 日发布。这被认为是第一个官方稳定版本，并且 JetBrains 已准备从该版本开始的长期向后兼容性。

在 Google I/O 2017 中，Google 宣布在 Android 上为 Kotlin 提供支持。

## 开发环境搭建
### 安装 Java
Kotlin 是基于 JVM 的编程语言，所以首先一定要先安装好 Java 开发环境，并配置好环境变量。点击链接：[Java SE](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) 下载对应版本，安装完成后配置环境变量。安装过程自行 Google。

下面贴一下 Windows 下配置环境变量的过程。
1. 打开，我的电脑 --> 属性 --> 高级 --> 环境变量 <br><br>
2. 新建系统变量 JAVA_HOME 和 CLASSPATH：<br>变量名：JAVA_HOME
     变量值：C:\Program Files\Java\jdk1.7.0（这个是你JDK安装的位置，注意变量值到JAVA JDK文件夹，复制粘贴）
变量名：CLASSPATH
变量值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar;（复制即可）<br><br>
3. 选择「系统变量」中变量名为「Path」的环境变量，双击该变量，把 JDK 安装路径中 bin 目录的绝对路径，添加到「Path」变量的值中，并使用半角的分号和已有的路径进行分隔。 <br>变量名：Path <br>变量值：%JAVA_HOME%\bin;%JAVA_HOME%\jre\bin;（在系统变量中找到「Path」变量，把前面的变量放到原有变量最前面）

### 安装 Kotlin
我这里选择 Working with the Command Line Compiler 的方式来开始学习 Kotlin。使用这种方式便于理解 Kotlin 的运行原理，并且命令行其实也是蛮炫酷的，更没有想象的那么难，命令不会可以查。

#### Windows
在  [GitHub](https://github.com/JetBrains/kotlin/releases/tag/v1.1.2-5) 中下载安装包，然后手动解压到自己想要的目录，解压完成后，配置环境变量。将 Kotlin 解压目录下的 bin 路径添加到环境变量的「系统变量」中「Path」下。
#### Mac & Linux
如果你是 Mac 或者 Linux 系统可以使用下面方式中的任意一种。由于我用的是 Windows，不保证下列方式均可行，并且没有测试过，只是将官方的方法照搬过来而已。
##### SDKMAN!
```s
 $ curl -s https://get.sdkman.io | bash
 $ sdk install kotlin
```
##### Homebrew
```s
 $ brew update
 $ brew install kotlin
```
##### MacPorts
```s
$ sudo port install kotlin
```

## 创建并运行第一个 Kotlin 程序
新建一个名为 hell.kt 的文件，扩展名 .kt 代表是 Kotlin 文件。在文件中输入以下内容：
``` kotlin
fun main(args: Array<String>) {
    println("Hello, World!")
}
```
然后在终端(Terminal)中输入以下命令：
```s
$ kotlinc hello.kt -include-runtime -d hello.jar
```
注：「kotlinc」 是编译的意思，类似于 javac；「hello.kt」 是需要编译的文件名；「-include-runtime」代表包含进 kotlin 运行时库来运行 hello.kt 的代码来生成 .jar 文件；「-d」代表打包成 .jar 文件的名字。由于 Kotlin 是 JVM 语言，所以最终是转换成 jar 包的。

然后，继续在终端输入以下命令来运行程序：
```s
$ java -jar hello.jar
```
输出 `Hello, World!` 代表运行成功。
- - -
如果要开发由其他 Kotlin 程序使用的库，则可以生成 .jar 文件，而不包含运行时库：
```s
$ kotlinc hello.kt -d hello.jar
```
在使用该 library 时，需要依赖 Kotlin 运行时环境，所以在编译时，应将出现在类路径中：
```s
 $ kotlin -classpath hello.jar HelloKt
```
注：HelloKt 是 Kotlin 编译器为 hello.kt 文件生成的主类名。

这种方式和上面的区别在于第二步给 hello.jar 指定了一个类 HelloKt，让 hello.jar 中的代码运行在 HelloKt 类里。


## 交互式 Kotlin shell
Kotlin 内置有一个交互式的 Shell。交互式 shell 的意思是可以直接在 shell 里输入代码，然后回车直接立即执行。

在终端输入：
```s
$ kotlinc-jvm
```
会输出以下欢迎信息：
```s
Welcome to Kotlin version 1.1.2-5 (JRE 1.8.0_112-b15)
Type :help for help, :quit for quit
```
欢迎信息中给出了退出的方式「:quit」

## Kotlin 脚本
Kotlin 也可以直接执行脚本。「脚本」就是在一个文件中写入想要执行的代码，然后输入一个命令就可以直接执行脚本里面的代码，不需要编译。Kotlin 脚本以 .kts 拓展名结尾。

例如：
新建名为 hello.kts 的脚本，在其中输入以下代码：
```
println("Hello Kotlin Script!")
```
然后在终端输入：
```s
$ kotlinc -script hello.kts
```
脚本执行，然后输出：
```
Hello Kotlin Script!
```

至此，Kotlin 从入门到放弃的第一篇「开始」就介绍完了，本文介绍了 Kotlin 的安装方式以及使用命令执行 Kotlin 程序的方法。建议其中内容均手动实践几遍，实践出真知。

本文参考及学习地址：[JetBrains/kotlin: Working with the Command Line Compiler](http://kotlinlang.org/docs/tutorials/command-line.html)


<br>ikook
2017.06.16


