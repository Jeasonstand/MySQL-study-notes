### 1、什么是数据库？

    DataBase   简称：DB
    
    用于存储和管理数据的仓库.

SQL、DB、DBMS分别是什么，他们之间的关系？

	DB: 
		DataBase（数据库，数据库实际上在硬盘上以文件的形式存在）
	
	DBMS: 
		DataBase Management System（数据库管理系统，常见的有：MySQL Oracle DB2 Sybase SqlServer...）
	
	SQL: 
		结构化查询语言，是一门标准通用的语言。标准的sql适合于所有的数据库产品。
		SQL属于高级语言。只要能看懂英语单词的，写出来的sql语句，可以读懂什么意思。
		SQL语句在执行的时候，实际上内部也会先进行编译，然后再执行sql。（sql语句的编译由DBMS完成。）


​	
	DBMS负责执行sql语句，通过执行sql语句来操作DB当中的数据。
	
	DBMS -(执行)-> SQL -(操作)-> DB

特点：

    1.持久化存储数据的。其实数据库就是一个文件系统
    2.方便存储和管理数据
    3.使用了统一的方式操作数据库 --SQL

什么是表？

	表：table
	
	表：table是数据库的基本组成单元，所有的数据都以表格的形式组织，目的是可读性强。
	
	一个表包括行和列：
		行：被称为数据/记录(data)
		列：被称为字段(column)
		
	学号(int)	姓名(varchar)	年龄(int)
	------------------------------------
	01			张三				20
	02			李四				21

每一个字段应该包括哪些属性？

		字段名、数据类型、相关的约束。

### 2、SQL语句分类

    DQL（数据查询语言）: 查询语句，凡是select语句都是DQL。
    DML（数据操作语言）：insert delete update，对表当中的数据进行增删改。
    DDL（数据定义语言）：create drop alter，对表结构的增删改。
    TCL（事务控制语言）：commit提交事务，rollback回滚事务。(TCL中的T是Transaction)
    DCL（数据控制语言）: grant授权、revoke撤销权限等。

### 3、登录MySQL

    mysql> mysql -u root -p123123

### 4、查看有哪些数据库

    mysql> show databases；

### 5、创建属于我们自己的数据库

    mysql> create datebase testdemo;

### 6、使用testdemo数据库

    mysql> use testdemo; 

### 7、查看当前使用的数据库中有哪些表

    mysql> show tables;

### 8、初始化数据

    mysql> source D:\course\MySQL\resources\testdemo.sql
    
    注： testdemo.sql，这个文件以sql结尾，这样的文件被称为“sql脚本”。什么是sql脚本呢？
    当一个文件的扩展名是.sql，并且该文件中编写了大量的sql语句，我们称这样的文件为sql脚本。
    
    注意：直接使用source命令可以执行sql脚本。
    
    sql脚本中的数据量太大的时候，无法打开，请使用source命令完成初始化。

### 9、删除数据库

    mysql> drop database testdemo;

### 10、查看表结构

    mysql> desc 表名

### 11、表中的数据

    mysql> select * from demo;

### 12、查看创建表的语句

    mysql> show create table demo;

### 13、常用命令

###### 查看当前使用的是哪个数据库

```
mysql> select database();
```

###### 查看mysql的版本号

```
mysql> select version();
```

###### 结束一条语句

```
mysql> \c
```

###### 退出mysql数据库服务器

```
mysql> exit
```



### 14、简单的查询语句（DQL）

	语法格式：
		select 字段名1,字段名2,字段名3,.... from 表名;
	
	提示：
		1、任何一条sql语句以“;”结尾。
		2、sql语句不区分大小写。
### 15、条件查询

###### 	语法格式：

​				select 
​									字段,字段...
​				from
​									表名
​				where
​									条件;

​	执行顺序：先from，然后where，最后select

### 16、排序（升序、降序）

###### 	语法格式：

	        select 
	            		字段				    3
	        from
	            		表名				    1
	        where
	            		条件				    2
	        order by
	            		....			     4
		
	        order by是最后执行的。
​	注意：默认是升序。怎么指定升序或者降序呢？asc表示升				序，desc表示降序。

### 17、分组函数？

​			count 计数
​			sum 求和
​			avg 平均值
​			max 最大值
​			min 最小值

记住：所有的分组函数都是对“某一组”数据进行操作的。

### 18、单行处理函数

​			什么是单行处理函数？
​					输入一行，输出一行。

### 19、group by 和 having

​			group by ： 按照某个字段或者某些字段进行分组。
​			having : having是对分组之后的数据进行再次过滤。

​	注意：分组函数一般都会和group by联合使用，这也是为什么				它被称为分组函数的原因。
​				并且任何一个分组函数（count sum avg max min）都				在group by语句执行结束之后才会执行的。
​				当一条sql语句没有group by的话，整张表的数据会自成				一组。

​	记住一个规则：当一条语句中有group by的话，select后面只				能跟分组函数和参与分组的字段。

### 20、总结一个完整的DQL语句怎么写

	          select					5
							..
	          from						1	
							..
	          where						2
							..
	          group by					3
							..
	          having					4
	               			..
	          order by					6






