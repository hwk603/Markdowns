title: compile Lua 5.3.0 for Windows
date: 2016-01-18 01:40:38
tags: lua

---
最近想研究一下lua，平时常用的都是windows，所以原本打算使用[lua for windows][1] ，然而最新的版本却只有lua 5.1，再加上莫名其妙下载不了【墙的错】，所以决定在windows上自己编译一下lua源码。

ps.祝自己期末不挂科~

    系统：windows 10
    编译器：Visual Studio 2015
    源码：lua-5.3.0
	
<!--more-->


步骤如下：

1. 下载[Lua 5.3.0 source code][2]

2. 打开Visual Studio Command prompt

![此处输入图片的描述][3]

然后cd至lua-5.3.0/src，运行以下命令：

```
cl /MD /O2 /c /DLUA_BUILD_AS_DLL *.c
ren lua.obj lua.o
ren luac.obj luac.o
link /DLL /IMPLIB:lua5.3.0.lib /OUT:lua5.3.0.dll *.obj 
link /OUT:lua.exe lua.o lua5.3.0.lib 
lib /OUT:lua5.3.0-static.lib *.obj
link /OUT:luac.exe luac.o lua5.3.0-static.lib
```
![此处输入图片的描述][4]

![此处输入图片的描述][5]

![此处输入图片的描述][6]


之后可以看到src目录下有了 lua.exe和luac.exe的解释器，以及 lua5.3.0.dll。

![此处输入图片的描述][7]

在当前目录下运行一下lua命令，成功！【此后可以把D:/lua-5.3.0/src添加到环境变量，就可以在全局使用lua了】

![此处输入图片的描述][8]


  [1]: https://code.google.com/p/luaforwindows/
  [2]: http://www.lua.org/ftp/lua-5.3.0.tar.gz
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/lua-01-1.png
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/lua-01.png
  [5]: http://7i7k6x.com1.z0.glb.clouddn.com/lua-02.png
  [6]: http://7i7k6x.com1.z0.glb.clouddn.com/lua-03.png
  [7]: http://7i7k6x.com1.z0.glb.clouddn.com/lua-04.png
  [8]: http://7i7k6x.com1.z0.glb.clouddn.com/lua-05.png