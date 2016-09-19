title: 网络数据挖掘之 Mini Search
date: 2016-04-03 22:36:38
tags: homework
---


**课程名称**：网络数据挖掘

**实验课时**：3

**试验项目**：Boolean Search

**试验时间**: 2016/3/28

**实验目的**：在上周实现对文件建立的倒排索引的基础上，实现简单的布尔逻辑检索。

**试验环境**： ` windows 10 ` + ` mongoDB `+ ` meteor `

<!--more-->

**实验内容**：

- 实验步骤：

1. 将之前已经建立好的索引文件` word_index.txt `和` file_index.txt `导入 mongoDB 数据库。
2. 利用` node.js `框架` meteor `实现搜索功能。


- 实验程序：


```
//前端
<body>
  <div class="container">
    <h1>Mini Search @ SCU</h1>
      <form class="form-horizontal" onsubmit="return false;">
      <div class="form-group">
        <input type="text" class="form-control" id="search-box" 
        placeholder="Type keyword to search">
      </div>
      </form>
      {{#each items}}
        {{> item}}
      {{/each}}

    </div> 
</body>

<template name="item">
    <dl class="dl-horizontal">
    <dt>file id</dt>            <dd>{{file_id}}</dd>
    <dt>file name</dt>          <dd>{{file_name}}</dd>
    <dt>file content</dt>       <dd>{{file_content}}</dd>
    <hr>
    </dl>
</template>

```

```
//后端
//获取 Mongodb 中存储元数据的 collection
Items  = new Mongo.Collection('word');
//据用户提交的关键字对数据库进行查询，并发布 (publish) 与之相关的数据
if (Meteor.isServer) {
  Meteor.publish('items', function (queryString) {
      return query(Items, queryString) // To implement later
  })
}
//捕捉键盘输入事件，并将查询字符串存储于 Session 中，并根据查询字符串向服务器端订阅 (subscribe) 新数据
if (Meteor.isClient) {
  Session.set('queryString', '')
  Meteor.subscribe('items', '')
  //对所得数据进行展示的帮助函数
  Template.body.helpers({
    items: function () {
      return query(Items, Session.get('queryString'))
    }
  });  
  Template.body.events({
    "keyup #search-box":_.throttle(function(event){
      Session.set('queryString', event.target.value)
      Meteor.subscribe('items', event.target.value)
    }, 50)
  })
}
//据用户的输入构造查询数据库的条件,对数据库进行查询,返回查询结果，
function query(collections, queryString){
    var query = queryString.split(' ')
    var json = collections.find({"word":query},{"wordid":1,"_id":0})
    var contact = JSON.parse(json);
    for (var i = query.length - 1; i >= 0; i--){
        if (query[i] == ''){
        continue
    }
    var testSpecial  = booleanSearch(query[i])
    if (testSpecial != null){
      andArray.push(testSpecial)
    } else {
      var regEx = new RegExp(query[i], 'ig')
      andArray.push({file_name: regEx})
    }
  }
    for(int i = contact.word.length;i >= 0;i--)
        file_id = contact.word(i);
        return collections.find({"file_id":i},{"file_id":1,"file_name":1,"file_content":1})
}
function booleanSearch(str){
    var relation
    var result = {}
    if (str.indexOf('or') != -1){
        relation = str.split('or')
        result[relation[0]] = { $lt: Number(relation[1])}
        return result
    } 
    else if (str.indexOf('and') != -1){
        relation = str.split('and')
        result[relation[0]] = { $gt: Number(relation[1])}
        return result
    }
    return null;
}
```

- 实现：

![][1]

![][2]

![][3]


  [1]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-04-03%201459694016.png
  [2]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-04-10%201460301690.png
  [3]: http://7i7k6x.com1.z0.glb.clouddn.com/images%202016-04-10%201460301744.png