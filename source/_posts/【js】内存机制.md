---
title: 【js】内存机制
date: 2018-11-16 10:34:49
tags:
categories: js
---
JavaScript创建变量（对象，字符串等）时分配内存，并且在不再使用它们时“自动”释放。 后一个过程称为垃圾回收。
<!--more-->
## 数据的存储方式
JS引擎将内存分为代码区和数据区，其中，数据区分为 Stack（栈内存） 和 Heap（堆内存）。简单类型的数据直接存在 Stack 里，复杂类型的数据是把 Heap 地址存在 Stack 里。
## 垃圾回收
当我们申明变量、函数、对象的时候，系统会自动为他们分配内存。而当一个变量、函数、对象不再被引用时，他们就是垃圾，将被回收。
## 内存泄漏
由于一些浏览器的bug，使本应被标记为垃圾的数据没有被标记为垃圾，内存会被永久占用。

解决方法是将页面关闭前将所有内容置为null
```javascript
window.onunload = function(){
  document.body.onclick = null;
}
```
## 关于内存的题目
```javascript
var a = 1
var b = a
b = 2
// 请问 a 显示是几？  

// 此时a的值不受b影响，所以
a === 1
```

```javascript
var a = {name: 'a'}
var b = a
b = {name: 'b'}
// 请问现在 a.name 是多少？

// 此时，b指向一个新的对象，a值不受影响，所以
a.name === 'a'
```

```javascript
var a = {name: 'a'}
var b = a
b.name === 'b'
// 请问现在 a.name 是多少？

// 此时，a，b指向的对象中name的值改变，所以
a.name = 'b'
```

```javascript
var a = {name: 'a'}
var b = a
b = null
// 请问现在 a 是什么？

// 此时，a值不受影响，所以
a === {name: 'a'}
```

```javascript
var a = {n:1};  
var b = a; 
a.x = a = {n:2};  

// 此时 a.x 中的 a 指的仍是之前的地址，而 a = {n:2}中的 a 指的是新的地址

alert(a.x);
alert(b.x);

// 所以
a.x === undefined
b.x === { n: 2 } 
```
