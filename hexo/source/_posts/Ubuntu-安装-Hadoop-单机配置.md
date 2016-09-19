title: Ubuntu 安装 Hadoop 单机配置
date: 2016-03-25 13:50:22
tags: hadoop
---

### 介绍

Hadoop 是 Apache 软件基金会旗下的一个开源分布式计算平台，用于开发在分布式计算环境中执行的数据处理应用程序。它以 Hadoop 分布式文件系统（`Hadoop Distributed File System`，`HDFS`）和`MapReduce`（`Google MapReduce`的开源实现）为核心，为用户提供系统底层细节透明的分布式基础架构。

![hadoop][1]

<!--more-->

### 环境要求

- Java，必须安装，Hadoop 框架使用 java 编写的。
- ssh，必须安装并且保证 sshd一直运行，以便用Hadoop 脚本管理远端Hadoop守护进程。

### 安装

- 安装依赖
```
$ sudo apt-get update
//更新源

$ sudo apt-get install default-jdk
//安装 java jdk

$ java -version
//查看 java 版本

$ sudo addgroup hadoop
//添加 hadoop 的用户组

$ sudo adduser --ingroup hadoop hduser
//添加 hduser 的用户

$ sudo apt-get install openssh-server
//安装 ssh

$ su hduser
//切换 用户

$ ssh-keygen -t rsa -P ""
//创建新的密钥

$ cat $HOME/.ssh/id_rsa.pub >> $HOME/.ssh/authorized_keys
//使用此密钥启用SSH访问本地计算机

$ ssh localhost
//测试SSH设置通过“hduser”用户连接到locahost

```
---
ps. 如果执行`ssh localhost`时看到下面的错误响应:

`ssh: connect to host localhost port 22: Connection refused`

![][2]

则可能是以下几个原因：

1. sshd 未安装
2. sshd 未启动
3. 防火墙
4. 需重新启动ssh 服务

我安装的时候已经安装了sshd，执行`which ssh`和`which sshd`可以看到：

![][3]

然后也没安装防火墙，肯定不是防火墙的事情，于是执行`ps -e | grep sshd`，才发现 sshd 没有运行，所以执行`/etc/init.d/ssh start`启动 sshd。

最后再执行`ssh localhost`就成功了。

![此处输入图片的描述][4]

---

- 安装 Hadoop

```
$ wget http://apache.fayea.com/hadoop/common/hadoop-2.7.2/hadoop-2.7.2.tar.gz 
//获取 Hadoop 的2.7.2的二进制包
$ tar xvzf hadoop-2.7.2.tar.gz -C /usr/local
//解压到/usr/local目录
$ sudo mv ./hadoop-2.6.0/ ./hadoop
//修改文件名
$ sudo chown -R hadoop:hadoop ./hadoop
//给予可执行权限
$ cd /usr/local/hadoop
$ ./bin/hadoop version
//如果安装成功，会显示版本信息

```

---

意外发现几篇很良心的博客，mark一下：

[Hadoop安装教程_单机/伪分布式配置_Hadoop2.6.0/Ubuntu14.04][5]

[Hadoop安装教程_单机/伪分布式配置_CentOS6.4/Hadoop2.6.0][7]

[Hadoop集群安装配置教程_Hadoop2.6.0_Ubuntu/CentOS][6]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/1-1509130T21H15.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/hadoopImage%201.png
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/hadoopImage%203.png
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/hadoopImage%202.png
  [5]: http://www.powerxing.com/install-hadoop/
  [6]: http://www.powerxing.com/install-hadoop-cluster/
  [7]: http://www.powerxing.com/install-hadoop-in-centos/