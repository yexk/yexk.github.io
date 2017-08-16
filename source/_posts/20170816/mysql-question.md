---
layout: blog
title: MySQL遇到的问题
date: 2017-08-16 11:40:26
categories: Mysql 
tags: 
- mysql
- 常见问题
---

## mysql5.7中datetime默认值设置0000-00-00失败的问题
> 问题：mysql5.7之后版本datetime默认值设置'0000-00-00'，出现异常：Invalid default value for 'create_time'

```mysql
-- 例如这个表格：
DROP TABLE IF EXISTS `test`;
CREATE TABLE `test` (
  `id` int(11) NOT NULL AUTO_INCREMENT COMMENT '自增ID',
  `time` datetime NOT NULL DEFAULT '0000-00-00 00:00:00' COMMENT '添加时间',
  PRIMARY KEY (`id`)
);
```
添加的时候就会报错： 
{% asset_img mysql_default_value.jpg %}

这个时候在MySQL的配置文件的`[mysqld]`中加入：
`sql_mode=STRICT_TRANS_TABLES,NO_ZERO_IN_DATE,NO_ZERO_DATE,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION`
{% asset_img mysql_default_value_conf.jpg %}

最后重启再导入就行了。

> 附上原文链接 http://blog.csdn.net/sd4493091/article/details/54947851 (此处对原文稍作修改)


## MySQL解决[Err] 1206 - The total number of locks exceeds the lock table size问题
> 默认缓冲区的文件大小问题。。

在配置文件改成一个较大的大小就行。
```
innodb_buffer_pool_size = 2G
```

## mysql的蠕虫复制
```mysql
insert into test1 (name) select name from test1;	
```

# 开启远程访问
在本机先使用root用户登录mysql： mysql -u root -p"youpassword" 进行授权操作：

```shell
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'youpassword' WITH GRANT OPTION;
```

重载授权表：

```shell
FLUSH PRIVILEGES;
```