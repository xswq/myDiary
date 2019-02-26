# 可视化，不局限与命令行

使用Intelij DataGrip

# 建表

`create table 表名称(列声明);`

例：

```sql
create table t_coffee (
    id bigint not null auto_increment,
    name varchar(255),
    price bigint not null,
    create_time timestamp,
    update_time timestamp,
    primary key (id)
);
```

表名，可以 t_name 的形式处理

column，不同的单词用 _ 分隔

默认null，不可以为null，必须需要赋值的 not null 

在命令行之下输入较长语句易出错，一般可以在编辑器中保存为 createtable.sql 之类的文件，

 `mysql -D samp_db -u root -p < createtable.sql`

**提示1:** 

1. 如果连接远程主机请加上 -h 指令; 
2. createtable.sql 文件若不在当前工作目录下需指定文件的完整路径。

**提示2:** 

1. 使用 show tables; 命令可查看已创建了表的名称; 
2. 使用 describe 表名; 命令可查看已创建的表的详细信息。

# 插入

例：

```sql
insert into t_coffee (name, price, create_time, update_time) values ('espresso', 2000, now(), now());
insert into t_coffee (name, price, create_time, update_time) values ('latte', 2500, now(), now());
insert into t_coffee (name, price, create_time, update_time) values ('capuccino', 2500, now(), now());
insert into t_coffee (name, price, create_time, update_time) values ('mocha', 3000, now(), now());
insert into t_coffee (name, price, create_time, update_time) values ('macchiato', 3000, now(), now());
```

insert into t_name (column_name…) values (value...)

now()，为sql函数调用

# 查询

`select 列名称 from 表名称 [查询条件];`

例：

查询名字中带有 "王" 字的所有人信息: 

`select * from students where name like "%王%";`

# 更新

`update 表名称 set 列名称=新值 where 更新条件;`

将id为5的手机号改为默认的"-": 

`update students set tel=default where id=5;`

# 删除

`delete from 表名称 where 删除条件;`

删除所有年龄小于21岁的数据: 

`delete from students where age<20;`

# 对表结构修改

* 添加
  * `alter table 表名 add 列名 列数据类型 [after 插入位置];`
  * 在表的最后追加列 address: `alter table students add address char(60);`

* 修改
  * `alter table 表名 change 列名称 列新名称 新数据类型;`
  * 将 name 列的数据类型改为 char(16): `alter table students change name name char(16) not null;`
* 删除
  * `alter table 表名 drop 列名称;`
  * 删除 birthday 列: `alter table students drop birthday;`
* 重命名
  * `alter table 表名 rename 新表名;`
  * 重命名 students 表为 workmates: `alter table students rename workmates;`

# 使用数据库

## 登录Mysql

`mysql -h 主机名 -u 用户名 -p`

* -h
  * 命令用于指定客户端所要登录的MySQL主机名, 登录当前机器该参数可以省略;

* -u
  * 登录的用户名

* -p
  * 告诉服务器将会使用一个密码来登录, 如果所要登录的用户名密码为空, 可以忽略此选项。

本机下，直接`mysql -u root -p`

输入密码即可

最后 exit / quit 来退出

## 创建数据库

`create database 数据库名 [其他选项];`

其他选项：像设置数据库字符编码，

`create database samp_db character set utf-8;`

可以使用 `show databases;` 命令查看已经创建了哪些数据库;

## 选择数据库

* 在登录数据库时指定, 命令: `mysql -D 所选择的数据库名 -h 主机名 -u 用户名 -p`
  * mysql -D samp_db -u root -p

* 在登录后使用 use 语句指定, 命令: `use 数据库名;`

## 密码

打开命令提示符界面, 执行命令: `mysqladmin -u root -p password 新密码`