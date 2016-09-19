title: Mbps、Kbps、bps、kb、mb及其换算和区别
date: 2015-09-17 22:39:17
tags: 计算机网络
---

```
Data rates are generally measured in kilobits per second (Kbps) or megabits per second (Mbps); 
In the context of data rates, a kilobit is10^3 bits (not 2^10 ) and a megabit is 10^6 bits. 
The use of the lower-case “b” means bits; 
Data rates expressed in terms of bytes often use an upper-case “B”.
```

<!--more-->
Mbps 即 Milionbit pro second(百万位每秒)； 

Kbps 即 Kilobit pro second（千位每秒）； 

bps 即 bit pro second（位每秒）；  

bit即比特，通常用b（小写）表示，指一位二进制位，Milionbit=1000Kilobit=1000000bit； 

所以1Mbps=1000000bps； 

这是通常用来衡量带宽的单位，指每秒钟传输的二进制位数；

而通常软件上显示的速度则是指每秒种传输的字节数（Byte）通常用B（大写）表示；  

MB即百万字节也称兆字节； 

KB即千字节； 

B即字节；  

转换关系为1MB=1024KB=1024*1024B； 

1B=8b；  

所以1M带宽即指1Mbps=1000Kbps=1000/8KBps=125KBps；

因此1M的带宽下载的速度一般不会超过125KB每秒。

2M、3M带宽分别是250KBps、375KBps； 

2M、3M带宽的下载速度分别不会超过250KB、375KB每秒。

假设要对10kbps进行换算，则有 10kbps=10000bps=0.01Mpbs。

数据传输速率的衡量单位K是十进制含义,但数据存储的K是2进制含义。 

1kbit/s就是1000bit/s,而KB是1024个字节,注意KB和kbit的区别，另外，数据传输速率的单位是bit/s 记作：bps 。

在实际应用中,1kbps=1000bps，1Mbps=1000,000bps。                   

1bps=0.000001bps，1Mbps与1m/s是有区别的，1m/s指的是是1024KB/S，而1Mbps指的是1000/8KB/S也就是125KB/S，记住K和k是没区别的，区别在于bps属于位每秒的单位，而m/s ,KB/S这两个属于字节每秒的单位，一字节等于8位，即1B=8b。