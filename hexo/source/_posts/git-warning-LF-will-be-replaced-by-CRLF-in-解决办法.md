title: 'git warning: LF will be replaced by CRLF in 解决办法'
date: 2015-09-26 14:51:46
tags: git
---
之前重装了git和hexo，然后在使用提交命令的时候就出现了**`warning: LF will be replaced by CRLF in XXXXXXXXXXXXXX.`**的警告。

![此处输入图片的描述][1]

虽然说没有什么影响吧。

不过就是觉得太碍眼了，

输入命令：`git config --global core.autocrlf false`

然后就没有问题了。

![此处输入图片的描述][2]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/git-01.PNG
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/git-02.PNG