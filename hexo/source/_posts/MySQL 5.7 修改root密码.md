title: mysql 5.7 修改root密码
date: 2016-02-23 13:07:16
tags: mysql
---

版本更新，原来`user`数据库里的`password`字段已经变更为`authentication_string`。

同样因为版本更新缘故，之前网上的很多教程都不适用了，甚至连官网的文档也不是能够顺利操作的。

<!--more-->

首先如果 `MySQL`正在运行，首先要将这个进程关掉。

![此处输入图片的描述][1]

之后在命令行中进行如下操作：

```
mysqld_safe --skip-grant-tables &；
//启动mysql时不启动grant-tables授权表，也就是说可以无须密码登录。
mysql -u root
//登录mysql。
use mysql;
//进入mysql数据库。
UPDATE user SET authentication_string=PASSWORD("新密码") WHERE User='root';
//修改root账户密码。
FLUSH PRIVILEGES;
//刷新MySQL的系统权限相关表，否则会出现拒绝访问。
quit;
//退出mysql。

```

之后，就可以用修改后的新密码登录mysql了。


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/QQ%E6%88%AA%E5%9B%BE20160223130414.png