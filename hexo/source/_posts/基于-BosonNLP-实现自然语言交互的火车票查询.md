---
title: 基于 BosonNLP 实现自然语言交互的火车票查询
date: 2016-09-03 23:57:48
tags: python

---

## 一、实验说明


### 1.1 简述

在已有的火车票查询工具 `iquery` 的基础上，利用 `BosonNLP` 提供的中文语义分析接口，添加自然语言交互功能。

`iquery` 使用 `Python3` 编写，提供基于命令行各种信息查询。

`BosonNLP` 即玻森中文语义开放平台，提供中文自然语言分析云服务。

<!--more-->

### 1.2 知识点

- `Python3`
- `iquery` 的调用
- `BosonNLP` 库

## 二、实验步骤

----

### 2.1 安装 `iquery`

打开终端 `Xfce`，执行命令：

```
$ sudo pip3 install iquery
```

`iquery` 是一个集成了很多查询功能的工具，火车票查询只是其中之一。

![](http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-09-02%201472805831.png)

使用 `iquery` 进行查询，必须严格遵守其输入格式：

![](http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-09-02%201472783889.png)



### 2.2 注册 `BosonNLP`

访问 `BosonNLP` 官网 `http://bosonnlp.com/`，注册账号，获取 API 密钥：

![](http://7i7k6x.com1.z0.glb.clouddn.com/image%2020160902.png)



### 2.3 编码

#### 2.3.1 安装依赖

```
$ sudo pip3 install bosonnlp
```

`bosonnlp` 是 `BosonNLP HTTP API` 封装库。



#### 2.3.2 主程序

##### a. 导入模块：

```
# -*- coding: utf-8 -*-
# six
from distutils.log import warn as printf
import sys
from bosonnlp import BosonNLP
from os.path import expanduser
import os
import collections
import subprocess
import datetime
```

##### b. 配置 API 密钥：

```
bosonnlp_token = 'BosonNLP 的 API 密钥'
```

##### c. 通过调用 `bosonnlp` 对自然语言的查询语句实体进行识别：

```
class QueryParser(object):
    def __init__(self):
        self.nlp = BosonNLP(bosonnlp_token)
    def parse(self, query_string):
        """
        input:
        9月12号 成都到北京的高铁票
        # 调用 BosonNLP 命名实体识别接口
        # 参考：https://bosonnlp-py.readthedocs.io/#id2
        output:
        [{'entity': [[0, 3, 'time'], [3, 4, 'location'], [5, 6, 'location']], 
        'tag': ['t', 'm', 'q', 'ns', 'p', 'ns', 'ude', 'n', 'n'],
        'word': ['9月', '12', '号', '成都', '到', '北京', '的', '高铁', '票']}]
        """
        result = self.nlp.ner(query_string)[0]
        words = result['word']
        tags = result['tag']
        entities = result['entity']
        return (words,entities,tags)
    def get_entity(self,parsed_words,index_tuple):
        """
        获取已识别的实体
        采用 filter
        参考 python cookbook 部分
        input:
            entities : 二元组
            parsed_words : 解析好的词组
        """
        return parsed_words[index_tuple[0]:index_tuple[1]]

    def format_entities(self,entities):
        """
        给元组命名
        """
        namedentity = collections.namedtuple('namedentity','index_begin index_end entity_name')
        return [namedentity(entity[0],entity[1],entity[2]) for entity in entities]

    def get_format_time(self,time_entity):
        """
        # BosonNLP 时间描述转换接口 
        output
        {'timestamp': '2013-02-28 16:30:29', 'type': 'timestamp'}
        """
        basetime = datetime.datetime.today()
        result = self.nlp.convert_time(
            time_entity,
            basetime)
        #print(result)
        timestamp = result["timestamp"]
        return timestamp.split(" ")[0]
```

##### d. 火车票查询函数 `pattern_train_ticket`：

```
def pattern_train_ticket(query):
    query_parse = QueryParser()
    (words,entities,tags) = query_parse.parse(query)
    #给元组命名，整体 filter
    namedentities = query_parse.format_entities(entities) 
    # 检查实体的数量，count，元组，token
    time_nameentity = [nameentity for nameentity in namedentities if nameentity.entity_name=="time"][0] 
    location_nameentities = [nameentity for nameentity in namedentities if nameentity.entity_name=="location"] 
    sorted_location_nameentities = sorted(location_nameentities,key=lambda a:a[1])
    # 排序为有序列表 list.sort() 按照第一个元素排序 sorted(a),按顺序,sorted(a,key=lambda a:a[1]) 按第二个元素排序
    time_entity =  query_parse.get_entity(words,(time_nameentity.index_begin,time_nameentity.index_end))
    time_string = "".join(time_entity)
    format_time = query_parse.get_format_time(time_string)

    location_from_nameentity = sorted_location_nameentities[0] 
    #较前边的,出发地
    location_from_entity =  query_parse.get_entity(words,(location_from_nameentity.index_begin,location_from_nameentity.index_end))
    location_from_string = "".join(location_from_entity)

    location_to_nameentity = sorted_location_nameentities[1] 
    #较后边的，目的地:w
    location_to_entity =  query_parse.get_entity(words,(location_to_nameentity.index_begin,location_to_nameentity.index_end))
    location_to_string = "".join(location_to_entity)

    #printf(u"捕获时间:{}".format(time_string))
    #printf(u"出发地:{}".format(location_from_string))
    #printf(u"目的地:{}".format(location_to_string))

    # 正式查询
    call_iquery_train_ticket(location_from_string,location_to_string,format_time)
    return

```

##### e. 调用 `iquery`:

```
def call_iquery_train_ticket(location_from_entity,location_to_entity,time_entity):
    printf(subprocess.call(["iquery",location_from_entity,location_to_entity,time_entity]))

```

##### f. `main`:

```
def main():
    query = " ".join(sys.argv[1:])
    printf(query)
    printf("*"*8)
    pattern_train_ticket(query)

if __name__ == '__main__':
    main()
```

将以上代码保存为 `.py` 文件，然后在当前目录下执行:

```
python3 *.py 火车票查询语句

```
例如：

```
python3 ibot.py 2016年9月十二号 成都到北京的车票
python3 ibot.py 明天从成都到北京的车票
python3 ibot.py 这周六从成都去北京出差，帮我看下车票
python3 ibot.py 下周五离开成都去北京 查下车票
python3 ibot.py 查一下成都去北京的车票，下周六
```

![](http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-09-02%201472783939.png)


## 参考

---

`https://github.com/protream/iquery`

`https://github.com/wwj718/ibot`

`https://python3-cookbook.readthedocs.io/zh_CN/latest/`

