title: debian8无法挂载u盘解决方法
date: 2015-10-17 01:48:01
tags: linux
---
在文件管理器里点击 U 盘图标，提示 vfat 无法识别；在终端里使用 mount 命令挂载，也会出现错误提示：
` "mount: unknown filesystem type 'vfat'" `

解决方法：
重新安装内核：
`# apt-get install --reinstall <linux-image-内核版本号-系统架构>`
例如：
`$ sudo apt-get install --reinstall linux-image-3.16.0-4-amd64`

ps.以上来自我的舍友lxhillwind