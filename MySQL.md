# MySQL
[学习视频](https://www.bilibili.com/video/BV1Vy4y1z7EX?spm_id_from=333.788.videopod.episodes&vd_source=15928c34608bc5de5fee0e613999a322)
[提供测试的数据库](./bjpowernode.sql)

数据库中最基本的单元是表： table
	行（row）：被称为数据/记录
	列（column）：被称为字段
每个字段都有：字段名、数据类型、约束等属性

### 常用命令
不区分大小写
+ show databases; 
+ show tables;
+ use <name>; 
+ create database <name>; 
+ select database()；
+ select  *  from <tablename>;
+ source <path>; 添加sql到数据库中
+ desc <tablename>;看表结构
+ select version();查看版本号
+ exit

### SQL语句的分类
+ DQL：
	数据查询语言（凡是带有select关键字的都是查询语句）
	select...
+ DML：
	数据操作语言（凡是对表当中的数据进行增删改的都是DML）
	insert
	delete
	update
+ DDL：
	数据定义语言（凡是带有create、drop、alter的都是DDL）
	DDL主要操作的是表的结构，不是表中的数据。
	create
	drop
	alter
+ TCL：
	事务控制语言
	包括：
		事务提交：commit;
		事务回滚：rollback;
+ DCL：
	数据控制语言
	例如：授权grant、撤销权限revoke
	
### DQL
#### 简单查询
+ select 字段名 from 表名;
	其中要注意：
		select和from是关键字
		字段名和表名是标识符
+ select 字段名, 字段名 from 表面;两个字段名间用“ ，”隔开
+ select * from 表名;
#### 列(column)起别名
+ select 字段名 as 别名 from 表名；
	用as关键字起别名
	注意：只是显示列名为别名，不修改原表列名
	且as可以省略为空格
#### 列参参与计算
+ select 字段名 * 数字 from 表名;
#### 条件查询
+ select 字段1，字段2，字段3...from 表名 where 条件;
  = 等于
  <> 或 ！= 不等于
  < 小于
  <= 小于等于
  \> 大于
  \>= 大于等于
  between ... and ... 两个值之间( >= and <=) 
  	注意：必须左小右大
  is null 为 null(is not null 不为空)
  	注意：在数据库当中null不能使用等号进行衡量
  and 并且
  or 或者
  	优先级：and的优先级比or高，需要加括号
  in 包含，相当于多个or(not in 不在这个范围中)
  	注意：in不是区间，是具体的值
  like 模糊查询，支持%或下划线匹配
  	%和_是特殊符号，%:任意多个字符，_:任意一个字符
	\转义字符
#### 排序
+ select 字段名 from 表名 order by 字段名; 默认升序
+ select 字符名 from 表名 order by 字段名 desc; 指定降序
+ select 字符名 from 表名 order by 字段名 asc; 指定升序
按多个字段排序
+ select 字符名 from 表名 order by 字段名1 asc, 字段名2 asc;
	字段名1起主导作用
+ select 字符名 from 表名 order by 2;
	按照查询结果的第二列排序，不建议使用，因为列顺序会变

**注意**
select ... from ... where ... order by ...关键字顺序不能变
执行顺序 1.from 2.where 3.select 4.order by

#### 数据处理函数（单行处理函数）
特点：一个输入对应一个输出
和单行处理函数相对应的是：多行处理函数（多行处理函数：多个输入对应一个输出）
+ lower 转成小写
+ upper 转成大写
+ substr 取子串
+ 
