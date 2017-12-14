---
layout: blog
title: 对比Laravel5.4 和ThinkPHP5 的区别
date: 2017-08-15 09:23:03
categories: php
tags: 
- laravel
- thinkphp
---

# 对比Laravel5.4 和ThinkPHP5 的区别

## 两者相同部分
1. 使用的`public/index.php`作为项目入口。
2. 使用了`MVC设计思想`。
3. url都使用了`PATHINFO模式`。
4. `命令行模式`。
5. 支持分布式数据库设计。
6. 支持路由模式
7. 支持表单验证机制。
8. 支持缓存
9. 支持错误和日志记录
10. 支持`Mysql`、`SqlServer`、`PgSQL`、`Sqlite`数据库
11. 资源控制器(RESTful)
12. 数据库迁移（migration）
13. 支持模型关联，链式操作
14. 监听SQL
15. 支持多语言
16. 支持redis
xx. ...(目前只发现了这么多，后续有在再补充)

<!-- more -->

**流程图**   
{% asset_img laravel5.4.png laravel %}
{% asset_img tp5.png tp5 %}

> 两者在使用和搭建上大致相同，通过相同的入口文件。类似的配置文件。和差不多的操作。

## 不同点
### Laravel5.4
- 服务容器
> Laravel 务容器是管理类依赖和运行依赖注入的有力工具。依赖注入是一个花俏的名词，它实质上是指：类的依赖通过构造器或在某些情况下通过「setter」方法进行「注入」。
- 服务提供者
> 
- Facades
- Contracts
> 
- 中间件
> Laravel 中间件提供了一种方便的机制来过滤进入应用的 HTTP 请求。
- CSRF 保护
- Blade 模板
- Laravel Mix
- 广播系统
- 集合
- 事件系统
- 消息通知
- 队列
- 任务调度

### ThinkPHP5
- 前置操作
- 行为（Behavior）
- 分页实现


> 详细的对比内容后续补充。