---
layout: post
title: 探索mysql
date: 2019-03-22 15:29:00 +0800
categories: db
---

## 命令行查询显示方式

```
mysql> pager less -SFX
mysql> SELECT * FROM sometable;
```
或
```
SELECT * FROM sometable\G
```

* [command line - How to best display in Terminal a MySQL SELECT returning too many fields? - Stack Overflow](https://stackoverflow.com/q/924729)

## Show语法

```
SHOW TABLES WHERE Tables_in_<DatabaseName> NOT LIKE 'tree%';
```

* [mysql: What is the right syntax for NOT LIKE? - Stack Overflow](https://stackoverflow.com/q/3698891)

## 锁

* [mysql的锁--行锁，表锁，乐观锁，悲观锁 - 浅井光一 - 博客园](https://www.cnblogs.com/deliver/p/5730616.html)
