---
layout: blog
title: LINUX PPPoE IPv6的环境搭建
date: 2017-08-15 16:46:56
categories: linux
tags: 
- pppoe server
---

## 设备环境：
- 操作系统：`Centos 7 x64 `
- 使用软件：`ppp` ,  `rp-pppoe`,  `radvd` ,  `kea dhcp`

## 软件安装：
这里使用的在线安装。离线安装的自己去google下安装环境

<!-- more -->

1.	rp-pppoe-3.11-5.el7.x86_64 
2.	ppp-2.4.5-33.el7.x86_64
3.	radvd-1.9.2-9.el7.x86_64

> 当时的版本

安装命令：
```shell
yum install rp-pppoe ppp radvd
```
## 软件配置：

### PPPOE-SERVER

命令 ：` vim /etc/ppp/options`
> (要是这个文件没有自己创建)

```shell
Local
ipv6 ,
# 注意ipv6后面必须要隔一个空格+逗号。去掉会拨号不成功。
```

命令：`vim /etc/ppp/pppoe-server-options`
> (要是这个文件没有自己创建)

```shell
# PPP options for the PPPoE server
# LIC: GPL
require-pap
require-chap
login
+ipv6
lcp-echo-interval 10
lcp-echo-failure 2
logfile /var/log/pppoe.log  
```

命令： `vim /etc/ppp/chap-secrets`
```shell
"test" * "test" *
# "账号" * "密码" * 
```

**启动pppoe命令**：
```shell
pppoe-server -I enp4s0 -L 192.168.5.1 -R 192.168.5.100 -N 20
```
>   
-l ： 后面带的是你需要用作提供pppoe上网的网卡名称。  
-L :   接你的提供服务的地址。  
-R： 接你提供服务的地址池的起始  
-N:   最大可拨号数量。  


### RADVD
命令：`vim /etc/radvd.conf`
```shell
interface enp4s0                #接你拨号上网的网卡名称
{
	AdvSendAdvert on;           #启用路由器公告（RA）功能
	MinRtrAdvInterval 30;       #每隔30-100秒间隔发送公告消息
	MaxRtrAdvInterval 100;
	AdvManagedFlag off;         # M值
	AdvOtherConfigFlag on;      # O值
	prefix 2020:db8:2::/64      #发送的前缀信息
	{
		AdvOnLink on;
		AdvAutonomous on;       #公告的前缀可用来自动位置配置
		AdvRouterAddr off;
	};
};
```

**启动命令**：
```shell
radvd -C /etc/radvd.conf
```
> `-C`的c是大写

### KEA DHCP 
下载链接：[https://www.isc.org/downloads/](https://www.isc.org/downloads/)
官方文档：[ftp://ftp.isc.org/isc/kea/1.2.0/doc/kea-guide.html](ftp://ftp.isc.org/isc/kea/1.2.0/doc/kea-guide.html)  

```shell
# DHCPv6 configuration starts here.
"Dhcp6":
{
    # Add names of interfaces to listen on.
    "interfaces-config": {
    	"interfaces": ["enp4s0","*"]
    },
    "option-data": [ {
    	"name": "dns-servers",
    	"data": "2001::1, 2001::2"
    } ],

......

# The following list defines subnets. Uncomment to enable them.
"subnet6": [
{    
    "subnet": "2017:db8:2::/64",
    "pools": [ { "pool": "2017:db8:2::1-2017:db8:2::ffff" } ],
    "reservations": [
        {
            "duid": "00:03:00:01:f4:28:54:00:15:51",
            "prefixes": [ "2017::/64" ]
        }
    ],
    "interface":"enp4s0"
},


```

**启动命令**：
```shell
kea-dhcp6 -c /etc/kea/kea.conf
```
> （c是小写）,该进程不会后台进行。
