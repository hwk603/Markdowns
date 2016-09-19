title: 翻墙篇之修改hosts
tags: hosts
date: 2015-3-1  19:50:26  
---

不论是第一次接触翻墙的人，还是精通了无数翻墙技巧的人，都不可避免地了解到 hosts。修改hosts是最成功、最有效，也是最为跨平台的方法。它简单高效，并且随时可修改，通过绕过 DNS 直接访问 IP 的方式，可以让翻墙变得十分容易，不会像客户端软件那样需要不停地切换国内国外网络，大大简化了操作步骤。

<!--more-->

### 如何修改 HOSTS

Hosts 文件一般在 Windows 系统的` windows\system32\drivers\etc\` 下，或 Mac、Linux类系统的`/etc/`下。找到这个本地文件后，直接用你在网上获取到的hosts文件的内容复制粘贴，覆盖掉你本地hosts里的内容。修改时应当注意权限问题。

> 注意：如果遇到无法保存，请右键文件hosts并找到“属性” -> “安全”，然后选择你登陆的用户名，最后点击编辑，勾选“写入”即可。

 
### HOSTS支持的网站
 - Google 服务（包括 YouTube，Gmail，Google+，Google Drive 等） 
 - Wikipedia 维基百科
 - Facebook 脸谱
 - Twitter 推特
 - Flickr 雅虎图片
 - 等等···
 
**重要提醒**：修改hosts之后，请使用https进行访问，例如：

https://www.google.com
https://www.facebook.com

附上一些稳定的hosts来源：

[github上的一些host项目（亲测可用，推荐）][1]
[老D博客上更新的hosts][2]

### 图示：

![此处输入图片的描述][3]

![此处输入图片的描述][4]

![此处输入图片的描述][5]

之后复制到本地hosts文件，替换掉原有的内容就可以了。


  [1]: https://github.com/search?utf8=%E2%9C%93&q=hosts
  [2]: http://laod.cn/hosts
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%208.png
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%209.png
  [5]: http://7i7k6x.com1.z0.glb.clouddn.com/Image%2012.png