---
layout: post
title:  "Windows 上安装 Jekyll"
date:   2015-11-05 15:20:35 +0800
categories: [安装jekyll]
---
## Windows 上安装 Jekyll ##

Jekyll是一个静态网站生成工具。它允许用户使用`HTML、Markdown`或`Textile`来建立静态页面，然后通过模板引擎`Liquid`（Liquid Templating Engine）来运行.

原文链接：[Setup Jekyll on Windows](http://yizeng.me/2013/05/10/setup-jekyll-on-windows/)

共分为以下几个重要步骤

1. 安装 `Ruby`
2. 安装 `DevKit`
3. 安装 `Jekyll`
4. 安装 `Pygments` 	
  1. 安装 `Python`
  2. 安装 `‘Easy Install’`
  3. 安装 `Pygments`
5. 启动 `Jekyll`
<!--break-->

## 安装 Ruby ##
1. [下载`rubyinstall`安装文件](http://rubyinstaller.org/downloads/ "下载ruby安装文件")

2. 在 “`RubyInstallers`” 部分，选择某个版本点击下载。
 例如，` Ruby 2.0.0-p451 (x64)` 是适于64位 `Windows` 机器上的 `Ruby 2.0.0 x64 `安装包。

3. 通过安装包安装

  1. 最好保持默认的路径 `C:\Ruby200-x64`， 因为安装包明确提出 “请不要使用带有空格的文件夹 (如： Program Files)”。
  2. 勾选 “`Add Ruby executables to your PATH`”，这样执行程序会被自动添加至 PATH 而避免不必要的头疼。
   `Windows Ruby` 安装包

  ![](http://i.imgur.com/RB4Ti7v.png)


4. 打开一个命令提示行并输入以下命令来检测 Ruby 是否成功安装。
    
 		ruby -v
    
   输出示例：
   
	ruby 2.0.0p451 (2014-02-24) [x64-mingw32]
     
    
## 安装 DevKit ##
DevKit 是一个在 Windows 上帮助简化安装及使用 Ruby C/C++ 扩展如 RDiscount 和 RedCloth 的工具箱。 详细的安装指南可以在程序的wiki 页面 阅读。

 1. [下载devKit](http://rubyinstaller.org/downloads/)

 2. 下载同系统及 Ruby 版本相对应的 DevKit 安装包。 例如，DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe 适用于64位 Windows 系统上的 Ruby 2.0.0 x64。

下面列出了如何选择正确的 DevKit 版本：

	Ruby 1.8.6 to 1.9.3: DevKit tdm-32-4.5.2
    
    Ruby 2.0.0: DevKit mingw64-32-4.7.2
    
    Ruby 2.0.0 x64: DevKit mingw64-64-4.7.2
 3. 运行安装包并解压缩至某文件夹，如 C:\DevKit

 4. 通过初始化来创建 config.yml 文件。在命令行窗口内，输入下列命令：
   		
		cd “C:\DevKit”
    
    	ruby dk.rb init
    
    	notepad config.yml
    	
 5. 在打开的记事本窗口中，于末尾添加新的一行 - C:\Ruby200-x64，保存文件并退出。

 6. 回到命令行窗口内，审查（非必须）并安装。
		
		ruby dk.rb review
    
    	ruby dk.rb install
## 安装 Jekyll ##
 1. 确保 gem 已经正确安装

		gem -v
    
  输出示例：
    
		2.0.14
    
 2. 安装 `Jekyll` `gem`
    
		gem install jekyll
    
## 安装 Pygments ##
Jekyll 里默认的语法高亮插件是 `Pygments`。 它需要安装 `Python` 并在网站的配置文件`_config.yml` 里将 `highlighter` 的值设置为`pygments`。



## 安装 Python ##
1. [下载python安装文件 ](http://www.python.org/download/)
2. 下载合适的 `Python` windows 安装包，如 `Python` 2.7.6 Windows Installer。 请注意，`Python` 2 可能会更合适，  	因为暂时 `Python` 3 可能不会正常工作。
3. 安装
4. 添加安装路径 (如： C:\Python27) 至 PATH。(如何操作? 请参见 故障诊断 #1)
5. 检验 Python 安装是否成功
    
    	python –V
    
   输出示例：
    
		Python 2.7.6
    
## 安装 ‘Easy Install’ ##
1. 浏览 [https://pypi.python.org/pypi/setuptools#installation-instructions](https://pypi.python.org/pypi/setuptools#installation-instructions) 来查看详细的安装指南。
2. 对于 Windows 7 的机器，下载 `ez_setup.py` 并保存，例如，至C:\。 然后从命令行使用 `Python` 运行此文件：
    
    
		python “C:\ez_setup.py”
    
3. 添加 ‘`Python Scripts`’ 路径 (如： C:\Python27\Scripts) 至 PATH
## 安装 `Pygments` ##
1. 确保 easy_install 已经正确安装
    
		easy_install --version
    
  输出示例：
    
		setuptools 3.1
    
2. 使用 “`easy_install`” 来安装 `Pygments`
    
		easy_install Pygments
    
## 启动 Jekyll ##
按照官方的 Jekyll 快速开始手册 的步骤， 一个新的 Jekyll 博客可以被建立并在localhost:4000浏览。
    
    jekyll new myblog
    cd myblog
    jekyll serve
    

