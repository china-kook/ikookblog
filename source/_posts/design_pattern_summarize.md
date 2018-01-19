
---
title: 设计模式之「概述」
date: 2017-04-18
tags:
    - Java
    - 设计模式
categories: 技术栈
thumbnail: https://meto.chinakook.com/designpattern.jpg
---

> 设计模式学习系列总结笔记之「概述」

<!--more-->

本文内容均来自「刘伟」前辈 CSDN 博客，只是将内容抽取，作为自己学习总结以及日后复习之用。

原文链接：[http://blog.csdn.net/LoveLion/article/category/738450/13](http://blog.csdn.net/LoveLion/article/category/738450/13)

## 设计模式从何而来

### 模式

Christopher Alexander 在其出版的书中归纳出 253 个模式，对每一个模式（Pattern）都从 Context「前提条件」、Theme 或 Proble「目标问题」、 Solution「解决问题」三个方面进行了描述。

Christopher Alexander 在其另一著作中提出了模式的定义：

** 每个模式都描述了一个在我们的环境中不断出现的问题，然后描述了该问题的解决方案的核心，通过这种方式，我们可以无数次地重用那些已有的成功的解决方案，无须再重复相同的工作。 **

简单来说：

** 模式是在特定环境下人们解决某类重复出现问题的一套成功或有效的解决方案。「A pattern is a successful or efficient solution to a recurring problem within a context」 **

### 设计模式

最早将模式的思想引入软件工程方法学的是1991-1992年以“四人组(Gang of Four，简称GoF，分别是Erich Gamma, Richard Helm, Ralph Johnson和John Vlissides)”自称的四位著名软件工程学者，在1994年归纳发表了23种在软件开发中使用频率较高的设计模式，旨在用模式来统一沟通面向对象方法在分析、设计和实现间的鸿沟。

软件模式并非仅限于设计模式，还包括架构模式、分析模式和过程模式等

软件模式是在软件开发中某些可重现问题的一些有效解决方法，软件模式的基础结构主要由四部分构成，包括问题描述「待解决的问题是什么」、前提条件「在何种环境或约束条件下使用」解法「如何解决」和效果「有哪些优缺点」

在软件模式中，设计模式是研究最为深入的分支，设计模式用于在特定的条件下为一些重复出现的软件设计问题提供合理的、有效的解决方案。

## 设计模式是什么

设计模式的一般定义如下：

** 设计模式「Design Pattern」是一套被反复使用、多数人知晓的、经过分类编目的、代码设计经验的总结，设计模式是为了可重用代码、让代码更容易被他人理解并且保证代码的可靠性。 **

设计模式一般包括模式名称、问题、目的、解决方法、效果等组成要素，其中关键要素是模式名称、问题、解决方法和效果。

 - ** 模式名称「Pattren Name」** 通过一两个词来描述模式的问题、解决方案和效果；

 - ** 问题「Problem」** 描述了应该在何时使用模式，它包含了设计中存在的问题以及问题存在的原因；

 - ** 解决方案「Solution」** 描述了一个设计模式的组成成分，以及这些组成成分之间的相互关系，各自的职责和协作方式，通常解决方案通过 UML 类图和核心代码来进行描述；

 - ** 效果「Consequences」** 描述了模式的优缺点以及在使用模式时应权衡的问题。

设计模式可分为创建型「Creational」，结构型「Structural」和行为型「Behavioral」三种：

** 创建型模式主要用于描述如何创建对象；结构型模式主要用于描述如何实现类或对象的组合；行为型模式主要用于描述类或对象怎样交互以及怎样分配职责。 **

在 GoF 23 种设计模式中包含 5 中创建型设计模式、7 种结构型设计模式、11 种行为型设计模式。

此外，根据某个模式主要是用于处理类之间的关系还是对象之间的关系，设计模式还可以分为类模式和对象模式。我们经常将两种分类方式结合使用，如单例模式是对象创建型模式，模板方法模式是类行为型模式。

类型  | 模式名称  |   学习难度  |   使用频率
:-----------: | :-----------: | :-----------:
创建型模式 Creational Pattern    | 单例模式 Singleton Pattern |  ★☆☆☆☆  | ★★★★☆
创建型模式 Creational Pattern    | 简单工厂模式 Simple Factory Pattern |  ★★☆☆☆  | ★★★☆☆
创建型模式 Creational Pattern    | 工厂方法模式 Factory Method Pattern  | ★★☆☆☆  | ★★★★★
创建型模式 Creational Pattern    | 抽象工厂模式 Abstract Factory Pattern|  ★★★★☆ | ★★★★★
创建型模式 Creational Pattern    | 原型模式 Prototype Pattern | ★★★☆☆ |  ★★★☆☆
创建型模式 Creational Pattern    | 建造者模式 Builder Pattern  | ★★★★☆  | ★★☆☆☆
结构型模式 Structural Pattern    | 适配器模式 Adapter Pattern |  ★★☆☆☆ |  ★★★★☆
结构型模式 Structural Pattern    | 桥接模式 Bridge Pattern |★★★☆☆ |  ★★★☆☆
结构型模式 Structural Pattern    |组合模式 Composite Pattern | ★★★☆☆  | ★★★★☆
结构型模式 Structural Pattern    | 装饰模式 Decorator Pattern | ★★★☆☆ |  ★★★☆☆
结构型模式 Structural Pattern    |外观模式 Façade Pattern | ★☆☆☆☆  | ★★★★★
结构型模式 Structural Pattern    |享元模式 Flyweight Pattern | ★★★★☆ |  ★☆☆☆☆
结构型模式 Structural Pattern    |代理模式 Proxy Pattern  |★★★☆☆   |★★★★☆
行为型模式 Behavioral Pattern    |职责链模式 Chain of Responsibility Pattern |  ★★★☆☆ |  ★★☆☆☆
行为型模式 Behavioral Pattern    |命令模式 Command Pattern   | ★★★☆☆  | ★★★★☆
行为型模式 Behavioral Pattern    |解释器模式 Interpreter Pattern |  ★★★★★ |  ★☆☆☆☆
行为型模式 Behavioral Pattern    |迭代器模式 Iterator Pattern | ★★★☆☆   |★★★★★
行为型模式 Behavioral Pattern    |中介者模式 Mediator Pattern  |★★★☆☆ |  ★★☆☆☆
行为型模式 Behavioral Pattern    |备忘录模式 Memento Pattern   |★★☆☆☆  | ★★☆☆☆
行为型模式 Behavioral Pattern    |观察者模式 Observer Pattern | ★★★☆☆|   ★★★★★
行为型模式 Behavioral Pattern    |状态模式 State Pattern | ★★★☆☆ |  ★★★☆☆
行为型模式 Behavioral Pattern    |策略模式 Strategy Pattern  | ★☆☆☆☆  | ★★★★☆
行为型模式 Behavioral Pattern    |模板方法模式 Template Method Pattern  | ★★☆☆☆ |  ★★★☆☆
行为型模式 Behavioral Pattern    | 访问者模式 Visitor Pattern  | ★★★★☆ |  ★☆☆☆☆

## 设计模式有什么用

设计模式来自众多专家的经验和智慧，它们是从许多优秀的软件系统中总结出的成功的、能够实现可维护性复用的设计方案，使用这些方案将可以让我们避免做一些重复性的工作。

设计模式提供了一套通用的设计词汇和一种通用的形式来方便开发人员之间沟通和交流，使得设计方案更加通俗易懂。当面对同一个设计模式时，你和别人的理解并无而已（编程语不同，跨国界的团队等），因为设计模式是跨语言、跨平台、跨应用、跨国界的。

大部分设计模式都兼顾了系统的可重用性和可拓展性，这使得我们可以更好地重用一些已有的设计方案、功能模块甚至一个完整的软件系统，避免我们经常做一些重复的设计、编写一些重复的代码。许多设计模式将有助于提高系统的灵活性和可拓展性。

合理的使用设计模式并对设计模式的使用情况进行文档化，将有助于别人更快地理解系统。可以让别人能都很快的理解我们的设计思路和实现方案。

学习设计模式将有助于初学者更加深入地理解面向对象思想。「让你知道：如何将代码分散在几个不同的类中？为什么要有“接口”？何谓针对抽象编程？何时不应该使用继承？如何不修改源代码增加新功能？同时还让你能够更好地阅读和理解现有类库（如JDK）与其他系统中的源代码」

## 刘伟前辈的个人观点

掌握设计模式并不是一件很难的事情，关键在于多思考、多实践

在学习每一个设计模式时至少应该掌握如下几点：这个设计模式的意图是什么，它要解决一个什么问题，什么时候可以使用它；它是如何解决的，掌握它的结构图，记住它的关键代码；能够想到至少两个它的应用实例，一个生活中的，一个软件中的；这个模式的优缺点是什么，在使用时要注意什么。

懂得运用设计模式，「少说多做」

千万不要滥用模式。每个模式都有自己的适用场景，不能为了使用模式而使用模式，滥用模式不如不用模式。

「每一个模式都是一种计策」，它为解决某一类问题而诞生，不管这个设计模式的难度如何，使用频率高不高，都应该好好学学。

设计模式的“上乘”境界：“手中无模式，心中有模式”。模式使用的最高境界是你已经不知道具体某个设计模式的定义和结构了，但你会灵活自如地选择一种设计方案「其实就是某个设计模式」来解决某个问题。所以，对模式的学习不要急于求成。

最后一点来自 GoF 已故成员 John Vlissides 的著作《设计模式沉思录》：模式从不保证任何东西，它不能保证你一定能够做出可复用的软件，提高你的生产率，更不能保证世界和平。模式并不能替代人来完成软件系统的创造，它们只不过会给那些缺乏经验但却具备才能和创造力的人带来希望。



<br>ikook
2017.04.18
