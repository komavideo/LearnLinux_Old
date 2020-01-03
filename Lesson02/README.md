Ubuntu Server 网络设置
=====================

## 知识点

* TCP/IP（网络传输协议:IPv4 or IPv6）
* Ubuntu网络设置文件
 + /etc/network/interfaces

## 作业内容

Ubuntu Server服务器IP地址设置

### (0)网址确定
~~~bash
$ ifconfig
~~~

### (1)编辑网络适配器（网卡）文件
~~~bash
$ cd /etc/network
$ sudo nano interfaces

...
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth0
iface eth0 inet static
address 192.168.11.200
netmask 255.255.255.0
network 192.168.11.0
broadcast 192.168.11.255
gateway 192.168.11.1
dns-nameservers 192.168.11.1
...
~~~

### (2)重新启动服务器
~~~bash
#网卡服务再启动（不推荐）
#sudo service networking restart

#OS再启动（推荐）
$ sudo reboot
~~~

### (3)服务器重新启动后确认IP地址设置
~~~bash
$ ifconfig
~~~

## 课程文件

https://github.com/komavideo/LearnLinux_Old

## 小马视频频道

http://komavideo.com
