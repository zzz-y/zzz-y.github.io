---
title: 【js】数据类型的转换
date: 2018-11-16 10:26:45
tags:
categories: js
---
> JavaScript 是一种弱类型语言，变量没有类型限制，可以随时赋予任意值。

<!--more-->
## Number类型
### Number()强制转换
使用`Number()`，将任意类型的值转换为`number`类型。
#### 简单类型转换

* 字符串：如果可以被解析为数值，则转换为相应的数值
* 字符串：如果不可以被解析为数值，返回 NaN
* 空字符串转为0
```javascript
Number('324') // 324
Number('324abc') // NaN
Number('') // 0
```

* 布尔值：true 转成 1，false 转成 0
* undefined：转成 NaN
* null：转成0
```javascript
Number(true) // 1
Number(false) // 0
Number(undefined) // NaN
Number(null) // 0
```

* 使用number()时，只要有一个字符无法转成数值，结果就是NaN
```javascript
parseInt('42 cats') // 42
Number('42 cats') // NaN
```
#### 复杂类型转换
仅当包含单个数值的数组转换时，可返回数值，否则均返回`NaN`
```javascript
Number({a: 1}) // NaN
Number([1, 2, 3]) // NaN
Number([5]) // 5
```
### parseInt()
将字符串转为整数。
* 字符串头部有空格时，空格会自动去除
* 字符串从头开始一个个字符依次转换，遇到不能转为数字的字符时，则返回已转好的部分。
* 字符串的第一个字符不能转换为数字时，返回`NaN`
```javascript
parseInt('8a') // 8
parseInt('15e2') // 15
parseInt('ab1') // NaN
parseInt('.3') // NaN
parseInt('') // NaN
parseInt('+') // NaN
parseInt('+1') // 1
```
* 字符串以0x或0X开头，parseInt会将其按照十六进制数解析
* 如果字符串以0开头，将其按照10进制解析
```javascript
parseInt('0x10') // 16
parseInt('011') // 11
```

### parseFloat()
将字符串转为浮点数
* 字符串符合科学计数法，则会进行相应的转换
```javascript
parseFloat('314e-2') // 3.14
parseFloat('0.0314E+2') // 3.14
```
### parseInt、parseFloat、Number的对比
```javascript
parseInt(true)  // NaN
parseFloat(true)  // NaN
Number(true) // 1

parseInt(null)  // NaN
parseFloat(null) // NaN
Number(null) // 0

parseInt('')  // NaN
parseFloat('') // NaN
Number('') // 0

parseInt('123.45#')  // 123
parseFloat('123.45#') // 123.45
Number('123.45#') // NaN
```
### 自动转换
javaScript遇到预期为数值的地方，系统内部会自动调用`Number()`，将参数值自动转换为数值。
* 使用一元运算符`+`将变量转换为数值
```javascript
+ '12dd' // NaN
+ '12' // 12
```
* 使用除`+`之外的运算符
```javascript
'5' - '2' // 3
'5' * '2' // 10
true - 1  // 0
false - 1 // -1
'1' - 1   // 0
'5' * []    // 0
false / '5' // 0
'abc' - 1   // NaN
null + 1 // 1
{} + 1 // 1
undefined + 1 // NaN
```
## String类型
### String()强制转换
使用`String()`，将任意类型的值转换为`String`类型。
#### 简单类型转换

* 数值：转为相应的字符串
* 字符串：转换后还是原来的值
* 布尔值：true转为字符串"true"，false转为字符串"false"
* undefined：转为字符串"undefined"
* null：转为字符串"null"
```javascript
String(123) // "123"
String('abc') // "abc"
String(true) // "true"
String(undefined) // "undefined"
String(null) // "null"
```

#### 复杂类型转换
如果是对象，返回一个类型字符串；如果是数组，返回该数组的字符串形式
```javascript
String({a: 1}) // "[object Object]"
String([1, 2, 3]) // "1,2,3"
```
### 自动转换
* 使用`toString()`
```javascript
({name:"Fjohn"}).toString() //  "[object Object]"
([1,2,3,4]).toString() // "1,2,3,4"
(new Date()).toString() // "Fri Jul 18 2014 09:08:55 GMT+0200"
(null).toString() // TypeError: Cannot read property 'toString' of null
(undefined).toString() // TypeError: Cannot read property 'toString' of undefined
({}).toString() // "[object Object]"
```
* 使用`+ ''`将其他类型数据转为`String`类型
```javascript
123 + '' // '123'
true + '' // 'true'
null + '' // 'null'
undefined + '' // 'undefined'
```

## Boolean类型
除了以下五个值的转换结果为false，其他的值全部为true
```javascript
Boolean(undefined) // false
Boolean(null) // false
Boolean(0) // false
Boolean(NaN) // false
Boolean('') // false
```
### Boolean()强制转换
使用`Boolean()`，将任意类型的值转换为`Boolean`类型。
### 自动转换
使用`!! expression`将其他类型值转换为`Boolean`类型

## 参考链接
* [阮一峰JavaScript教程 - 数据类型转换](https://javascript.ruanyifeng.com/grammar/conversion.html)