---
layout: post
title:  "mac 上安装 Jekyll"
date:   2015-11-09 10:15:35 +0800
categories: [安装jekyll]
---
## mac 上安装 Jekyll ##
mac os自带`ruby` 和 `gem`
 更新gem

    $ sudo gem update --system

 安装 `jekyll`

	$sudo gem install jekyll

	
这里有个问题由于国内墙了`ruby` `gem` 的镜像下载源,因此需要更   改镜像地址命令如下：

<!--break-->

 删除原有的镜像

	$ gem sources --remove https://rubygems.org/

 添加淘宝下载源

	$ gem sources -a http://ruby.taobao.org/

 查看

	$ gem source -l

这样就算完成了`jekyll`安装

