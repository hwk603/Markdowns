title: php基础入门(三)
tags: php
date: 2015-04-15 10:30:00
---

## 流程控制结构 ##

### 循环 ###

+ 我们都很烦做同样的事情，比如小时候老师留作业“把某某段落抄五遍”，明明抄一遍就可以了，感觉做同样的事情好烦啊，做同样而无聊的事情就更是烦上加烦。
+ 没错，使用循环结构可以让你从烦闷中解脱出来，我们使用循环结构来做类似的事，在PHP中，循环分为while循环和for循环，那么它们通常怎么用呢？
+ 先来说while循环，它的核心思想就是：如果条件满足，则一直做某件事，它的语法结构和if很像，当然，内部的执行机制是两码事。它也是后面跟一个逻辑值，如果该值为真，则一直做某件事。
    `while (条件){要执行的代码;}`
+ while后面通常跟一个小括号，里面写各种逻辑运算，但是得到的结果是一个布尔类型的值或者是可以转型为布尔类型的值，然后跟一个大括号，这个大括号里面的内容通常被称为循环体。

<!--more-->

```





<?php
    $i=1;
    while($i<=5)
    {
        echo "The number is " . $i . "<br>";
        $i++;
    }
?>
```
    输出：
```
The number is 1
The number is 2
The number is 3
The number is 4
The number is 5
```

+ for循环则是一个更加强大的循环，PHP的for循环和C的for循环很像:

    `for (初始值; 条件; 增量){要执行的代码;}`

 - 初始值：主要是初始化一个变量值，用于设置一个计数器（但可以是任何在循环的开始被执行一次的代码）。
 - 条件：循环执行的限制条件。如果为TRUE，则循环继续。如果为FALSE，则循环结束。
 - 增量：主要用于递增计数器（但可以是任何在循环的结束被执行的代码）。
```
<?php
    for ($i=1; $i<=5; $i++)
    {
        echo "The number is " . $i . "<br>";
    }
?>
```
### break***conitue***return ###

在学习完毕上面讲解的几种结构之后，我们来看一下三大杀手，它们是break、continue 和 return。

 - break

break是被用在上面所提的各种循环和switch语句中的。他的作用是跳出当前的语法结构，执行下面的语句。break语句可以带一个参数n，表示跳出循环的层数，如果要跳出多重循环的话，可以用n来表示跳出的层数，如果不带参数默认是跳出本重循环。
```
<?php
    $arr = array('one', 'two', 'three', 'four', 'stop', 'five');
    while (list (, $val) = each($arr))
    {
        if ($val == 'stop') 
        {
            break;    /* You could also write 'break 1;' here. */
        }
        echo "$val<br />\n";
    }

/* 使用可选参数 */

    $i = 0;
    while (++$i) 
    {
        switch ($i) 
        {
            case 5:
                echo "At 5<br />\n";
                break 1;  /* 只退出 switch. */
            case 10:
                echo "At 10; quitting<br />\n";
                break 2;  /* 退出 switch 和 while 循环 */
            default:
                break;
        }
    }
?>
```
 - continue

continue是用来用在循环结构中，控制程序放弃本次循环continue语句之后的代码并转而进行下一次循环。ontinue本身并不跳出循环结构，只是放弃这一次循环。如果在非循环结构中(例如if语句中，switch语句中)使用continue，程序将会出错。
```
<?php
    for($i=1;$i<=100;$i++)
    {
	    if($i%3==0||$i%7==0)
	    {
		    continue;
	    }
	    else
	    {
		    echo $i,"<br/>";
	    }
    }
?>
```

 - return

return语句是用来结束一段代码，并返回一个参数的。可以从一个函数里调用，也可以从一个include()或者require()语句包含的文件里来调用，也可以是在主程序里调用，如果是在函数里调用程序将会马上结束运行并返回参数，如果是include()或者require()语句包含的文件中被调用，程序执行将会马上返回到调用该文件的程序，而返回值将作为include()或者require()的返回值。而如果是在主程序中调用，那么主程序将会马上停止执行。
```
<?php
    for($i=1000;$i>=1;$i–)
    {
	    if(sqrt($i)>=29)
	    {
		    echo $i,"<br/>";
	    }
	    else
	    {
		    return;
	    }
    }
    echo "本行将不会被输出";
?>
```

> 嗯，总而言之：  
> break结束循环，跳出循环体,进行后面的程序；  
> continue结束本次循环，进行下次循环； 
> return跳出循环体所在的方法，相当于结束该方法。

**未完待续**
