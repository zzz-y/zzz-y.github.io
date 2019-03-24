---
title: HTTP 缓存
date: 2019.03.12
tags:
categories: HTTP
---
前端开发的时候，在页面刷新后，所有数据都会被清空。如果要使数据不被清除，这个时候就需要用到其他存储方式：`cookie`、`session`、`localStorage`、`sessionStorage`。

<!--more-->
## Cookie
****
1.  服务器通过 Set-Cookie 头给客户端一串字符串
2.  客户端每次访问相同域名的网页时，必须带上这段字符串
3.  客户端要在一段时间内保存这个Cookie
4.  Cookie 默认在用户关闭页面后就失效，后台代码可以任意设置 Cookie 的过期时间
5.  [大小大概在 4kb 以内](https://stackoverflow.com/questions/640938/what-is-the-maximum-size-of-a-web-browsers-cookies-key "null")

## Session
****
1. 将 Session Id（随机数）通过 Cookie 发给客户端
2. 客户端访问服务器时，服务器读取 Session Id
3. 服务器有一块内存（哈希表）保存了所有 session
4. 通过 Session Id 我们可以得到对应用户的隐私信息，如 id、email
5. 这块内存（哈希表）就是服务器上的所有 session

## localStorage & sessionStorage
****
1. localStorage / sessionStorage 跟 HTTP 无关
2. HTTP 不会带上 localStorage / sessionStorage 的值
3. 只有相同域名的页面才能互相读取 localStorage / sessionStorage（没有同源那么严格）
4. 每个域名 localStorage / sessionStorage 最大存储量为 5Mb 左右（每个浏览器不一样）
5. localStorage 永久有效 （除非用户清除缓存)
sessionStorage 在用户关闭页面（会话结束）后就失效

## Session 和 Cookie 的关系
****
Cookie 保存在客户端，每次都随请求发送给 Server

Session 保存在 Server 的内存里，其 Session ID 是通过 Cookie 发送给客户端的

## 异同
****
### 生命周期
Cookie：后台可设置过期时间，默认在用户关闭页面后就失效

localStorage：永久有效，除非用户清除缓存

sessionStorage：在用户关闭页面（会话结束）后就失效

### 存放数据大小
Cookie：4KB 

localStorage & sessionStorage：最大存储量为 5MB 左右

### HTTP请求
Cookie：每次都会携带在HTTP头中，如果使用cookie保存过多数据会带来性能问题

localStorage 和 sessionStorage：仅在客户端（即浏览器）中保存，不参与和服务器的通信

## 应用场景
****
Cookie：客户端记录用户信息，可在同一浏览器的不同进程间共享，比如两个`chrome`窗口。

Session：存储特定用户会话所需的属性及配置信息，在web页面跳转时，信息不丢失。常用场景：
1. 存储整个会话过程中保持用户状态的信息，比如登录信息或者用户浏览时产生的其他信息
2. 存储只需要在页面**重新加载**过程中，或者**一组功能页**之间保持状态的对象
3.在 Web服务器上保持用户的**状态信息**供在任何时间从任何设备上的页面进行访问

localStorage：对数据实时同步都有较高要求的都会是这个技术的应用场景：
1. 同源窗口通信：例如通知中心上的未读数量，在不同的窗口中，只要消息数量更新，所有窗口的消息提示数量都会更新；localStorage 也可用来管理购物车的内容。
2. 填写表单时，自动存储表单填写内容

sessionStorage：使用 sessionStorage 进行页面传值

## HTTP缓存
****
`cache-control` 被用于在http 请求和响应中通过指定指令来实现缓存机制。缓存指令是单向的, 这意味着在请求设置的指令，在响应中不一定包含相同的指令。

`cache-control` 可以让浏览器在一定时间内不去访问服务器，直接用本地的硬盘或者内存做出响应，若要更新只要在入口处把`URL`稍做变动，和以前的所有`URL`都不一样，浏览器就不会使用缓存，而去下载最新的文件，然后把最新的内容缓存下来。这样会让网页特别的快。

`Expire` 设置缓存过期时间
这个过期时间指的是本地时间，若用户本地时间错误，则所有缓存都会出错

`Expire` 和 `cache-control` 同时设置时，优先使用 `cache-control`

`ETag`  的缓存是在 HTTP 请求中设置 `ETag` 的值，如果用户再次访问相同 `URL` 时，服务器将客户端的 `ETag` 和当前版本的资源的 `ETag` 进行比较，如果两个值匹配， 服务器返回 304 状态，告诉客户端可使用缓存