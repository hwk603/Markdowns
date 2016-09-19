title: linux中打开window下txt文件乱码
date: 2015-10-29 00:10:17
tags: linux
---

有些在Windows下能够打开的txt文件在linux下用gedit打开时，中文显示是乱码，这是因为编码方式不同造成的。Windows下默认txt文件的编码方式是GBk，而linux下的gedit默认没有对GBK的支持。解决方法如下：
  
  在终端运行`gconf-editor`，在`apps -> gedit-2 -> preference -> encodings`里面有个`auto-detect`，在它的前面加上GBK或GB18030就OK了。
  
  
vim打开文件乱码

解决方法：
在`~/.vimrc`中输入：
```
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
```
在我的机器上没有`.vimrc`这个文件，我找到了`/etc/vim/vimrc`这个文件，于是加入了上面的行，测试好使了，我想是不是直接编辑`.vimrc`放到`~`下面也可以呢，于是删除了`/etc/vim/vimrc`里的那行，之后创建`.vimrc`文件，并写入`set file.....`这句，并复制到`~`目录下，测试也成功了。





