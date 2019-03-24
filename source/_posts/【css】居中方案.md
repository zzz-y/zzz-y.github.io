---
title: 【css】居中方案
date: 2018-10-20 11:33:22
tags:
categories: CSS
---
前言：根据最近学习的课程，简单总结一下学习到的css左右布局以及居中方案。后期学习深入之后再回来进行css居中的完整总结。
<!--more-->
### 水平居中
#### 内联元素水平居中
将内联元素外部的块级元素的`text-align`设置为`center`，即可实现内联元素（`inline`、`inline-block`）的水平居中。
```html
<div>
  <span>居中</span>
</div>
<style>
div{
  border: 2px dashed orange;
  text-align: center;
  height: 50px;
}
</style>
```
[演示](http://js.jirengu.com/riqof/1/edit?html,css,output)

#### 块级元素水平居中
将固定宽度的块级元素的`margin-left`和`margin-right`设置为`auto`，即可实现块级元素的水平居中。
```html
<div>
  <div class="center">居中</div>
</div>
<style>
div{
  border: 2px dashed orange;
  text-align: center;
  height: 50px;
}
.center{
  background: orange;
  height: 30px;
  width: 60px;
  margin: 0 auto;
}
</style>
```
[演示](http://js.jirengu.com/riqof/2/edit?html,css,output)

#### 多个块级元素水平居中
将每个块级元素的`display`设置为`inline-block`，然后将它们的父容器的`text-align`设置为`center`，即可使多个块级元素水平居中。
```html
<div class="parent">
  <div class="child">块级元素1</div>
  <div class="child">块级元素2</div>
  <div class="child">块级元素3</div>
  <div class="child">块级元素4</div>
</div>
<style>
.child{
  display: inline-block;
}
.parent{
  border: 2px dashed orange;
  text-align: center;
  height: 60px;
}
</style>
```
[演示](http://js.jirengu.com/siyun/edit?html,css,output)

### 垂直居中
#### 内联元素垂直居中
设置内联元素的行高（`line-heigt`）和内联元素的父元素的高度（`height`）相等，且内联元素的字体大小远小于行高，即可使内联元素垂直居中。
```html
<div class="parent">
  <span>垂直居中</span>
</div>
<style>
.parent{
  border: 2px dashed orange;
  height: 80px;
}
span{
  font-size: 30px;
  line-height: 80px;
}
</style>
```
[演示](http://js.jirengu.com/tizir/edit?html,css,output)

#### 块级元素垂直居中
##### 固定高度的块级元素
通过绝对定位元素距离顶部50%，并设置margin-top向上偏移元素高度的一半，即可实现垂直居中。
```html
<div class="parent">
    <div class="child">固定高度垂直居中</div>
</div>
<style>
.parent {
  height: 140px;
  position: relative;
  border: 2px dashed orange;
}
.child {
  position: absolute;
  top: 50%;
  height: 100px;
  margin-top: -50px;
  background: orange;
}
</style>
```
[演示](http://js.jirengu.com/hemav/1/edit?html,css,output)
#### 未知高度的块级元素
借助CSS3中的transform属性向Y轴反向偏移50%的方法实现垂直居中
```html
<div class="parent">
    <div class="child">未知高度垂直居中</div>
</div>
<style>
.parent {
  height: 140px;
  position: relative;
  border: 2px dashed orange;
}
       
.child {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: orange;
}
</style>
```
[演示](http://js.jirengu.com/tucah/1/edit?html,css,output)
### 左右布局/左中右布局
给所有子元素添加 `float: left`，给父元素加 clearfix 类，清除浮动
html:
```html
<div class="clearfix">
  <div class="children">元素1</div>
  <div class="children">元素2</div>
  <div class="children">元素3</div>
</div>
```
css:
```css
.children{
  float: left;
}
.clearfix::after {
    display: block;
    content: '';
    clear: both;
}
```