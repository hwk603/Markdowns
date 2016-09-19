title: windows64位下配置GO语言环境
date: 2015-07-14 23:05:43
tags: go

---

## 简要介绍一下Go语言

Go语言是谷歌推出的一种全新的编程语言，可以在不损失应用程序性能的情况下降低代码的复杂性。谷歌首席软件工程师罗布派克(RobPike)说：我们之所以开发Go，是因为过去10多年间软件开发的难度令人沮丧。

<!--more-->

## Go语言开发环境搭建

 1. 下载Go语言安装程序
 下载地址：
[官方下载](https://golang.org/dl/) 
[墙内下载地址](http://www.golangtc.com/download)
这里提供我个人安装的64位Go语言安装包（http://pan.baidu.com/s/1pJonQiB）


 2. 安装
如果你下载的是msi文件，那么直接双击就可以了，默认安装在`C:\go`。
如果你下载的是程序压缩包，那么解压在任意你喜欢的路径下（例如：`D:\go`），进入下一步配置环境变量。

 3. 配置环境变量
* 添加**Path**环境变量：如果你的go语言程序解压在D盘根目录下，那么在环境变量**Path**后添加go安装目录下的bin目录`D:\go\bin`。
![path添加](http://7i7k6x.com1.z0.glb.clouddn.com/go01.PNG)
* 新建**GOROOT**环境变量：如上，添加go安装目录的根目录`D:\go`。
![GOROOT添加](http://7i7k6x.com1.z0.glb.clouddn.com/go02.PNG)
 4. 验证是否安装成功
在运行中输入cmd打开命令行工具，在提示符下输入`go version`。
如果成功显示go语言版本号，则安装成功。
![go语言安装验证](http://7i7k6x.com1.z0.glb.clouddn.com/go03.PNG)


