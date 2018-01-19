---
title: MySQL 常用命令归纳
date: 2017-07-24
tags:
    - 数据库
    - MySQL
categories: 技术栈
thumbnail: https://meto.chinakook.com/blog-images/mysql.png
---

> 《MySQL 必知必会》学习总结&&常用命令归纳，看完这篇文章就不用买《MySQL 必知必会》了，这篇就够了。

## 数据库基础概念&&什么是 SQL、MySQL

### 数据库基础概念
- **数据库(database)** 保存有组织的数据的容器(通常是一个文件或者一组文件)。<br><br>
- **表(table)** 某种特定类型数据的结构化清单。<br><br>
- **模式(schema)** 关于数据库和表的布局及特定的信息。<br>
  模式可以用来描述数据库中特定的表以及整个数据库(和其中表的关系)。<br><br>
- **列(column)** 表中的一个字段。所有表都是由一个或者多个列组成的。<br><br>
- **数据类型(datatype)** 所容许的数据的类型。每个表列都有相应的数据类型，它限制（或容许）该列中存储的数据。<br><br>
- **行(row)** 表中的一个记录。<br><br>
- **主键(primary key)** 一列（或一组列），其值能够唯一区分表中每个行。
  主键的条件：
  1.任意两行都不具有相同的主键值；
  2.每个行都必须具有一个主键值（主键列不允许 NULL 值）

### 什么是 SQL

SQL 是结构化查询语言（Structured Query Language）的缩写。SQL 是一种专门用来与数据库通信的语言。

##### SQL 有以下优点：
- SQL 不是某个特定数据库供应商专有的语言。几乎所有重要的 DBMS 都支持 SQL，所以，学习此语言几乎能与所有数据库打交道。<br><br>
- SQL 简单易学。它的语句全都是由描述性很强的英语单词组成，而且这些单词的数目不多。<br><br>
- SQL 尽管看上去很简单，但它实际上是一种强有力的语言，灵活使用其语言元素，可以进行非常复杂和高级的数据库错操作。

### 什么是 MySQL

数据的所有存储、检索、管理和处理实际上是由数据库软件 —— DBMS（数据库管理系统）完成的。MySQL 是一种 DBMS，即它是一种数据库软件。

##### MySQL 的优点：

- 成本 —— MySQL 是开放源代码的，一般可以免费使用（甚至可以免费修改）。<br><br>
- 性能 —— MySQL 执行很快，非常快。<br><br>
- 可信赖 —— 某些非常重要和声望很高的公司、站点使用 MySQL，这些公司和站点都用 MySQL 来处理自己的重要数据。<br><br>
- 简单 —— MySQL 很容易安装和使用。


## 使用 MySQL 的常用命令归纳（前方高能，很长，很详细）

### USE mysql;
  输出：`Database changed`
  分析：选择并打开「mysql」这个数据库，记住，必须先使用 USE 打开数据库，才能读取其中的数据。
  > 注：这里的 mysql 是指所选数据库的名字。该数据库是 MySQL 软件内部使用的数据库。

### SHOW 语句
- `SHOW DATABASES;`<br>
  分析：返回一个可用的数据库列表。该列表中可能包含 MySQL 内部使用的数据库。<br><br>
- `SHOW TABLES;`<br>
  分析：获得一个所选数据库内的表的列表，即返回当前选择的数据库内可用表的列表。<br><br>
- `SHOW COLUMNS FROM test_table;`<br>
  分析：返回要求显示的表的表列。`SHOW COLUMNS` 要求给出一个表名(这里例子中的 FROM test_table，test_table 为表名)，它对每个字段返回一行，行中包括字段名、数据类型、是否允许 NULL、键信息、默认值以及其他信息。<br>
  注：DESCRIBE 语句，MySQL 支持用 DESCRIBE 作为 SHOW COLUMNS FROM 的一种快捷方式。即 `DESCRIBE test_table;` 是 `SHOW COLUMNS FROM test_table;` 的一种快捷方式。<br><br>
- 所支持的其他 `SHOW` 语句还有：<br>
  1.`SHOW STATUS;` 用于显示广泛的服务器状态信息；<br>
  2.`SHOW CREATE DATABASE;` 和 `SHOW CREATE TABLE;` 分别用来显示创建特定数据库或表的 MySQL 语句；<br>
  3.`SHOW GRANTS;` 用来显示授予用户（所有用户或特定用户）的安全权限；<br>
  4.`SHOW ERRORS;` 和 `SHOW WARNINGS;` 用来显示服务器错误或者警告信息。<br>
  > 注：在 MySQL 命令行程序中，执行命令 `HELP SHOW` 显示允许操作的 SHOW 语句。

### 检索数据
最经常使用的 SQL 语句可能就是 SELECT 语句了，它的用途是从一个或多个表中检索信息。为了使用 SELECT 检索表数据，必须至少给出两条信息 —— 想选择什么，以及从什么地方选择。
>注：以下例子使用的数据库、表名、以及表列等如下：
数据库：
crashcourse
表：
![SHOW TABLES](https://meto.chinakook.com/blog-images/mysql/tables.png)
<br>表列：
- customers
  ![](https://meto.chinakook.com/blog-images/mysql/customers.png)
  <br>
- orderitems
  ![](https://meto.chinakook.com/blog-images/mysql/orderitems.png)
  <br>
- orders;
  ![](https://meto.chinakook.com/blog-images/mysql/orders.png)
  <br>
- productnotes;
  ![](https://meto.chinakook.com/blog-images/mysql/productnotes.png)
  <br>
- products;
  ![](https://meto.chinakook.com/blog-images/mysql/products.png)
  <br>
- vendors;
  ![](https://meto.chinakook.com/blog-images/mysql/vendors.png)

#### 检索单个列
输入：`SELECT prod_name FROM products;`
分析：上述语句利用 SELECT 语句从 products 表中检索一个名为 prod_name 的列。所需的列名在 SELECT 关键字之后给出，FROM 关键字指出从其中检索数据的表名。
> 注： 输出的结果为未排序的数据；SQL 语句是不区分大小写的，但是建议对所有 SQL 关键字使用大写，而对所有列和表名使用小写，这样做有助于使代码更加易于阅读和调试。

#### 检索多个列
输入：`SELECT prod_id, prod_name, prod_price FROM products;`
分析：从一个表中检索多个列，和前一个例子使用相同的 SELECT 语句，唯一不同的地方是必须在 SELECT 关键字后给出多个列名，列名之间必须用逗号分隔。

#### 检索所有列
输入：`SELECT * FROM products;` 命令
分析：如果给定一个通配符*，则返回表中所有列。列的顺序一般是列在表定义中出现的顺序。
> 注： 一般，除非你确实需要表中的每个列，否则最 好别使用*通配符。虽然使用通配符可能会使你自己省事，不 用明确列出所需列，但检索不需要的列通常会降低检索和应 用程序的性能。

#### 检索不同的行
如何检索出有不同值的列表呢？解决办法是使用 DISTINCT 关键字，顾名思义，此关键字指示 MySQL 只返回不同的值。

输入：`SELECT DISTINCT vend_id FROM products;`
分析：SELECT DISTINCT vend_id 告诉 MySQL 只返回不同（唯一）的 vend_id 行。如果使用 DISTINCT 关键字，它必须直接放在列名的前面。
> 注：不能部分使用 DISTINCT。DISTINCT 关键字应用于所有列而不仅是前置它的列。如果给出 SELECT DISTINCT vend_id, prod_price，除非指定的两个列的值相同，否则所有行都将被检索出来。
如下：
没有使用 DISTINCT 关键字
![](https://meto.chinakook.com/blog-images/mysql/no_distinct.png)
<br>
使用 DISTINCT 关键字
![](https://meto.chinakook.com/blog-images/mysql/distinct.png)

#### 限制结果
输入：`SELECT prod_name FROM products LIMIT 5;`
分析：为了返回第一行或者前几行，可使用 LIMIT 子句。此语句使用 SELECT 语句检索单个列。LIMIT 5 指示 MySQL 返回不多于5行。

为得出下一个 5 行，可指定要检索的开始行和行数。

输入：`SELECT prod_name FROM products LIMIT 5,5;`
分析：LIMIT 5, 5 指示 MySQL 返回从行 5 开始的 5 行。第一个数为开始位置，第二个数为要检索的行数。

所以，带一个值的LIMIT总是从第一行开始，给出的数为返回的行数。带两个值的LIMIT可以指定从行号为第一个值的位置开始。
> 注：检索出来的第一行为行 0 而不是行 1。因此，LIMIT 1, 1将检索出第二行而不是第一行；MySQL 5 支持 LIMIT 的另一种替代语法。LIMIT4OFFSET 3意为从行 3 开始取 4 行，就像 LIMIT 3, 4 一样。

####  使用完全限定的表名
到此为止使用的 SQL 例子只通过列名引用列。也可能会使用完全限定的名字来引用列（同时使用表名和列字）。请看以下例子：

输入：`SELECT products.prod_name FROM products;`
分析：这条语句在功能上和 `SELECT prod_name FROM products;` 语句是一样的。但这里指定了一个完全限定的列名。

表名也是可以完全限定的，例如：`SELECT products.prod_name FROM crashcourse.products;` 这条语句和刚才的那条语句是一样的。

### 排序检索数据
如何使用 SELECT 语句的 ORDER BY 子句，根据需要排序检索出来的数据呢？下面我们来看一下。

#### 排序数据
我们上面使用 SELECT 语句检索出来的数据都是没有经过排序的。关系数据库理论认为，如果不明确规定排序顺序，则不应该假定检索出来的数据的顺序有意义。

为了明确地排序用 SELECT 语句检索出来的数据，可使用 ORDER BY 子句。

输入：`SELECT prod_name FROM products ORDER BY prod_name;`
分析：
未完待续...


<br>ikook
2017.07.24
