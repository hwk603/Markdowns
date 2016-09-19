layout: windows
title: windows 10 下 apache 80 端口被占用问题
date: 2015-09-12 18:33:04
tags: windows
---

升级windows10后，总体使用感觉还是不错的。然而，今天启动apache的时候，突然发现，之前windows7下可以正常使用的apache突然无法启动了。刚开始以为是升级系统以后配置出错，但重装了apache后发现依然不行；然后怀疑是权限的问题，于是使用管理员身份的控制台去调用命令`net start Apache2.4`，结果还是无法打开。

<!--more-->

手动启动服务报错：


![此处输入图片的描述][1]


我想：干脆执行一下httpd好了。在Apache安装目录的`httpd.exe`的目录下，执行httpd命令。结果：

```
(OS 10013)以一种访问权限不允许的方式做了一个访问套接字的尝试。 : AH00072: make_sock: could not bind to address 127.0.0.1:80
AH00451: no listening sockets available, shutting down
AH00015: Unable to open logs
```

套接字绑定错误，这下可以确定是Apache的80端口被占用了。然后使用命令 `netstat -ano` 来查看一下到底是哪个程序占用了80端口:

![此处输入图片的描述][2]

可以看到80端口被PID为4的System进程占用。什么鬼？！这时候千万不要尝试终结此进程，会蓝屏，【别问我怎么知道的】。

网上找到的解除System进程对80端口占用的方法：

 - 打开注册表，在cmd下输入：`regedit`。

 - 找到：`HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\HTTP`。

 - 在右边找到`Start`这一项，将其改为0。

 - 重启系统，System进程不会占用80端口。


浏览器输入`http://127.0.0.1`，成功！

![此处输入图片的描述][3]
    


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/Apacheerro1.gif
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/pid.JPG
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/localhost.JPG