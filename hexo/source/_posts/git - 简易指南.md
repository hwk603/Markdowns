title: git - 简易指南
tags: git
date: 2015-07-10 16:30:00
---


助你开始使用 git 的简易指南，木有高深内容，;)。

<!--more-->

## 安装 ##
[git for windows][1]
[git for OSX][2]
[git for linux][3]

## 配置git ##
在使用git之前你需要配置一下git。git在你创建提交的时候会记录你的名字和email地址，所以你应该告诉git这些内容。可以使用'git config'命令来设置。

    $ git config --global user.name "你的用户名"
    $ git config --global user.email "你的邮箱"

## 常用命令 ##

 - 初始化一个Git仓库，使用`git init`命令。
 
 - 添加文件到Git仓库，分两步：

 第一步，使用命令`git add <file>`，注意，可反复多次使用，添加多个文件；
 第二步，使用命令`git commit`，完成。

 - 远程库
第1步：创建SSH Key。在C盘user目录下，看看有没有.ssh目录，如果有，再看看这个目录下有没有id_rsa和id_rsa.pub这两个文件，如果已经有了，可直接跳到下一步。如果没有，打开Shell（Windows下打开Git Bash），创建SSH Key：
  `$ ssh-keygen -t rsa -C "你的邮箱"`
  
 ![](http://7i7k6x.com1.z0.glb.clouddn.com/github-01.png)
第2步：登陆GitHub，打开“Account settings”，“SSH Keys”页面：

 ![图片1][4]
然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容：
 ![图片2][5]
第3步：关联远程仓库
在本地的仓库下运行命令：
`$ git remote add origin git@github.com:你自己的GitHub账户名/仓库名.git`
下一步，就可以把本地库的所有内容推送到远程库上：

```   
$ git push -u origin master
Counting objects: 19, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (19/19), done.
Writing objects: 100% (19/19), 13.73 KiB, done.
Total 23 (delta 6), reused 0 (delta 0)
To git@github.com:michaelliao/learngit.git
* [new branch]      master -> master
Branch master set up to track remote branch master from origin.

```	

     

  [1]: http://msysgit.github.io/
  [2]: https://code.google.com/p/git-osx-installer/downloads/list?can=3
  [3]: http://git-scm.com/downloads
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/github-02.png
  [5]: http://7i7k6x.com1.z0.glb.clouddn.com/github-03.png
