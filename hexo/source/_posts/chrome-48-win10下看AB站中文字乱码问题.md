title: chrome 48+win10下看AB站中文字乱码问题
date: 2016-02-05 21:28:12
tags: chrome
---

chrome新版本A站和B站的播放器内文字会显示为乱码。

仅仅只是和flash相关的就弹幕出现中文乱码，b站只有右边的弹幕栏框里是乱码，飘的弹幕是正常的，a站飘的弹幕都是乱码。

![此处输入图片的描述][1]

![此处输入图片的描述][2]

我昨天遇到这个问题，现在说下总结：
这个问题跟flash有关，是在flash中出现的，普通网页没有。非windows 10的相同版本chrome，没有问题；而windows10的chrome47或者开发版49都有问题，想来可能是 chrome中的` ppapi flash `对于 windows 10的一些东西不太兼容，有问题，才导致显示异常，等待解决。

目前已有的解决的方法：

地址栏输入`chrome://flags/`,更改direct-write设置，点启用：

![此处输入图片的描述][3]

重启后，已无乱码：

![此处输入图片的描述][4]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%202.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%201.png
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%203.png
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%204.png