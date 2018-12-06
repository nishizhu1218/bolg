---
title: mysql标准语句分类
date: 2018-12-06 22:45:20
tags:
---
```
DDL：Data Define Language  定义数据
	 CREATE/DROP/ALTER 
DML:Data Munipulate Language   操作数据
			操作
	 INSERT/DELETE/UPDATE
DQL:Data Query Language   查询数据
		 查询
	 SELECT
DCL：Data control Language 控制用户权限
     GRANT（授权）某个人去管理某个数据库
	 REVOKE(收权)


1.计算机存储字符
（1）如何存储英文字符
	ASCII（美国人发明）:总共128个，对所有的英文字符及其标点符号进行编码
	HEllo ->72102108108111
	Latin-1(欧洲人发明)：总共有256个，兼容ASCII码，同时对欧洲符号进行了编码。MySQL默认使用这种编码。
（2）如何存储中文字符
	GB2312 对常用的6千多汉字进行了编码，兼容ASCII码
	GBK 对2万多个汉字进行了编码，兼容GB2312
	BIG5 台湾繁体字编码
	Unicode 对世界上主流的语言常用的字符进行了编码，兼容了ASCII，不兼容GBK,GB2312，BIG5 等系列。
		具体分为UTF-8、UTF-16、UTF-32等存储方案。
（3）解决MySQL存储中文乱码
	sql脚本文件存储的编码utf 8
	客户端连接服务器端使用的编码为utf8
	服务器端创建数据库存储使用的编码为utf8
    2.MySQL中的列类型
创建数据表的时候，指定的列可以存储的数据类型。
CREATE TABLE book(bid   列类型)；

（1）数值类型
TINYINT  微整型，占1个字节  范围-128~127
SMALLINT  小整型  占2个字节  范围-32768~32767
INT  整型， 占4个字节  范围-2147483648~2147483647
BIGINT  大整型，占8个字节
FLOAT   单精度浮点型，占4个字节，范围3.4e38，范围比INT大得多，可能产生计算误差。
DOUBLE  双精度浮点型，占8个字节，范围比BIGINT大得多
DECIMAL  (M,D) 定点小数， 不会产生计算误差，M代表总的有效位数，D代表小数点后的有效位数
BOOL 布尔型，只有两个结果 TRUE/1、FALSE/0  TRUE  FALSE不能添加引号；真正存储数据的时候，会使用TINYINT。

（2）日期时间类型——必须添加引号
DATE  日期型  "2018-12-31"
TIME 时间型   "14:22:30"
DATETIME 日期时间型  "2018-12-31    14:22:30"
（3）字符串类型——必须添加引号
VARCHAR(M)   变长字符串，不会产生空间浪费，操作速度相对较慢，M最大值是65535
CHAR（M） 定长字符串，可能产生空间浪费，操作速度较快，M最大值是255；用于存储手机号码，身份证号等固定长度的字符。
TEXT（M）大型变长字符串，最多存2G
CREATE TABLE t1(
	id  SMALLINT,
	age  TINYINT,
	commentCount INT,
	price  DECIMAL(6,2),
	phone  CHAR(11),
	article  VARCHAR(8000),
	pubTime  DATE
);
```