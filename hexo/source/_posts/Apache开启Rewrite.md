title: Apache开启Rewrite
date: 2016-01-03 22:34:25
tags:  apache
---


ubuntu如何开启Rewrite模块
在终端输入：
```
sudo a2enmod rewrite  开启Rewrite模块（停用模块，使用 a2dismod）
sudo gedit /etc/apache2/sites-available/default 修改下面的地方
<Directory />
Options FollowSymLinks
AllowOverride None（修改为AllowOverride All）
</Directory>
<Directory "/var/orioner">
Options Indexes FollowSymLinks MultiViews
AllowOverride None（修改为AllowOverride All）
Order allow,deny
allow from all
</Directory>
```
最后`sudo /etc/init.d/apache2 restart`。
----------------------------------------------------
在网站下面建立.htaccess文件
修改.htaccess文件属性 ` chmod -R 777 .htaccess`



