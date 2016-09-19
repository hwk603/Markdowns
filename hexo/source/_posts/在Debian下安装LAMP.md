title: 在Debian下安装LAMP
date: 2016-05-01 15:01:17
tags: linux
---

### Debian LAMP环境的搭建

![][1]

<!--more-->

#### 第一步：安装MySQL:

```
$sudo apt-get install mysql-server-5.0
```

这样安装的是 MySQL 的5.0版本，而且可以自动的解决各种依赖关系，从而会安装上服务器端与客户端以及各种相应的软件包。

#### 第二步：安装 Apache2:

```
$sudo apt-get install apache2
```

这样安装的是Apache的2.x版本，如果采用的是:

```
$sudo apt-get install apache
```

则安装的是 Apache 的1.x版本。

#### 第三步：安装 PHP5

```
$sudo apt-get install php5
$ apt-get intall php5-mysql
//这个不安装PHP代码无法连接到MYSQL上
```

这样就会安装PHP5版本，而且会自动的安装上各种所需要的模块。如 Apache2 与 MySQL 的相应 Module 等。

#### 第四步：安装 phpmyadmin

```
$sudo apt-get install phpmyadmin
```

这样我们就已经成功的搭建了我们的 LAMP 开发环境了。



### 测试

#### MySQL

apt 在成功的安装了MySQL后，默认启动了MySQL服务器，我们可以用下面的命令来与之建立连接：

```
$ mysql
```

如果显示了mysql提示符，则说我们的 mysql 安装是成功的。

由于安装过程可能配置 mysql 的 root 用户密码,如果配置了直接使用mysql会报错:

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using passwor
```

请使用` $ mysql -u root -p `输入密码进入控制台:

```
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using passwor
```

#### Apache2
apt在成功的安装了Apache2后，默认启动了Apache2守护进程，我们可以在我们的浏览器地址栏中输入 `http://localhost/`，如果可以看到默认的主页，则说我们的 Apache2 安装是成功的。

#### PHP

可以简单的写一个 PHP 的脚本如 index.php 放在 Apache2  目录下，默认为`/var/www/`目录。脚本内容如下：

```
<?php
phpinfo();
?>

```

这样以后在我们的浏览器地址栏中输入 `http://localhost/index.php`

如果可以正确的解析，则说明 PHP 的安装是成功的。

如果PHP脚本没有正确的进行解析，重启系统测试一下！


### 问题

#### 启停apache

```
$sudo /etc/init.d/apache2 start
$sudo /etc/init.d/apache2 stop
$sudo /etc/init.d/apache2 restart
```

#### 浏览器中文乱码

修改配置文件:

```
sudo gedit /etc/apache2/apache2.conf
```

添加: ` AddDefaultCharset  UTF-8 `.

 


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-05-19%201463641523.png