---
layout: post
title: Writing your first Django app, part 1.
date: 2016-03-21
categories: blog
tags: [Django, Python, ]
description: Django Demo.
---

[Django 1.8.2文档](http://python.usyiyi.cn/django/intro/tutorial01.html)

创建第一个Django程序，本文为个人读书笔记，为了加深记忆和练习VIM特此记录：

## 创建一个项目

在终端下，cd到你想要用来保存代码的目录，然后运行如下命令：

    $ django-admin startproject mysite

这将会在你的当前目录生成一个mysite目录(使用tree命令生成)

    mysite/
    ├── manage.py
    └── mysite
        ├── __init__.py
        ├── settings.py
        ├── urls.py
        └── wsgi.py

这些文件是：

* 外层的mysite/根目录仅仅是项目的一个容器。它的命名对Django的命名无关紧要；你可以把它重新命名为任何你喜欢的名字；

* manage.py: 一个命令行工具，可以使你用多种方式对Django项目进行交互。

* 内层的mysite/目录是你的项目的真正Python包，它是你导入任何东西时将需要使用的Python包的名字。

* mysite/__init__.py: 一个空文件，它告诉Python这个目录应该被看做一个Python包。

* mysite/setting.py: 该Django项目的设置/配置。[Django设置](http://python.usyiyi.cn/django/topics/settings.html)将告诉你这些设置如何工作。

* mysite/url.py: 该Django项目的URL声明，你的Django站点的目录。你可以在[URL路由器中](http://python.usyiyi.cn/django/topics/http/urls.html)阅读到关于URL的更多内容

* mysite/wsgi.py: 用于你的项目与WSGI兼容的Web服务器入口，更多细节参见[如何利用WSGI进行部署](http://python.usyiyi.cn/django/howto/deployment/wsgi/index.html)

## 数据库的建立：

如果使用sqlite，不需要事先创建任何东西--数据库文件将会在需要的时候自动创建

我这里使用的是mysql，中文，东八区

mysite/setting.py 配置如下(假定你已经创建了一个叫polls的数据库和一个叫jakey的用户)：

	DATABASES = {
		'default': {
			'ENGINE': 'django.db.backends.mysql', 
			'NAME': 'polls',
			'USER': 'jakey',
			'PASSWORD': 'cjs168',
			'HOST': 'localhost',
			'PORT': '3306',
		 }
	}

	LANGUAGE_CODE = 'zh-CN'

	TIME_ZONE = 'Asia/Shanghai'

创建数据库的脚本(init\_polls.sql)：

	drop database if exists polls;
	
	create database polls;

	GRANT ALL ON polls.* TO 'jakey' IDENTIFIED BY 'cjs168';

执行以下命令(输入设置的root的密码)：

	$ mysql -u root -p < init\_polls.sql


默认情况下，INSTALL\_APPS包含下面的应用，它们都是Django与生俱来的：

* django.contrib.admin --管理站点

* django.contrib.auth --认证系统

* django.contrib.contrnttypes --用于内容类型的框架

* django.contrib.sessions --会话框架

* django.contrib.messages --消息框架

* django.contrib.staticfiles --管理静态文件的框架

然而上面的部分应用至少需要使用一个数据库表，因此我们需要在使用它们之前先在数据库中创建相应的表

	$ python manage.py migrate



