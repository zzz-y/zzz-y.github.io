---
title: 实现一个jQuery的API
date: 2018.12.02 21:05
tags:
categories: js
---
本文通过使用原生DOM API实现类似于jQuery的元素添加类和获取元素文字的方法来理解jQuery的实现原理

<!--more-->
## html部分
```html
<ul>
  <li id="item1">1</li>
  <li id="item2">2</li>
  <li id="item3">3</li>
  <li id="item4">4</li>
  <li id="item5">5</li>
</ul>
```

## 实现元素添加类
封装一个`addClass()`函数，设置两个参数，一个是操作的元素集合`nodes`，一个是添加的`className`
```javascript
function addClass(nodes, className) {
    for (let i = 0; i < nodes.length; i++) {
      nodes[i].classList.add(className)
    }
}
```
## 实现设置元素的文本
封装一个`setText()`函数，设置两个参数，一个是操作的元素集合`nodes`，一个是设置的文本`text`
```javascript
function setText(nodes, text) {
    for (let i = 0; i < nodes.length; i++) {
      nodes[i].textContent = text
    }
}
```
## 给`addClass()`和`setText()`一个公共的命名空间
```javascritp
function jquery(nodes) {
 return {
    addClass: function(className) {
      for (let i = 0; i < nodes.length; i++) {
        nodes[i].classList.add(className)
      }
    },
    setText: function(text) {
      for (let i = 0; i < nodes.length; i++) {
        nodes[i].textContent = text
      }
    }
  }
}

var node2 = jquery(document.querySelectorAll('li'))
node2.addClass('red')

```
## 判断函数`jquery`传入的参数是元素还是字符串
通过`typeof`判断传入的参数是否为字符串，若不是，再次判断其是否为元素。然后对传入的参数进行处理，将需要操作的节点存入声明的`nodes`对象中
```javascritp
function jquery(nodeOrSelector) {
 let nodes = {}
  if (typeof nodeOrSelector === 'string') {
    let temp = document.querySelectorAll(nodeOrSelector)
    for (let i = 0; i < temp.length; i++) {
      nodes[i] = temp[i]
    }
    nodes.length = temp.length
  } else if (nodeOrSelector instanceof Node) {
    nodes = {
      0: nodeOrSelector,
      length: 1
    }
  }
 return {
    addClass: function(className) {
      for (let i = 0; i < nodes.length; i++) {
        nodes[i].classList.add(className)
      }
    },
    setText: function(text) {
      for (let i = 0; i < nodes.length; i++) {
        nodes[i].textContent = text
      }
    }
  }
}
```
## 完整代码
```javascript
window.jQuery = function(nodeOrSelector) {
  let nodes = {}
  if (typeof nodeOrSelector === 'string') {
    let temp = document.querySelectorAll(nodeOrSelector)
    for (let i = 0; i < temp.length; i++) {
      nodes[i] = temp[i]
    }
    nodes.length = temp.length
  } else if (nodeOrSelector instanceof Node) {
    nodes = {
      0: nodeOrSelector,
      length: 1
    }
  }
  return {
    addClass: function(className) {
      for (let i = 0; i < nodes.length; i++) {
        nodes[i].classList.add(className)
      }
    },
    setText: function(text) {
      for (let i = 0; i < nodes.length; i++) {
        nodes[i].textContent = text
      }
    }
  }
}
window.$ = jQuery

$('li').addClass('red') // 可将所有 li 的 class 添加一个 red
$('li').setText('hi') // 可将所有 li 的 textContent 变为 hi
```
