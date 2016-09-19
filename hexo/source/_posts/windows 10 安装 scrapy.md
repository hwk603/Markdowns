title: windows 10 安装 scrapy
date: 2016-03-08 16:29:17
tags: python
---


### 要求：

- python环境并且已经配置过环境变量
- 安装了python的软件包管理工具pip
- python访问windows系统API的库pywin32

<!--more-->

1. python的安装配置：
安装下载适合的python版本：https://www.python.org/downloads/；
之后修改 PATH 环境变量，将 Python 的可执行程序及额外的脚本添加到系统路径中。将以下路径添加到 PATH 中:
    ```
    D:\software\python27\;D:\software\python27\Scripts\;
    ```

2. [pip][2]的安装配置：
下载最新的pip版本：https://pypi.python.org/pypi/pip#downloads，最好选择tar.gz包；
解压安装包，在终端中进入解压目录，然后使用如下命令进行安装
    ```
    python setup.py install
    ```

3. [pywin32][3]的安装配置：
选择合适版本下载：https://sourceforge.net/projects/pywin32/files/pywin32/；

---

### 安装：
确定已经满足要要求，如下：

![此处输入图片的描述][4]

在终端执行：
```
pip install Scrapy
```
安装成功：

![此处输入图片的描述][5]

---

### 问题

- `ERROR: 'xslt-config' 不是内部或外部命令，也不是可运行的程序或批处理文件`


![此处输入图片的描述][6]

解决方法：

在https://pypi.python.org/simple/lxml/重新下载python的lmxl，适合自己的系统版本。


- `error: Microsoft Visual C++ 9.0 is required`

![此处输入图片的描述][7]

解决方法：

> For Windows installations:
> 
> While running setup.py for package installations, Python 2.7 searches
> for an installed Visual Studio 2008. You can trick Python to use a
> newer Visual Studio by setting the correct path in VS90COMNTOOLS
> environment variable before calling setup.py.
> 
> Execute the following command based on the version of Visual Studio
> installed:
> 
> - Visual Studio 2010 (VS10): `SET VS90COMNTOOLS=%VS100COMNTOOLS% `
> - Visual Studio 2012 (VS11): `SET VS90COMNTOOLS=%VS110COMNTOOLS% `
> - Visual Studio 2013 (VS12): `SET VS90COMNTOOLS=%VS120COMNTOOLS% `
> - Visual Studio 2015 (VS14): `SET VS90COMNTOOLS=%VS140COMNTOOLS%`

我pc上安装的是VS2015，所以终端执行:
```
SET VS90COMNTOOLS=%VS140COMNTOOLS%

```
然后继续执行scrapy安装。

  [1]: https://www.python.org/downloads/
  [2]: https://pip.pypa.io/en/latest/installing/
  [3]: https://sourceforge.net/projects/pywin32/files/pywin32/
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/Iscrapy-mage%205.png
  [5]: http://7i7k6x.com1.z0.glb.clouddn.com/scrapy-Image%207.png
  [6]: http://7i7k6x.com1.z0.glb.clouddn.com/scrapy-Image%202.png
  [7]: http://7i7k6x.com1.z0.glb.clouddn.com/scrapy-Image%203.png