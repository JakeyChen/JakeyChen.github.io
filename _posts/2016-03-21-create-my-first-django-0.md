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

数据库的建立：


