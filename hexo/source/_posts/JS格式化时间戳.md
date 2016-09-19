title: JS格式化时间戳
tags: js
date: 2015-06-21 16:30:00
---

PHP格式化时间戳倒是很方便，一个 time 函数就搞定了。而JS麻烦许多。

<!--more-->
```
    Date.prototype.format = function(format) 
    {
    var o = {
                "M+" :this.getMonth() + 1, // month
                "d+" :this.getDate(), // day
                "h+" :this.getHours(), // hour
                "m+" :this.getMinutes(), // minute
                "s+" :this.getSeconds(), // second
                "q+" :Math.floor((this.getMonth() + 3) / 3), // quarter
                "S" :this.getMilliseconds(),// millisecond
            }
    if (/(y+)/.test(format)) 
    {
        format = format.replace(RegExp.$1, (this.getFullYear() + "").substr(4 - RegExp.$1.length));
    }
    for ( var k in o) 
    {
        if (new RegExp("(" + k + ")").test(format))
        {
            format = format.replace(RegExp.$1, RegExp.$1.length == 1 ? o[k]: ("00" + o[k]).substr(("" + o[k]).length));
        }
    }
    return format;
    }
	
```

使用的话直接`Date.format('yyyy-MM-dd hh:mm:ss')`就可以了。

注意：JS时间戳是毫秒，所以PHP的时间戳转换的时候需要乘以1000




