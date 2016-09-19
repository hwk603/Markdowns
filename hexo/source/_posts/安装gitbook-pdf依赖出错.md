title: 安装gitbook-pdf依赖出错
date: 2016-02-25 00:09:45
tags: gitbook
---

GitBook 是一个基于 Node.js 的命令行工具，可使用 Github/Git 和 Markdown 来制作精美的电子书。

之前已经通过`npm install -g gitbook-cli`命令安装了gitbook，但一直没安装gitbook-pdf依赖，所以一直在windows本地生成过pdf。

<!--more-->

命令行输入：
```
npm install gitbook-pdf -g
```
然而出现了error：

![此处输入图片的描述][1]

仔细看提示可以发现，错误原因是因为`phantomjs-1.9.7-windows.zip`这个文件下载问题，后来到网上查一下才发现原来这个源被墙了【万恶的GFW！！！

然后就简单了，随便找一个`phantomjs-1.9.7-windows.zip`下载到本地，放在`C:\Users\hwk603\AppData\Local\Temp\phantomjs`里面。

这里提供一个下载链接：

[phantomjs-1.9.7-windows.zip][2]

回到命令行，再次执行：
```
npm install gitbook-pdf -g
```

![此处输入图片的描述][3]

安装成功！！！

  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160224231625.png
  [2]: http://pan.baidu.com/s/1dE0t0ul
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160224231924.png