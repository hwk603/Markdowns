title: 安装java之后,找不到tools.jar和dt.jar
date: 2015-10-17 01:26:59
tags: java
---
可能很多初学者和我一样，在初次接触java开发的过程中，急于看到最终的结果，匆匆在网上下载了jdk之后，点击安装，结果等安装完，开始配置classpath时，发现`jdk/lib`下面根本就没有` tools.jar `和`dt.jar` 这两个包。我在首次遇到这样的问题时，也以为是下载的包有问题，于是重新下载了之后再安装，结果还是老样子。

问题的根本原因，我们没有弄清两个概念：JDK和JRE。JDK是java开发核心组件，是用来编译解释java程序的核心组件，包含java `compile（javac） `面向的是java开发人员。JRE是java运行环境。Java一种是跨平台语言，一次编译，多次在多台电脑上运行，这种机制主要依靠JVM实现。java程序编译得到的是中间字节码，中间字节码是不能再机器上直接运行的，必须要经过JVM把中间字节码转换为机器语言，事实上，JRE中主要包含的就是JVM。JRE是面向的是java程序用户。

搞清楚了JDK和JRE之后，在安装java相关的程序要当心了。在安装java包时，会遇到两次路径选择，第一次时选择jdk的路径，第二次是选择JRE的路径，如果把所选择的jdk的路径和jre的路径相同，那么jre包中的内容会覆盖掉jdk中的内容，因此，在你安装完成之后，会发现找不到tools.jar和dt.jar包。所以，在安装的过程中，jdk和jre要安装在不同的文件下，比如我的jdk安装在`D:\java\jdk`下面，jre安装在`D:\java\jre`下面。安装好之后，path和classpath的配置时针对JDK的，可以配置为：

```
Path="D:\java\jdk\bin;"
classpath="D:\java\jdk\lib\dt.jar;D:\java\jdk\lib\tools.jar;"
```
然后在cmd中输入`javac`，看到java命令帮助，表明java相关软件已经安装成功。
![此处输入图片的描述][1]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/java-01.png