Ubuntu Server 安装Web服务器（Apache）-(1)
=======================================

## 知识点

* Apache
* Nginx

## 作业内容

### 1)安装Apache服务器

~~~bash
# 安装之前确认一下安装包的信息
$ apt-cache show apache2
# 确认本地TCP端口的使用情况
$ nmap 127.0.0.1
# 开始安装
$ sudo apt-get install apache2
# 再次确认本地TCP端口的使用情况
$ nmap 127.0.0.1
~~~

### 2)Apache配置文件

**配置文件目录：/etc/apache2**

* apache2.conf
 + Apache全局配置文件，记载服务器基本的设置内容，一般轻易不需要改变
* conf-available和conf-enabled（a2enconf,a2disconf）
 + 服务器配置文件，主要用于Apache内部参数的设置，例如：字符集，安全配置等等
* mods-available和mods-enabled（a2enmod,a2dismod）
 + 服务器的模块配置，也就是Apache扩展功能的配置，里面的内容能讲厚厚的一本书，可以说包罗万象，奥妙无穷，但不过如果您不是高级网管的话，其实并不需要全部掌握，看您的发展方向。
* sites-available和sites-enabled（a2ensite,a2dissite）
 + 内部站点的配置，我们可以用一台Apache服务器配置多个站点，同时也可以在这里配置SSL的网站（即：https）。
* envvars
 + 存放环境变量，一般不需要修改。
* magic
 + http传输的多媒体类型设置，一般不需要修改。
* ports.conf
 + 服务器端口配置，一般http为80，https为443，通常不需要改变。

### 3)启用/禁用ssl模块

~~~bash
# 启用模块
$ sudo a2enmod ssl
# 禁用模块
$ sudo a2dismod ssl
# 重启Apache服务
$ sudo service apache2 restart
~~~

### 4)设置服务器名称

~~~bash
$ sudo nano /etc/apache2/apache2.conf
...
ServerName myvideo.com
...
# 重启Apache服务
$ sudo service apache2 restart
~~~

### 5)Apache文档目录修改

~~~bash
$ cd /etc/apache2
$ ll sites-available/
$ ll sites-enabled/
$ sudo a2dissite 000-default
$ sudo nano sites-available/myvideo.conf
...
<VirtualHost *:80>
    ServerName www.myvideo.com
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/myvideo
    ErrorLog ${APACHE_LOG_DIR}/myvideo_error.log
    CustomLog ${APACHE_LOG_DIR}/myvideo_access.log combined
</VirtualHost>
...
$ sudo mkdir -p /var/www/myvideo
$ sudo chown xiaoma:xiaoma -R /var/www/myvideo/
$ cd /var/www/myvideo
$ nano index.html
...html
<!DOCTYPE html>
<html lang="zh">
    <head>
        <meta charset="utf-8">
        <title>小马视频频道</title>
    </head>
    <body>
        <h1>小马视频频道-主站</h1>
    </body>
</html>
...
# 启用刚刚的网站设置
$ sudo a2ensite myvideo
# 重启Apache服务
$ sudo service apache2 restart
~~~

## 课程文件

https://github.com/komavideo/LearnLinux_Old

## 小马视频频道

http://komavideo.com
