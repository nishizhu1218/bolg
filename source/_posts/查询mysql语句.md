---
title: 查询,约束mysql语句
date: 2018-12-01 15:53:24
tags:
---
```
以下是mysql查询，约束的语句，加油！！
列约束
（1）主键约束——PRIMARY KEY
（2）唯一约束——UNI
（3）非空约束——NOT NULL
声明了非空约束的列上不能插入null
（4）默认值约束——DEFAULT
可以使用DEFAULT 关键字声明默认值，有两种方式可以应用默认值
INSERT INTO xz_laptop_family VALUES(40,"苹果",DEFAULT);
INSERT INTO xz_laptop_family VALUES()
zhangsan@tedu.cn   123456
chengliang@tedu.cn  123456
（检查约束)——CHECK
     检查约束可以对插入的数据进行检验
CREATE TABLE student（
age TINYINT(age>=18 AND age<=60)
 ）;
mysql不支持检查约束，会降低数据的插入速度。
（6）外键约束——FOREIGN KEY
声明了外键约束的列，取值必须在另一个表的主键列上出现过，列类型要保持一致，取值可以是NULL
FOREIGN KEY(familyid)
REFERENCEAS xz_laptop_family(fid)
2.MySQL中的自增列
auto_INCREMENT（increment）：自动增长，加入一个列声明了自增列，无需手动复制，直接设置为NULL，会获取当前的最大值，然后加1插入。
注意：
        自增列允许手动赋值
        只适用于整数型的主键列上
        sql中提供了两个模糊查询的字符
% 可以匹配任意多个字符  >=0
_  可以匹配任意一个字符  =1
注意：以上的这两个匹配不能和=使用，必须要使用LIKE关键字
（9）分页查询
     假如查询的结果集中有太多的数据，一次显示不完，可以分页显示
需要有两个条件 ：当前的页码、每页的数据量
SELECT * FROM emp LIMIT  start,count;
start: 是一个数字，从结果集中的哪1条开始读取，第1条 称为0 
count：是一个数字，最多读取的行数
每页开始的算法
start=(页码-1)*count
假设每一页显示5条记录
第一页：SELECT *FROM emp LIMIT 0,5;
第二页：SELECT *FROM emp LIMIT 5,5;
第三页：SELECT *FROM emp LIMIT 10,5;
第四页：SELECT＊FROM emp LIMIT 15.5;
假设每一页显示6条记录
第一页：SELECT * FROM emp LIMIT 0,6;
第二页:  SELECT * FROM emp LIMIT 6,6;
```