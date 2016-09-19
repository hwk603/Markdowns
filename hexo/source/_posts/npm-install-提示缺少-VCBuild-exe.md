title: npm install 提示缺少 VCBuild.exe
date: 2016-03-30 20:44:29
tags: node
---


执行` node install `命令安装依赖的时候，发现出现error如下：

 >MSBUILD : error MSB3428: 未能加载 Visual C++ 组件“VCBuild.exe”。要解决此问题：
 
> 1) 安装 .NET Framework 2.0 SDK； 2) 安装 Microsoft Visual Studio 2005；或  3)
> 如果将该组件安装到了其他位置，请将其位置添加到系统路径中。 
> 
> [E:\code\javascript\strut2\node_modules\webpack-dev-server\node_modules\socket.io\node_modules\socket.io-client\node_modules\ws\build\binding.sln]

![][1]

然而，我的 pc 上该有的 Microsoft Visual Studio 依赖都是有的。

![][2]

后来发现，需要强制指定才行，例如：如果我的系统上安装了` Microsoft Visual Studio 2015 `,执行一下命令：

```
npm config set msvs_version 2012 --global

```

  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-03-30%201459340917.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-03-30%201459341535.png