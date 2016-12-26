---
layout: post
title:  "http安全"
date:   2016-12-23 16:15:35 +0800
categories: [web,security,web安全]
---

## WEB安全问题 ##

1. XSS跨站脚本攻击(Cross Site Scripting)，执行用户脚本

	如：通过页面一些简单的表单输入框，进行javascript脚本攻击,下面这断代码没有对输入框进行字符检验或转义

	    <script src="jquery-1.11.1.min.js"></script>
    用户输入：<input type="text" id="in">
    	<button id="sub">提交</button>
    	<div id="showIn">
    
    	</div>
    <script>
    	$(function(){
    		$("#sub").click(function(){
    			console.info(document.cookie)
    			$("#showIn").html($("#in").val());
    		});
    	})
    </script>
	

2. CSRF(Cross-site request forgery)跨站请求伪造 

	相当攻击者盗用了你的身份，以你的名义发送恶意请求。如现在有A站与B站（恶意网站）,用户在A站登录成功后。这时B站也处于打开状态，然而B站通过某种方式得到了A站相关操作请求（如：退出登录），用户并不相退出A站，但可不小心点到了B站的某个图片或按钮之类的。这些图片或按钮就会发送一个退出登录。


3. sql注入（服务器代码漏洞）
	
	服务器sql是通过字符串拼接的方式，如下：

	`select * from table where id="+variable+";`
	
	假如variable变量传入1是正常查询的值，但如果用户传入 1 or
1=1 这样就能把所有数据查出来
	
	解决办法是通过参数化，参数化如：
	
	`select * from table where id=:variable;`
	
	这个variable会根据参数的类型进行替换，如是int那必然是id=1
大家会问那是字符串不是也一样会有吗？其实不会，字符串会被参数化成`1 or 1=1`，这是一个字符串值，而不会当成sql语义执行


4. 伪造请求

	通过抓包工具（[SmartSniff](http://211.162.213.122:9011/www.nirsoft.net/c3pr90ntc0td/utils/smsniff-x64.zip "小巧绿包抓包工具")），通过分析请求内容，可以得到请求参数，请求头等等。如用户通过http进行登录操作，由于http是明文，因此能得到用户输入的账号与密码，如果网站是通过cookie来保存用户session这样还能通过sessionId来发送伪请求。
 
5. https安全通信(TLS/SSL)

	安全主要加密，身份认证。


   1）加密运用对称加密与非对称加密

对称加密：使用同样的密匙进行加密与解密操作，加密速度快。有个缺点就是如何传输这个密匙，如客户端在传输密匙有可能被别人抓包得到。

非对称加密：
 
   2）身份认证   

需要做https服务端向，颁发证书的机构申请。
 
   3)数据完整性
