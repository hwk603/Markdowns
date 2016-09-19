title: "git push 失败 failed to push some refs to git"
date: 2015-09-12 20:25:25
tags: git
---

在使用git 对源代码进行push到gitHub时可能会出错，error: failed to push some refs to git。

<!--more-->

![][1]

出现如上图中错误的主要原因是github中的README.md文件不在本地代码目录中。

![][2]

![][3]

可以通过如下命令进行github与本地代码合并:

```
git pull --rebase origin master
```

![][4]

执行上面代码后可以看到本地代码库中多了README.md文件。

![][5]

重新执行之前的git push 命令，成功！

![][6]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/giterror-01.JPG
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/giterror-02.JPG
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/giterror-04.JPG
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/giterror-05.JPG
  [5]: http://7i7k6x.com1.z0.glb.clouddn.com/giterror-03.JPG
  [6]: http://7i7k6x.com1.z0.glb.clouddn.com/giterror-06.JPG