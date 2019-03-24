---
title: HTML入门(1)
date: 2018-10-14 10:08:50
tags:
categories: HTML
---
### 万维网联盟
[万维网联盟](https://zh.wikipedia.org/wiki/%E4%B8%87%E7%BB%B4%E7%BD%91%E8%81%94%E7%9B%9F)（World Wide Web Consortium，W3C），又称W3C理事会，是万维网的主要国际标准组织。
为解决网上应用中不同平台、技术和开发者带来的不兼容问题，保障网上信息的顺利和完整流通，万维网联盟制定了一系列标准并督促网上应用开发者和内容提供者遵循这些标准。标准的内容包括使用语言的规范，开发中使用的导则和解释引擎的行为等等。W3C也制定了包括XML和CSS等的众多影响深远的标准规范。
<!--more-->
### MDN
[MDN Web Docs](https://developer.mozilla.org/zh-CN/)（旧称Mozilla Developer Network、Mozilla Developer Center，简称MDN）是一个汇集众多Mozilla基金会产品和网上技术开发文档的免费网站。
MDN可以理解为一个工具类网站，所有HTML、CSS、JavaScript方面的内容，都可以在MDN中找到详细介绍。

### HTML
HTML(HyperText Markup Language，超文本标记语言)是一种用于创建网页的标准标记语言，与CSS、JavaScript一起被众多网站用于设计令人赏心悦目的网页、网页应用程序以及移动应用程序的用户界面。 

### HTML5和H5
HTML5是在2014年由W3C宣布制定完成的第五套标准规范，而H5指的是能运行在微信上的网页。
> HTML5是一个标准，而H5应该是一个技术合集。
(参考：[H5是什么](https://www.zhihu.com/question/30363342))

### 空元素
不可能存在子节点（例如内嵌的元素或者元素内的文本）的元素。
在HTML中有以下空元素：
- `<area>`: 在图片上定义一个热点区域，可以关联一个超链接，仅在`<map>`元素内部使用。
- `<base>`: 指定用于一个文档中包含的所有相对URL的基本URL。一个文档中只能有一个`<base>`元素。
- `<br>`: 换行
- `<col>`: 定义表格中的列
- `<colgroup>`: 当span属性存在时，该元素为空元素
- `<command>`: 表示一个用户可以调用的命令，此功能已废弃
- `<embed>`: 将外部内容嵌入文档中的指定位置
- `<hr>`: 水平线
- `<img>`: 图像
- `<input>`
- `<keygen>`: 此功能已废弃
- `<link>`: 
- `<meta>`: 
- `<param>`: 为`<object>`元素定义参数
- `<source>`: 为`<picture>`、`<audio>` 和 `<video>`指定多个媒体资源
- `<track>`: 被当作媒体元素`<audio>` 和 `<video>`的子元素来使用
- `<wbr>`: 

### 可替换元素
1.  一个内容不受CSS视觉格式化模型控制，CSS渲染模型并不考虑对此内容的渲染，且元素本身一般拥有固有尺寸（宽度，高度，宽高比）的元素，被称之为可替换元素。
2. 可替换元素就是浏览器根据元素的标签和属性，来决定元素的具体显示内容。
3. 典型的可替换元素有 `<img>`、 `<object>`、 `<video>` 和表单元素，如`<textarea>`、 `<input>`。
4. 某些元素只在一些特殊情况下表现为可替换元素，例如 `<audio>` 和 `<canvas>`。

### HTML常用标签
##### DOCTYPE（文档类型声明）
在HTML中，文档类型声明是必要的，所有文档的头部，都有`<!DOCTYPE html>`，这个声明是为了确保浏览器按照最佳的相关规范进行渲染，而不是使用一个不符合规范的渲染模式。

##### &lt;html&gt; 元素
HTML文档的根元素，一个页面中有且只有一个根元素，所有其他元素必须是此元素的后代。

##### &lt;head&gt; 元素
规定文档相关的配置信息（元数据），包括文档的标题，引用的文档样式和脚本等。
当`<head>`元素中什么都没有的时候，可省略。
可用于`<head>`元素内的元素有: `<title>, <base>, <link>, <style>, <meta>, <script>, <noscript>, <command>`

##### &lt;meta&gt; 元素
提供有关页面的元信息，比如针对搜索引擎和更新频度的描述和关键词。
```
<meta charset="UTF-8">   声明当前文档所使用的字符编码
<meta http-equiv="content-type" content="text/html"> 定义文档的MIME TYPE
<meta name="keywords" content="HTML,ASP,PHP,SQL"> 定义文档级元数据的名称
```

##### &lt;title&gt; 元素
定义文档的标题，显示在浏览器的标题栏或标签页上。它只可以包含文本，若是包含有标签，则包含的任何标签都不会被解释。

##### &lt;link&gt; 元素
规定了外部资源与当前文档的关系。 这个元素可用来为导航定义一个关系框架。这个元素最常于链接样式表。

##### &lt;script&gt; 元素
用于嵌入或引用可执行脚本。

##### &lt;body&gt; 元素
必须是 html 元素的直接子元素，表示文档的内容

##### &lt;h1&gt;~ &lt;h6&gt;标题元素
标题元素呈现了六个不同的级别的标题，`<h1>` 级别最高，而 `<h6>` 级别最低。在使用时，避免跳过某级标题：始终要从 `<h1>` 开始，接下来依次使用 `<h2>` 等。

##### &lt;a&gt; 元素
可以创建一个到其他网页、文件、同一页面内的位置、电子邮件地址或任何其他URL的超链接。
属性：
- `download` 指示浏览器下载URL而不是导航到它，因此将提示用户将其保存为本地文件
- `href`  包含超链接指向的URL或URL片段。
   1. `href=""`  页面刷新
   2. `href="#"`  页面锚点变成#，页面滚动到顶部
   3. `href="../index.html"`  相对路径
   4. `href="?name=11"`  参数
   5. `href="//qq.com"`  无协议， 浏览器会根据当前协议，补全无协议链接的协议。如果用 file:// 协议浏览页面，就会访问到 file://qq.com，这是一个不存在的路径，应该尽量不使用 file:// 协议预览网页，以免无协议链接出错
   6. `href="javascript:;"`  javascript 伪协议
- `target`  指定在何处显示链接的资源。
   1. `_self`: 当前页面加载。这个是默认值。
   2. `_blank`: 新窗口打开
   3. `_parent`: 加载响应到当前框架的父框架。如果没有父级框架，和_self的行为一致
   4. `_top`: 加载响应进入顶层框架。如果没有父级框架，和_self的行为一致

##### 比较&lt;strong&gt;与&lt;b&gt;&nbsp;&nbsp;&nbsp;&lt;em&gt;与&lt;i&gt;
`<strong>`: 表示文本十分重要，一般用粗体显示，是一个逻辑状态。
`<b>`: 表示样式上的加粗，是一个物理状态。
`<em>`: 表示着重强调其内容，把内容呈现为斜体
`<i>`: 表示从正常的散文中区分出的文本, 如电影或书籍的名字，一个外来词, 或者当文本指的是一个字的定义，而不是其自身代表的语义。内容呈现为斜体

##### &lt;img&gt; 元素
代表文档中的一个图像。
- `alt` 定义描述图像的替换文本。若图像的url错误、图像还未被下载时，用户将看到这个文字。
- `src` 必须，图像的url
- `title` 当鼠标悬停在图片上方时，显示title文字

##### &lt;ol&gt; & &lt;ul&gt;列表元素
- `ol` 有序列表
- `ul` 无序列表
- 无论是有序列表还是无序列表，只能嵌套`li`元素，在`li`元素中可再嵌套其他元素

##### 定义列表（&lt;dl&gt; &lt;dt&gt; &lt;dd&gt;）
`dl` 表示整个列表，`dt` 表示一个标题，`dd` 表示对标题的解释
```html
<dl>
   <dt>梁静茹</dt>
      <dd>她是一位歌手</dd>
   <dt>彭于晏</dt>
      <dd>他是一位演员</dd>
</dl>
```

##### 表格
```html
<table>
    <colgroup>
        <col width="100"><col width="200"><col width="100"><col width="70">
    </colgroup>
    <thead>
        <tr>
            <th>项目</th><th>姓名</th><th>班级</th><th>分数</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <th></th><th>小明</th><th>1</th><th>94</th>
        </tr>
        <tr>
            <th></th><th>小红</th><th>2</th><th>96</th>
        </tr>
        <tr>
            <th>平均分</th><th></th><th></th><th>95</th>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <th>总分</th><th></th><th></th><th>190</th>
        </tr>
    </tfoot>
</table>
```
- `tr` table row
- `td` table data
- `col` 定义表格中的列，大部分属性在HTML5中已废弃，现基本很少使用该元素，大多直接对表格进行CSS样式控制
- `colgroup`、`thead`、`tbody`、`tfoot`标签顺序和展示顺序无关
-  在table元素改变样式border-collapse:collapse;时，表格的border可合并

##### &lt;form&gt; 元素
表示了文档中的一个区域，这个区域包含有交互控制元件，用来向web服务器提交信息。
- `action` 指定请求路径
- `method` 指定请求方法
   1. `post`: 指的是 HTTP POST 方法; 表单数据会包含在表单体内然后发送给服务器
   2. `get`: 指的是 HTTP GET 方法; 表单数据会附加在 action 属性的URI中，并以 '?' 作为分隔符, 然后这样得到的 URI 再发送给服务器
   3. 这个值可以被 `<button>` 或者 `<input>` 元素中的 `formmethod` 属性覆盖
- `target`  指示在提交表单之后，在哪里显示收到的回复
   1. `_self`: 当前页面重新加载返回值。这个是默认值。
   2. `_blank`: 新窗口加载返回值
   3. `_parent`: 在父级的frame中以HTML4或HTML5文档形式加载返回值，如果没有父级的frame，和_self一致
   4. `_top`: 在当前文档的最高级内加载返回值，如果没有父级，和_self的行为一致。
- 若form中只有一个按钮`<button>`且没有定义type属性，则`<button>`该自动升级为提交按钮；
若定义type属性为button，则这个form表单没有提交按钮。
- 若form中只有一个input且type为button，则这个表单没有提交按钮；
若type为submit时，则为提交按钮。
- submit是唯一能确定form表单能不能点击提交的按钮

##### &lt;input&gt; 元素
文本框：
```html
<input type="text" name="userName"/>
```
密码框：
```html
<input type="password" name="userPwd"/>
```
多选按钮：
```html
<label><input type="checkbox" name="fruit" value="apple"/>苹果</label>
<label><input type="checkbox" name="fruit" value="orange"/>橘子</label>
<label><input type="checkbox" name="fruit" value="banana"/>香蕉</label>
```
单选按钮：
```html
<label><input type="radio" name="sex" value="man"/>男</label>
<label><input type="radio" name="sex" value="woman"/>女</label>
```
区间：
```html
<input type="range" min="0" max="100" step="1"/>
```
日期控件：
```html
<input type="date"/>
```
不含时区的时间控件:
```html
<input type="time"/>
```
表单提交按钮：
```html
<input type="submit">
```
表单重置按钮：
```html
<input type="reset">
```

##### &lt;select&gt; 元素
下拉选择框控件，下拉框中的选项为`<option>`，可以由`<optgroup>`分组。
- `required`: 规定select的值不可为空
- `disabled`: 用户不可选
- `selected`: 是否已选中
- `multiple`: 是否可多选，默认单选


