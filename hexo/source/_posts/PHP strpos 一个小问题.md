title: PHPstrpos一个小问题
tag: php
date: 2015-05-01 20:00:00
---

strpos函数：在一个给定的字符串中查找指定子串，如果找到，返回该子串第一次在主串中出现的位置，如果未找到返回false。
依照这个解释，我写了段简单的代码
<!--more-->
```
    $subject = 'this is a hello world';
    if(strpos($subject, 'this')>0)
    {
      //找到了 
    }
    else
    { 
      //未找到 
    } 
```

这样会有一个问题，因为php中0与false是相等(==)的，所以，当子串在主串起始处出现会返回0，这里需要使用 === 来判断




