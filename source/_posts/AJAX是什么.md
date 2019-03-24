---
title: AJAX是什么
date: 2019-03-21
tags:
categories: js
---
AJAX 即 “Asynchronous JavaScript and XML”（异步的 JavaScript 与 XML 技术），AJAX的概念由Jesse James Garrett 提出。
<!--more-->
AJAX 的使用方法：
1. 使用 XMLHttpRequest 发请求
2. 服务器返回 XML 格式的字符串
3. JS 解析 XML，并更新局部页面

****
## 使用原生JS发送AJAX请求
前端代码
```javascript
myButton.addEventListener('click', (e) => {
  // 声明一个XMLHttpRequest对象
  let request = new XMLHttpRequest();
  // 初始化一个请求, 参数为 方法 路径 是否异步（默认为是）
  request.open('GET', '/xxx')
  request.onreadystatechange = () => {
    if (request.readyState === 4) {
      /* readyState 代理当前所处的状态：
       * 0 代理被创建，但未调用 open()方法  
       * 1 open() 被调用，send() 未调用
       * 2 send() 被调用，且头部和状态已经可获得
       * 3 响应体下载中；responseText 中已获取部分数据
       * 4 下载操作已完成
      **/
      if (request.status >=200 && request.status <300) {
        console.log(request.responseText);
      } else if(request.status >= 400) {
        console.log('请求失败')
      }
    }
  };
  // 发送请求
  request.send();
});
```

后端代码
```
if (path == '/xxx') {
    response.statusCode = 200;
    response.setHeader('Content-Type', 'text/json; charset=utf-8')
    response.write(`
    {
      "student": {
        "name": "张三",
        "age": "20",
        "school": "实验学校"
      }
    }
    `)
    response.end()
  } 
```