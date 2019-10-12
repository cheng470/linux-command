MySQL 数据库

# 例子

```sh
# 连接本地数据库
mysql -h 127.0.0.1 -p
```

## 查触发器

```sh
mysql> use sigdb;

# 查看当前库所有触发器
mysql> show triggers;
mysql> show triggers\G

# 查看所有库的触发器
mysql> select * from information_schema.triggers\G

# 查看指定数据库的触发器
mysql> select * from information_schema.triggers where trigger_schema='sigdb'\G

# 查看指定数据库的触发器，只显示触发器名称
mysql> select trigger_name from information_schema.triggers where trigger_schema='sigdb';
```

# 文档

[MySQL :: MySQL Documentation](https://dev.mysql.com/doc/)