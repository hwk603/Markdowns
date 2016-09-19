title: "windows 下 docker-machine 启动失败"
date: 2016-04-25 20:30:15
tags: Docker Toolbox
---

自从某次 windows 自动更新以后，启动 docker toolbox 的时候就会出现以下问题：

```
$ docker-machine start default
//error:
Machine default already exists in VirtualBox. 
Setting environment variables for machine default...
                    ##         .
              ## ## ##        ==
           ## ## ## ## ##    ===
       /"""""""""""""""""\___/ ===
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
       \______ o           __/
         \    \         __/
          \____\_______/
Error getting IP address: Something went wrong running an SSH command!
command : ip addr show dev eth1
err : exit status 255
output : 
docker is configured to use the default machine with IP For help getting started, check out the docs at https://docs.docker.com 

Error running connection boilerplate: Error getting driver URL: Something went wrong running an SSH command!
command : ip addr show dev eth1
err : exit status 255
output :

```

<!--more-->

之后，删除虚拟机，重建：

```
$ docker-machine rm default
$ docker-machine create --driver virtualbox default
```

会出现错误如下：

```
This computer doesn't have VT-X/AMD-v enabled. Enabling it in the BIOS is mandatory
```

然后直接去 Virtualbox 虚拟机中去，发现 VT-X/AMD-v 硬件加速不可用。

![][1]

猜测 windows 上其他程序接管了 VT-X/AMD-v 硬件加速，查看了一下 windows 的更新日志，发现罪魁祸首是 Hyper-V，去 windows 程序与功能 —— 启用或关闭 windows 功能，关闭 Hyper-V，重启 windows 。

成功！！！

  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-04-25%201461586814.png
  
