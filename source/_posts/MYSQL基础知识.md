---
title: mysql基础知识
date: 2018-12-06 22:45:20
tags:
---
```
以下是MYsql的一些基础知识和语句 加油！！
服务器
	如何在项目中保存数据——数据库——单词
(1).数据库概述
     数据库(database):以特定的结构批量存储业务数据的软件。
     关系型数据库逻辑结构(RDBMS)
Relation Database Manage System
  	Server->Database->Table->Row->Column

常见的关系型数据库：
 SQLite ： 微型数据库，常用于移动设备
 MySQL： 开源中小型数据库，可用于各种操作系统
 PostgreSQL： 开源中小型数据库
 SQL Server： Microsoft开发的中型数据库，只用于Windows系统
 Orange： Oracle公司开发的中大型数据库，可用于各种操作系统
（2）.MYSQL数据库
 Oracle分支：MYSQL
 Martin分支：MariaDB
xampp是一个服务器套装，包含多款开源的服务器，例如MySQL,PHP...
 MySQL部署结构
    服务器端软件：负责存储/维护数据——银行总行机房
    客户端软件：负责向服务器发起增删改查的命令——ATM机
（1）服务器端：
C:\xampp\mysql\bin\mysqld.exe   启动文件
C:\xampp\mysql\data  数据文件——人无法看懂
（2）客户端：
    C:\xampp\mysql\bin\mysql.exe  客户端软件
用来连接服务器端
（3）连接MySQL服务器
  mysql.exe -h127.0.0.1 -P3306 -uroot -p
  简写形式
mysql -uroot

3. 常用MySQL管理命令
quit;   退出服务器的连接
show databases;   显示服务器上当前所有的数据库
use 数据库名称;      进入指定的数据库	
show tables;     显示当前数据库中所有的数据表
desc   表名称;     描述表中有哪些列

关系型数据库(RDBMS)：Relation Databse
4.MySQL常用的SQL命令
SQL：SQL: Structured Query Language,结构化查询语言,用于对关系型数据库服务器中的数据进行增删改查的操作。
SQL语言最早是由IBM提出，后提交给了ISO，最终成为了数据库行业的标准语言，分为SQL-87、SQL-92、SQL-99等。
当前标准的SQL命令可以被绝大多数的关系型数据库所支持。
SQL命令的两种执行方式
（1）交互模式：客户端输入一行，点击回车，服务器执行一行。适用于临时性的查看数据。
mysql -uroot 回车
（2）脚本模式：客户端把要执行的命令写在一个文本文件中，一次性的提交给服务器执行。适用于批量的增删改查。
 mysql -uroot <  脚本文件的路径/..../01.sql   回车
SQL语法规范
  （1）每条SQL语句必须以英文的分号结尾，一条语句可以跨越多行，见到分号认为语句结束。
  （2）若第N行语句有错误，则此语句以及后续的语句都不能再执行。
  （3）SQL命令不区分大小写，习惯上数据库关键字用大写，非关键字用小写。
  （4）SQL命令还可以使用单行注释：#...，和多行注释：/*....*/,
注释的代码不会被服务器执行。
日常开发中常用的SQL命令
（1）丢弃指定的数据库，如果存在的话
DROP DATABASE IF EXISTS jd;
（2）创建新的数据库
CREATE DATABASE jd;
（3）进入刚刚创建的数据库
USE jd;
（4）创建保存数据的表
CREATE TABLE student(
 sid INT,
name  VARCHAR(8),
sex  VARCHAR(1),
score  INT
);
（5）向数据表中插入数据
INSERT INTO student VALUES("1","tom","M","80");
（6）查询表中所有数据
select * from student;
（7）修改数据
update student SET score="66",sex="F" where sid="2"
（8）删除数据
delete from student  where sid="3"

# 整型 主键自增
	did INT PRIMARY KEY AUTO_INCREMENT,（primary    increment）
# 查询表中所有数据 
SELECT * FROM demo_t(表名);
# 查询特定的几列
SELECT did ,dtitle FROM demo_t(表名);
# 删除 一列数据
DELETE FROM demo_t(表名) WHERE did = 3;
# 更新一条数据其中的字段
UPDATE demo_t(表名) SET dprice = "3000.00" WHERE did = 1;
# 将表中的某几列 以 中文 显示
SELECT did AS '编号' , dprice AS "价格" FROM demo_t;
```