Ubuntu Server 包管理
===================

## 知识点

* 包管理文件
* 包管理命令

### 包管理文件

~~~bash
/etc/apt/sources.list
~~~

**Nginx源设置**

~~~bash
$ sudo nano /etc/apt/sources.list
...
deb http://nginx.org/packages/ubuntu/ trusty nginx
deb-src http://nginx.org/packages/ubuntu/ trusty nginx
...
$ sudo apt-get update
$ sudo apt-get upgrade
~~~

### 包管理命令

* apt-get
 + 软件包安装，删除等维护工作，它帮我们解决了软件包之间的依赖问题，类似RedHat系统的rpm
* apt-cache
 + 软件包信息查看工具，比如：软件查找，信息确认等等
* tasksel
 + 软件包安装任务，可以帮咱们一次安装一套软件包，比如：LAMP服务器等（Apache+MySql+PHP）
* dpkg
 + 与apt-get类似的包管理工具，但更加底层，可以执行很多apt-get不能执行的功能

**apt-get常用命令选项**

| 命令选项 | 功能描述 |
|:-------|:--------|
| update          | 软件包列表更新 |
| upgrade         | 软件包安装更新 |
| install         | 安装软件包 |
| remove          | 卸载软件包 |
| autoremove      | 自动删除不在需要的下载包 |
| purge           | 永久删除一个软件包，包括设置文件等 |
| source          | 下载源码包 |
| build-dep       | 为某个软件包设置编译依赖 |
| dist-upgrade    | 系统核心更新或某个软件包更新 |
| clean           | 删除本地缓存文件 |
| autoclean       | 删除本地不再使用缓存文件 |
| check           | 检查软件包的依赖关系 |
| changelog       | 下载显示软件包的更新履历 |
| download        | 下载指定软件包到当前目录 |

## 作业内容

安装一个网络扫描工具nmap

~~~bash
$ cd
# nmap软件包信息查看
$ apt-cache show nmap
# 安装nmap软件包
$ sudo apt-get install nmap
$ nmap www.google.com
# 卸载nmap软件包
$ sudo apt-get purge nmap
$ nmap www.google.com
~~~

## 课程文件

https://github.com/komavideo/LearnLinux_Old

## 小马视频频道

http://komavideo.com
