title: 解决Windows Git Bash中文乱码问题
date: 2015-09-25 13:48:08
tags: git
---
在git的安装目录下，有个etc文件夹。

只需修改这个文件夹里的几个文件即可正常显示中文。

-  `/etc/gitconfig：`

在最下面添加一下代码:

```

[gui]
encoding = utf-8 
[i18n]
commitencoding = GB2312 #log编码，window下默认gb2312,声明后发到服务器才不会乱码
[svn]
pathnameencoding = GB2312 #支持中文路径

```

- `/etc/git-completion.bash:`

在最下面添加一下代码:

```

alias ls='ls --show-control-chars --color=auto' #ls能够正常显示中文

```

-  `/etc/inputrc:`

修改一下代码:

```
set output-meta on #bash中可以正常输入中文
set convert-meta off

```