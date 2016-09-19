title: windows 10 的升级
date: 2015-08-29 14:40:27
tags: windows
---

![此处输入图片的描述][1]

话说自从今年7月29号windows 10正式版发布至今，刚好一个月。用了这么久的win 10，感觉各方面都较之前的版本有所超越。下面提供一个最简单的升级到win 10的方法。


<!--more-->

- **准备工作：**
  - 准备好已经激活好的win7/8/8.1（只要是激活的就行，不管是KMS工具还是联网永久激活都可以）强烈不建议GHOTS系统升级，最好使用原版系统或者预装正版系统升级。

  - 升级之前检查好电脑硬件是否支持windows10系统，以免造成麻烦。（可以用腾讯或360的win10升级助手检测一下。PS：只用于检测，不要用于升级系统，检测完删除即可）

  - 注册微软账户并登陆当前系统，以体验升级win10后的全部功能。

- **升级：**
  下载好windows10的iso文件，原版系统下载地址：http://msdn.itellyou.cn/。下载的系统版本请对应当前的系统版本。

  比如：win7旗舰版对应下载win10专业版，win7家庭版对应下载win10家庭版；x86即32位系统 ，x64即64位系统。（windows_10_multiple_editions包含专业版和家庭版）然后解压到除C盘（系统盘）以外的盘，比如解压到E盘。
  
  ![此处输入图片的描述][2]
  
  点击setup.exe开始升级安装，暂时不获取更新以节约时间，点击下一步。
  
  ![此处输入图片的描述][3]
  
  选择需要保留的内容，看个人需要。最好还是先保留了，点击安装。
  
  ![此处输入图片的描述][4]
  
  自动进···入预安装界面。稍后会自动重启。耐心等待ing
  
  ![此处输入图片的描述][5]
  
  重启之后进入正式升级界面。还是要耐心等待ing 坐和放宽！
    
  ![此处输入图片的描述][6]
  
  安装完毕后 进入系统的相关设置。
  
  ![此处输入图片的描述][7]

  顺利进入桌面，运行`slmgr.vbs /xpr`显示系统永久激活。大功告成。登陆微软账户就可以开始调戏小娜和小冰了！！
  
  ![此处输入图片的描述][8]
  
  ![此处输入图片的描述][9]
 
---

安装其实已经到此为止了，但是本着no zuo no die 我就是要 try 的精神，本人尝试了一下将已升级成功的正版windows 10系统格式化重装一遍，测试能否保持激活状态。【结果当然是成功的，不然我还会在这愉快的写博客吗（笑）】

下面是我格盘重装的过程，不需要任何工具（前提是系统正常使用或者可以进入高级恢复模式）假设把系统镜像解压到E盘根目录。

- **格盘重装**

  按住shift点击重启，出现此界面，点击疑难解答→高级选项
  
  ![此处输入图片的描述][10]
  
  ![此处输入图片的描述][11]
  
  重启自动进入命令提示符，期间要求验证账户，输入密码即可
  
  ![此处输入图片的描述][12]
  
  命令符界面输入pushd E： （注意空格，iso文件如果解压在D盘就是pushd D：）。
  
  ![此处输入图片的描述][13]
  
  输入 setup.exe 就开始运行系统的安装程序，然后就可以重装系统了。（win10为例）。
  
  ![此处输入图片的描述][14]
  
  这里也需要密钥，直接跳过。
  
  ![此处输入图片的描述][15]
  
  注意：此处选择必须对应之前的版本，否则永久激活失效。
  
  ![此处输入图片的描述][16]
  
  试验一下格盘重装（全新安装）。
  
  ![此处输入图片的描述][17]
  
  选择系统盘分区，点击格式化，接着下一步。
  
  ![此处输入图片的描述][18]
  
  全新安装的界面和升级安装的界面不一样，还是传统风格。耐心等待安装完成。
  
  ![此处输入图片的描述][19]
  
  重启进入系统相关设置，密钥跳过以后再说！
  
  ![此处输入图片的描述][20]
  
  等待界面时间略长，还是要耐心等待。
  
  ![此处输入图片的描述][21]
  
  然后就是创建账户，完成最后的应用配置。
  
  ![此处输入图片的描述][22]
  
  ![此处输入图片的描述][23]
  
  全新安装完成，依旧永久激活。
  
  ![此处输入图片的描述][24]
  
---

关于windows 10 的升级就到这里了，安装过程中有其他问题，请留言。


  
  


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-1.jpg
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-3.jpg
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-4.jpg
  [4]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-5.jpg
  [5]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-6.jpg
  [6]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-7.jpg
  [7]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-8.jpg
  [8]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-9.jpg
  [9]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-10.jpg
  [10]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-11.jpg
  [11]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-12.jpg
  [12]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-13.jpg
  [13]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-14.jpg
  [14]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-15.jpg
  [15]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-16.jpg
  [16]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-17.jpg
  [17]: http://7i7k6x.com1.z0.glb.clouddn.com/win0-18.jpg
  [18]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-19.jpg
  [19]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-20.jpg
  [20]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-21.jpg
  [21]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-22.jpg
  [22]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-23.jpg
  [23]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-24.jpg
  [24]: http://7i7k6x.com1.z0.glb.clouddn.com/win10-25.jpg