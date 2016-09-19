title: Windows 10 下 MarkdownPad2 预览无法显示
date: 2015-09-17 22:11:17
tags: windows
---

以前在win7下安装的MarkdownPad2，使用完全没有问题。升级win10后，打开MarkdownPad2，却发现右侧预览页面打不开。

<!--more-->

![此处输入图片的描述][1]

![此处输入图片的描述][2]

官方的说法是从 Win 8 开始就有这个问题了，解决办法就是安装 [Awesomium 1.6.6 SDK][3]，如果还是不行就再安装 [Microsoft's DirectX End-User Runtimes (June 2010)][4]，经我实际测试，只需要安装前者就可以了。下面是官方的原文：

> LivePreview is not working - it displays an error message stating This
> view has crashed! This issue has been specifically observed in Windows
> 8. You may see an error message as shown here, and no HTML will be rendered when you type in the Markdown Editor pane. To fix this issue,
> please try installing the [Awesomium 1.6.6 SDK][5]. If you continue to experience issues, please install [Microsoft's DirectX End-Useruntimes (June 2010)R][6].
> 
> 
> ===================================
> Referer:[MarkdownPad - Frequently Asked Questions][7]

根据提示，安装完Awesomium 1.6.6 SDK后，MarkdownPad2就可以正常显示了。


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/markdown-01.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/markdown-02.png
  [3]: http://pan.baidu.com/s/1jGxpWxg
  [4]: https://www.microsoft.com/en-us/download/details.aspx?id=8109
  [5]: http://pan.baidu.com/s/1jGxpWxg
  [6]: https://www.microsoft.com/en-us/download/details.aspx?id=8109
  [7]: http://markdownpad.com/faq.html#livepreview-directx