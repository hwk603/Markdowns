title: linux 上 chrome 更新失败解决办法
date: 2016-05-10 10:18:49
tags:
---
![][1]

<!--more-->

好久没更新linux系统了，今天执行了一下:
```
$ sudo apt-get update
$ sudo apt-get upgrade

```
然后发现其他更新都成功了，只有chrome链接失败：
```
E: Failed to fetch http://dl.google.com/linux/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_49.0.2623.75-1_amd64.deb  Connection failed
```
解决办法：
1. 如果你的系统是32位的话，chrome 已经不再提供之后的安全更新;你只能选择继续使用该版本，或者选择卸载 chrome，安装 chromium 。
2. 如果你的系统是64位的话，需要修改你的`/etc/apt/sources.list.d/google-chrome.list`文件，可以在终端输入：
```
vim /etc/apt/sources.list.d/google-chrome.list
```
添加如下一行：
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
之后，保存退出，再执行`sudo apt-get upgrade`就可以正常更新chrome了。

[参考][2]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-05-19%201463642217.png
  [2]: https://www.reddit.com/r/chrome/comments/48oje6/linux_how_to_fix_failed_to_fetch/