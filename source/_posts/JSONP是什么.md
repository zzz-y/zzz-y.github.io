---
title: JSONP是什么
date: 2018.12.18 09:03
tags:
categories: js
---
JSONP(JSON with padding)，服务器与客户端跨源通信的常用方法，可以让网页从别的网域获取数据。

<!--more-->
## JSONP的全部过程
1. 在页面中创建一个动态的`<script>`，
2. 通过`<script>`标签中的`src`写入对应服务器的地址发出`get`请求
3. 服务器接收到请求后，将数据作为参数放到一个指定名字的回调函数里传回来 
* url示例：
`http://www.domain.com:port/path?callback=callbackName`
* 一般`callbackName`使用随机数生成，为了避免对全局变量造成污染。在调用了回调函数之后，立刻删除这个回调函数。
* JSONP不支持`post`请求，因为`<script>`向浏览器发送的是`get`请求
## JSONP实现的示例

从 domain.com:8081 的客户端向 jack.com:8002 的服务器发送请求
```html
<script>
    let script = document.createElement('script');
    // 设置一个随机数拼接成回调函数的名称
    let name = 'lalala' + parseInt(Math.random() * 10000, 10); 
    // 设置回调函数
    window[name] = function(result){
        console.log(result);
    };
    // 向jack.com:8002发起请求
    script.src = 'http://jack.com:8002/lalala?callback='+name 
     // 动态地创建一个<script>
    document.body.appendChild(script);

    // 获取到请求返回的响应后，删除动态创建的 script 和回调函数
    // 请求成功的操作
    script.onload = function (e) {
        e.currentTarget.remove();
        delete window[name];
    };
     // 请求失败的操作
    script.onerror = function (e) {
        e.currentTarget.remove();
        delete window[name];
    };
</script>
```

 从jack.com:8002 的服务器获取数据的代码：
 ```
 if (path === '/lalala'){
    // 执行对数据库的操作
    let amount = fs.readFileSync('./db', 'utf8')
    amount -= 1
    fs.writeFileSync('./db', amount)
    // 获取回调函数的名称
    let callbackName = query.callback
    response.setHeader('Content-Type', 'application/javascript')
    // 将响应结果'success'作为参数传入回调函数
    response.write(`
        ${callback}.call(undefined, 'success')
    `)
    response.end()
}
 ```