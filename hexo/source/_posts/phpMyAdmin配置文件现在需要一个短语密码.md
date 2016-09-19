title: phpMyAdmin配置文件现在需要一个短语密码
date: 2016-02-23 13:28:53
tags: php
---
更新phpMyAdmin后，每次登录，在其下方都会出现“配置文件现在需要一个短语密码。”的提示：

![此处输入图片的描述][1]

<!--more-->

会出现这个问题，是在配置phpmyadmin填写认证方法时，即下面这行：

`$cfg[‘Servers’][$i][‘auth_type’] = ‘cookie';`

在此有四种模式可供选择,`cookie`，`http`，`HTTP`，`config`；

`config`方式即输入phpmyadmin的访问网址即可直接进入，无需输入用户名和密码，是不安全的，不推荐使用。

当该项设置为`cookie`，`http`或`HTTP`时，登录phpmyadmin需要数据用户名和密码进行验证，,具体如下：

- PHP安装模式为`Apache`，可以使用`http`和`cookie`；

- PHP安装模式为`CGI`，可以使用`cookie`。

**解决方法：**
```
 1、在phpMyAdmin/libraries/config.default.php,102行
    找到$cfg['blowfish_secret'] = ''; 
    改成 $cfg['blowfish_secret'] = '任意字符'; 

2、在phpMyAdmin目录中，打开config.sample.inc.php，17行
   找到$cfg['blowfish_secret'] = ''; 
   改成 $cfg['blowfish_secret'] = '任意字符'; 

```

这个密码用于Cookies的加密，以免多个PhpMyAdmin或者和其他程序共用Cookies时搞混。

之后，刷新，“配置文件现在需要一个短语密码。”的提示就不遇见了。

![此处输入图片的描述][2]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/phpmyadmin_Image%202.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/phpmyadminImage%204.png