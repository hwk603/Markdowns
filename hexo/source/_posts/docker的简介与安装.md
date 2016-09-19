title: docker 的简介与安装
date: 2016-02-26 22:24:34
tags: docker
---

## 简介

docker 是一个基于 go 语言的开源项目，其目的是实现轻量级的操作系统虚拟化解决方案。

<!--more-->

## 安装

### ubuntu 14.04

- 系统要求

```
$ uname -a
//获取系统内核版本
//Docker 目前支持的最低 Ubuntu 版本为 12.04 LTS
//Docker 目前只能按照在 64 位平台上，并且要求内核版本不低于 3.10

```

- 安装命令：

```
    
$ sudo apt-get install -y linux-image-extra-$(uname -r)
//使 docker 支持 aufs 存储方式。
    
$ sudo apt-get install -y apt-transport-https
//添加支持 https 的镜像源。
    
$ sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
//添加源的 gbg 密钥。
    
$ lsb_release -c
//获取当前操作系统代号，一般来说：12.04 (LTS) 代号为 precise，14.04 (LTS) 代号为 trusty，15.04 代号为 vivid，15.10 代号为 wily。
    
$ sudo cat <<EOF > /etc/apt/sources.list.d/docker.list
deb https://apt.dockerproject.org/repo ubuntu-代号 main
EOF
//添加 docker 的官方 apt 软件源
    
$ sudo apt-get update
//更新 apt 软件包缓存。
    
$ sudo apt-get install -y docker-engine
//安装最新的 docker 版本。
    
```

### centos 7.0

- 系统要求
```
$ uname -a
//获取系统内核版本
//跟 Ubuntu 情况类似，64 位操作系统，内核版本至少为 3.10。
//Docker 目前支持 CentOS 6.5 及以后的版本
```
    
    
- 安装命令
```
$ sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/$releasever/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF
//添加 docker 软件源。
    
$ sudo yum update
//更新 docker 软件源缓存。
    
$ sudo yum install -y docker-engine
//安装最新的 docker 版本。

```
    
