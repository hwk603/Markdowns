title: MongoDB在windows上的配置
date: 2015-11-01 21:55:00
tags: MongoDB
---

[MongoDB的官方下载][1]

![此处输入图片的描述][2]

- `MongoDB for Windows 64-bit ` 适合 64 位的 Windows Server 2008 R2, Windows 7 , 及最新版本的 Window 系统。
- `MongoDB for Windows 32-bit ` 适合 32 位的 Window 系统及最新的 Windows Vista。 32 位系统上 MongoDB 的数据库最大为 2GB。
- `MongoDB for Windows 64-bit Legacy` 适合 64 位的 Windows Vista, Windows Server 2003, 及 Windows Server 2008 。

---

<!--more-->

下载后，安装MongoDB。

安装过程中，你可以通过点击 "Custom(自定义)" 按钮来设置你的安装目录。

为了启动mongodb方便，可以将bin子目录中的mongod.exe路径加入环境变量，电脑->属性->高级系统设置->环境变量,在path里加入路径。

在安装目录mongodb下面建立data和log文件夹，data文件夹中建立db文件夹。

进入MongoDB安装目录下的bin子目录；在bin子目录中创建一个新的文本文件，取名为`mongodb.config`，写入以下：

```
## 数据库文件目录
dbpath=D:/mongodb/data
## 日志目录
logpath=D:/mongodb/log/mongo.log
diaglog=3

```

cmd中切换到`c:\mongodb\bin\`[你的安装目录],输入命令：

```
mongod --config c:\mongodb\bin\mongodb.config
```

此时就可以运行`mongo`了（没有d），它会启动一个shell并连接到运行中的服务器。输入`db.version()`以确认所有的东西都正常工作：可以看到所安装的软件版本。

### 将MongoDB服务器作为Windows服务运行

**一定要注意此时要在管理员权限下运行！！！**

```
mongod --config c:\mongodb\bin\mongodb.config --install
```

![此处输入图片的描述][3]


  [1]: https://www.mongodb.org/downloads#production
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/mongo-01.png
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/mongo-02.png