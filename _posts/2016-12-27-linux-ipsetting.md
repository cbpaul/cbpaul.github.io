---
layout: post
title:  "ubuntu设置静态ip"
date:   2016-12-27 14:15:35 +0800
categories: [linux]
---

## ubuntu设置静态ip ##

1. **修改文件如下**


    sudo vim /etc/network/interfaces
 
修改内容如下：

    auto eth0
    iface eth0 inet static #设置为静态
    address 192.168.1.17 #静态ip地址
    gateway 192.168.1.1 #这个地址你要确认下 网关是不是这个地址
    netmask 255.255.255.0 #子网掩码
    broadcast 192.168.1.255 #广播地址

2. **重启网卡**

    sudo /etc/init.d/network restart

3. **通过以上配置如果不能上外网，查看`dns`是否需要配置，修改配置文件**

    sudo vim /etc/resolv.conf

，配置正确的`dns`,然后执行第二步