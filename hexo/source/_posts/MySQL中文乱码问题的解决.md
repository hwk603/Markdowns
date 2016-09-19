title: MySQL中文乱码问题的解决
date: 2015-09-26 13:26:15
tags: Mysql
---

当向 MySQL 数据库查看或者插入一条带有中文的数据出现乱码时，可以使用语句 `show variables like 'character%';` 来查看当前数据库的相关编码集。

<!--more-->

![此处输入图片的描述][1]



    client	    为客户端使用的字符集。
    connection	为连接数据库的字符集设置类型，如果程序没有指明连接数据库使用的字符集类型则按照服务器端默认的字符集设置。
    database	为数据库服务器中某个库使用的字符集设定，如果建库时没有指明，将使用服务器安装时指定的字符集设置。
    results	    为数据库给客户端返回时使用的字符集设定，如果没有指明，使用服务器默认的字符集。
    server	    为服务器安装时指定的默认字符集设定。
    system	    为数据库系统使用的字符集设定。


了解了上面的信息我们来分析下乱码的原因，问题出在了当前的CMD客户端窗口，因为当前的 CMD客户端输入采用GBK编码，而数据库的编码格式为UTF-8，编码不一致导致了乱码产生。

而当前 CMD 客户端的编码格式无法修改，所以只能修改` connection、 client、results `的编码集来告知服务器端当前插入的数据采用GBK编码，而服务器的数据库虽然是采用UTF-8编码，但却可以识别通知服务器端的GBK编码数据并将其自动转换为UTF-8进行存储。可以使用如下语句来快速设置与客户端相关的编码集：

```
set names gbk;
```

设置完成后即可解决客户端插入数据或显示数据的乱码问题了，但我们马上会发现这种形式的设置只会在当前窗口有效，当窗口关闭后重新打开CMD客户端的时候又会出现乱码问题；那么，如何进行一个一劳永逸的设置呢？在MySQL的安装目录下有一个`my.ini`配置文件，通过修改这个配置文件可以一劳永逸的解决乱码问题。

![此处输入图片的描述][2]

在这个配置文件中`[mysql]`与客户端配置相关，`[mysqld]`与服务器配置相关。默认配置如下：

```
[mysql]
default-character-set=utf8
[mysqld]
character-set-server=utf8
```

这时只需要将下的默认编码` default-character-set=utf8 `改为 `default-character-set=gbk` ，重新启动 MySQL 服务即可。


重新进行查询，显示成功：

![此处输入图片的描述][3]

此时的数据库的相关编码集：

![此处输入图片的描述][4]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/mysql.PNG
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/mysql-02.PNG
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/mysql-04.PNG
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/mysql-05.PNG