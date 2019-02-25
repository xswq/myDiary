# 建表

例：

```sql
create table t_coffee (
    id bigint not null auto_increment identity,
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

