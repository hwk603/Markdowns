layout: hexo
title: hexo deploy时重复输入用户名密码的问题
date: 2015-10-18 01:08:12
tags: hexo
---

每次部署执行`hexo deploy`都需要输入用户名

![此处输入图片的描述][1]

问题原因及解决方案：

最主要的原因可能是你木有采用`git@github.com`

![此处输入图片的描述][2]

而是用`https//github.com`。

![此处输入图片的描述][3]

修改后重新提交部署：

![此处输入图片的描述][4]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/hexo-01.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/hexo-04.png
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/hexo-03.png
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/hexo-02.png