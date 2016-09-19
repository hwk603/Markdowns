title: '解决git push:connection reset by peer'
date: 2015-12-03 22:05:36
tags: git
---


今天push项目的时候遇到这样一个错误：

![此处输入图片的描述][1]

然而此时github网站是可访问的。

最后，google后发现输入如下命令后就能push成功：

```
git config remote.origin.url git@github.com:your_username/your_project.git

```
![此处输入图片的描述][2]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/github-08.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/github-09.png