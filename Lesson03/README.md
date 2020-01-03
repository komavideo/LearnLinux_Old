Ubuntu Server 系统更新
=====================

## 知识点

* 系统更新设置文件
* 系统更新手动命令

### 系统更新设置文件

**系统更新设置文件**
~~~
#sudo apt-get install unattended-upgrades
#自动更新
/etc/apt/apt.conf.d/50unattended-upgrades
~~~

**更新文件源**
~~~
/etc/apt/sources.list
~~~

### 系统更新手动命令

~~~bash
#更新文件源（/etc/apt/sources.list）
$ sudo apt-get update

#检查文件源的版本，如果软件版本更新的话则提示用户是否更新
$ sudo apt-get upgrade

#Ubuntu核心等文件的更新（用户可自行选择是否更新）
$ sudo apt-get dist-upgrade

#服务器重新启动（推荐）
$ sudo reboot
~~~

## 作业内容

建立一个自己的系统更新文件

~~~bash
$ cd
$ nano up
...
sudo apt-get update
sudo apt-get upgrade
...
$ chmod +x up
$ ./up
~~~

## 课程文件

https://github.com/komavideo/LearnLinux_Old

## 小马视频频道

http://komavideo.com
