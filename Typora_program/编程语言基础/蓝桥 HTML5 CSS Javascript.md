# 蓝桥 HTML5 CSS Javascript

## HTML

### HTML概述

#### HTTP 基础

##### HTTP 概述

> 超文本传输协议（HTTP，HyperText Transfer Protocol)是互联网上应用最为广泛的一种网络协议。所有的 WWW 文件都必须遵守这个标准。设计 HTTP 最初的目的是为了提供一种发布和接收 HTML 页面的方法。1960 年美国人 Ted Nelson 构思了一种通过计算机处理文本信息的方法，并称之为超文本（Hypertext）,这成为了 HTTP 超文本传输协议标准架构的发展根基。Ted Nelson 组织协调万维网协会（World Wide Web Consortium）和互联网工程工作小组（Internet Engineering Task Force ）共同合作研究，最终发布了一系列的 RFC，其中著名的 RFC 2616 定义了 HTTP 1.1。

注：定义来自于搜狗百科。

![img](https://doc.shiyanlou.com/courses/1552/1226977/67af99a4ede57b2f3269f8a7a18f02e2-0)

上图描述了客户端和服务器的交互过程。当用户在浏览器输入网址后，浏览器与服务器建立了一个连接，浏览器给 Web 服务器发送了一个 HTTP 请求，服务器接收并解析请求后，返回响应。HTTP 响应中包含状态代码和返回资源的内容（响应正文）。

##### 常见状态码

- 200 ：成功。
- 400 ：客户端请求有语法错误，服务器端不能理解。
- 401 ：该请求可能未经过授权。
- 403 ：服务器端收到该请求，但是拒绝为它提供服务，可能是没有权限等等。
- 404 ：该资源没找到。
- 500 ：服务器端发生了一个不可预知的错误。
- 503 ：服务器端当前还不能处理客户端的这个请求，可能过段时间之后才能恢复正常。



#### 什么是HTML

HTML（超文本标记语言）是一种用于创建网页的标准标记语言。 HTML 不需要编译，可以直接由浏览器执行，它的解析依赖于浏览器的内核。 它不是一种编程语言，而是一种标记语言。



#### HTML 网页结构

一个网页的基本结构：

```html
<!doctype html>
<html>
  <head>
    <title>HTML 简介</title>
  </head>
  <body></body>
</html>
```

`<!DOCTYPE html>` 是我们的文档声明头。他告诉了浏览器，本文档处理的是 HTML 文档。`html` 标签即根元素，此处表示文档的开始。`head` 标签是网页的头部，设置网页的相关信息。`title` 标签设置网页标题。`body` 标签定义文档的主体，也就是我们的主要内容。



#### HTML 注释

在 HTML 中满足以下格式的内容即为注释，被注释的内容将不会被渲染和显示。

```
<!-- 在此处写注释 -->
```

**注：**在开始标签中有一个惊叹号，但是结束标签中没有。浏览器不会显示注释，但是能够帮助记录。

```html
<!doctype html>
<html>
  <body>
    <!--这是一段注释。注释不会在浏览器中显示。-->

    <p>这是一段普通的段落。</p>
  </body>
</html>
```



### HTML 常用标签

#### HTML 标签

超文本标记语言（英语简称：HTML ）标记标签通常被称为 HTML 标签，HTML 标签是 HTML 语言中最基本的单位，HTML 标签是 SGML（标准通用标记语言下的一个应用）最重要的组成部分。HTML 标签的大小写无关的，例如 `<body>` 和 `<BODY>` 表示的意思是一样的，都代表“主体”，推荐使用小写。

#### 双标签（双标记）

双标记也称体标记，是指由开始和结束两个标记符组成的标记。其基本语法格式如下：

```
<标记名></标记名>
```

常见的双标签有：

```html
<html></html>
<head></head>
<title></title>
<body></body>
<h1></h1>
<p></p>
<div></div>
<span></span>
<a></a>
<ul></ul>
```

例子 `<a></a>`：

```html
<a href="https://www.lanqiao.cn">实验楼</a>
```

#### 单标签（单标记）

单标记也称空标记，是指用一个标记符号即可完整地描述某个功能的标记。其基本语法格式如下：

```
<标记名/>
```

常见的单标签有：

```html
<br />
<!--换行-->
<hr />
<!--水平分隔线-->
<meta />
<img />
```

#### 标签的关系

- 嵌套关系

```html
<head>
  <title> </title>
</head>
```

- 并列关系

```html
<head></head>
<body></body>
```



#### HTML 元素

HTML 元素指的是从开始标签（start tag）到结束标签（end tag）的所有代码。

例子：

```html
<p>I Love You</p>
```

注：这个元素定义了 HTML 文档中的一个段落。这个元素拥有一个开始标签 `<p>`，以及一个结束标签 `</p>`。元素内容是：`I Love You`



#### HTML 常见标签

##### h 系类标签

`h` 标签有六种 `h1`，`h2`，`h3`，`h4`，`h5`，`h6`，它代表着我们的标题。

```html
<!doctype html>
<html>
  <head>
    <title>HTML 简介</title>
    <meta charset="utf-8" />
  </head>
  <body>
    <h1>我是一级标题</h1>
    <h2>我是二级标题</h2>
    <h3>我是三级标题</h3>
    <h4>我是四级标题</h4>
    <h5>我是五级标题</h5>
    <h6>我是六级标题</h6>
  </body>
</html>
```



##### p 标签

`p` 标签是我们的文本标签。



##### 图片标签

HTML 的图像是通过标签 `<img>` 来定义的。 语法: `<img src="图片地址"/>` 。



##### a 标签

<a href="链接"> 标签是超链接标签，意思就是我们点击它可以跳转到一个网页。



##### div 标签

<div> 标签是一个块级元素，块级元素占据其父元素（容器）的整个空间，你可以把它想成一个盒子。 <div> 能够设置其宽高，后面我们会讲到。



##### 换行标签和空格字符

在浏览器显示页面时，浏览器会移除源代码中多余的空格和空行，所有连续的空格或空行都会被认为是一个空格。如果希望在不产生一个新段落的情况下换行，可以使用 `<br/>` 标签。如果想使用空格的话可以使用 ` ` 字符。



##### 水平分割线

`<hr/>` 标签用于在 HTML 页面中创建一条水平线。



#### 容器标签（div、span）

##### 标签

标签 `<div>` 可将网页页面分割成不同的独立部分，通常用于定义文档中的区域或节。该标签是一个块级元素，浏览器会自动在 `<div>` 和 `</div>` 所标记的区域前后自动放置一个换行符。



##### span 标签

标签 `<span>` 通常作为文本的容器，它没有特定的含义和样式，只有与 CSS 同时使用才可以为指定文本设置样式属性。该标签是一个内联元素，他与块级元素相反，内联元素不会自动在前后自动放置换行符，因此内联元素会默认显示在同一行。



#### HTML 列表

列表作为网页设计的重要内容之一，能够用来制作导航栏和新闻列表等。HTML 列表分为：有序列表（ol），无序列表（ul）以及自定义列表（dl）。

#### 无序列表与有序列表

无序列表是一个项目的列表，此列项目使用实心圆、空心圆、方块进行标记，无序列表使用 `<ul>` 标签。同样，有序列表也是一列项目，列表项目使用数字进行标记。有序列表始于 `<ol>` 标签。每个列表项始于 `<li>` 标签。

```html
<p>无序列表</p>
<ul>
  <li>列表项1</li>
  <li>列表项2</li>
</ul>

<p>有序列表</p>
<ol>
  <li>列表项1</li>
  <li>列表项2</li>
</ol>
```

![img](https://doc.shiyanlou.com/courses/1552/1226977/47cf04c5bc00e949fbcf7ab2e42c4ecc-0)

可以看到有多少个列表项就有多少个 `<li>` 标签。

**无序列表和有序列表的 type 属性：**

type 属性定义了列表项前项目符号的类型。

`<ul>` 标签的 type 属性：

| 值           | 备注   |
| ------------ | ------ |
| disc（默认） | 实心圆 |
| circle       | 空心圆 |
| square       | 小方块 |

`<ol>` 标签的 type 属性：

| 值        | 备注                        |
| --------- | --------------------------- |
| 1（默认） | 数字表示（1，2，3...)       |
| A         | 大写字母表示（A,B,C...)     |
| a         | 小写字母表示（a,b,c...)     |
| I         | 大写罗马数字表示(I,II,III…) |
| i         | 小写罗马数字表示(i,ii,iii…) |

我们来看其中一两个 type 属性：

```html
<p>无序列表</p>
<ul type="circle">
  <li>空心圆列表项1</li>
  <li>空心圆列表项2</li>
</ul>

<p>有序列表</p>
<ol type="A">
  <li>列表项1</li>
  <li>列表项2</li>
</ol>
```

![img](https://doc.shiyanlou.com/courses/1552/1226977/1feaa73cb508751fc4f8744d63144266-0)

是不是很简单呢？只需要修改 type 属性，就可以看到不同的项目符号了，自己动手试试其他的吧！

#### 自定义列表（dl）

定义：自定义列表不仅仅是一列项目，而是项目及其注释的组合。自定义列表以 `<dl>` 标签开始。每个自定义列表项以 `<dt>` 开始。每个自定义列表项的定义以 `<dd>` 开始。自定义列表的列表项前没有任何项目符号。

语法格式：

```html
<dl>
  <dt>名词1</dt>
  <dd>名词1解释1</dd>
  ...
  <dt>名词2</dt>
  <dd>名词2解释1</dd>
  ...
</dl>
```

例子：

```html
<h2>一个自定义列表：</h2>
<dl>
  <dt>春天</dt>
  <dd>是万物复苏，百花争艳的季节</dd>
  <dt>夏天</dt>
  <dd>是夏日绵绵，烈日炎炎的季节</dd>
</dl>
```

在浏览器中的运行效果为：

![img](https://doc.shiyanlou.com/courses/1552/1226977/f3ff64c89a6de71182e033e314548dbf-0)



### HTML 表格与 div

![](https://doc.shiyanlou.com/document-uid897174labid9222timestamp1545370661694.png)

table 元素布局：

- 优点：

1. 理解比较简单。
2. 不同的浏览器看到的效果一般相同。

- 缺点：

1. 显示样式和数据绑定在一起。
2. 布局的时候灵活度不高。
3. 一个页面可能会有大量的 table 元素，代码冗余度高。
4. 增加带宽。
5. 搜索引擎不喜欢这样的布局。

div 元素布局：

- 优点：

1. 符合 W3C 标准。
2. 搜索引擎更加友好。
3. 样式的调整更加方便，内容和样式的分离，使页面和样式的调整变得更加方便。
4. 节省代宽，代码冗余度低。
5. 表现和结构分离，在团队开发中更容易分工合作而减少相互关联性。



### HTML 表单

`<form>` 标签用于创建 HTML 表单，常见的表单格式为：

```html
<form name="" method="" action=""></form>
```

- name：定义表单的名字。
- method：定义表单结果从浏览器传送到服务器的方式，默认参数为：`get` 。`post` 安全性更高，因此常用作传输密码等，而 `get` 安全性较低，一般用于查询数据。
- action：发送数据要去的地址。它的值必须是一个有效的 URL，可以是相对 URL 也可以是绝对 URL。如果没有提供此属性或者 `action="#"`，则数据将被发送到包含表单的页面的 URL。

网页中的表单由许多不同的表单元素组成，这些表单元素包括文字字段、单选按钮、复选框、按钮等。

#### 文字字段

在网页中最常见的表单元素就是文字字段，用户可以在文字字段内输入字符或者单行文本。 语法：

```html
<input
  type="text"
  name="控件名称"
  value="文字字段的默认取值"
  size="控件的长度"
  maxlength="最长字符数"
/>
```

该语法包含了许多参数，除了 `type` 参数以外，其他的参数都是可选的，大家可以自行选择。举个例子：

```html
<form name="formBox" method="post" action="">
  姓名：<input type="text" name="name" size="20" /><br />
  年龄:<input type="text" name="age" size="40" value="10" maxlength="3" />
</form>
```

![1](https://doc.shiyanlou.com/courses/1552/1226977/48fe8ad047e687d69431d18786acd523-0)

可以尝试给年龄输入值，如果文本字段长度超过了 3，就不能再输入了。

#### 密码输入框

密码输入框是一种特殊的文字字段，他的各个属性和文字字段是相同的，但是输入进密码输入框的字符全部是“*”表示，保证周围人看不见输入的文本。

```html
<input type="password" name="pwd" />
```

#### 单选按钮

单选按钮可以使用户从选择列表中选择一个选项。

```html
<form name="formBox" method="post" action="">
  <input type="radio" name="sex" value="male" checked />男<br />
  <input type="radio" name="sex" value="female" />女
</form>
```

几个单选按钮可以连接在一起，只需要把它们的 `name` 值设置为相同的。同一组中只有一个按钮可以同时被选。如果没有选中任何一个，那么整个单选按钮池就被认为处于未知状态，且不会随表单提交。 可以尝试如果 name 不相同或者没有 name 会是什么情况。

#### 复选框

复选框可以让用户从一个选项列表中选择超出一个的选项。

```html
<form name="formBox" method="post" action="">
  <input type="checkbox" name="music" checked />音乐<br />
  <input type="checkbox" name="art" />美术<br />
  <input type="checkbox" name="math" />数学<br />
</form>
```

复选框可以拥有自己的名字，并不需要属于一个组。

#### 按钮

HTML 表单中，有三种按钮：提交按钮，重置按钮，匿名按钮。我们可以使用 `<button>` 元素或者 `<input>` 元素来创建一个按钮。`type` 属性的值指定显示什么类型的按钮。

**提交按钮（submit）**

用于发送表单数据给服务器。

语法：

```html
<form name="formBox" method="post" action="">
  <input type="text" value="输入的内容" />
  <button type="submit">This a submit button</button>

  <!--or-->

  <input type="submit" value="This is a submit button" />
</form>
```

**重置按钮（reset）**

重置按钮用来清除用户在页面中输入的信息。

语法：

```html
<form name="formBox" method="post" action="">
  <input type="text" />
  <button type="reset">This a reset button</button>

  <!--or-->

  <input type="reset" value="This is a reset button" />
</form>
```

在文本框中输入内容，点击按钮即可清除。

**匿名按钮（button）**

没有自动生效的按钮，但是可以使用 JavaScript 代码进行定制。如果你省略了 `type` 属性，那么这就是默认值。

语法：

```html
<button type="button">This a anonymous button</button>

<!--or-->
<button>This a anonymous button</button>

<!--or-->
<input type="button" value="This is a anonymous button" />
```

不管使用的是 `<button>` 元素还是 `<input>` 元素，按钮的行为都是一样的。它们的不同点在于：

- 从前面的例子中也可以看出 `<button>` 元素允许你使用 HTML 内容作为其标记内容，但 `<input>` 元素只接受纯文本内容。
- 使用 `<button>` 元素，可以有一个不同于按钮标签的值（通过将其设置为 `value` 属性）。（但是在 IE 8 之前的版本中是不行的）。



菜单和列表主要是用来选择给定答案中的一种，这类选择中往往答案比较多。

#### 下拉菜单

下拉菜单能够节省页面空间，正常状态下显示一个选项，单击展开所以选项。

```html
<form name="formBox" method="post" action="">
  <select name="select">
    <option value="成都">成都</option>
    <option value="广州">广州</option>
    <option value="四川">四川</option>
    <option value="上海">上海</option>
  </select>
</form>
```

![img](https://doc.shiyanlou.com/courses/1552/1226977/5b8ceabf1f70a4c9f9de44c988c269c0-0)

注意：下拉菜单的宽度是由 `<option>` 标记中包含的最长文本的宽度决定的。

#### 列表项

在页面中列表项可以显示出几条信息，一旦超出这个信息量，在列表项右侧会出现滚动条，拖动滚动条可以看到所有选项。

```html
<form name="formBox" method="post" action="">
  <select name="select" size="2" multiple="multiple">
    <option value="成都">成都</option>
    <option value="广州">广州</option>
    <option value="四川">四川</option>
    <option value="上海">上海</option>
  </select>
</form>
```

![img](https://doc.shiyanlou.com/courses/1552/1226977/46d2b29df310445f489325b2496353dd-0)

`size="2"` 表示一次显示 2 条数据。



#### 文本域

当用户想要填入多行文本时，就应该使用文本域而不是文本字段。文本域使用 `<textarea>` 标记。

```html
<form name="formBox" method="post" action="">
  留下您的联系方式：
  <textarea name="textarea" cols="35" rows="5"></textarea>
</form>
```

![img](https://doc.shiyanlou.com/courses/1552/1226977/c65996e46046a25524bc374863662918-0)

`cols` 代表列数，`rows` 代表行数。



### HTML 图像与框架

#### 图像标签

在 HTML 中，图像由 `<img>` 标签定义。语法为：

```html
<img src="url" alt="" />
```

<img> 是空标签，它只包含属性，没有闭合标签。要在页面上显示图像，你需要使用源属性（src）。src 的值是图像文件的 URL，也就是引用该图像的文件的的绝对路径或相对路径。alt 规定图像的替代文本即当图片未成功显示的时候显示的文本信息。title 设置鼠标悬停时显示的内容（一般不用设置）。此外还可以通过设置 width 和 height 的值来设置图片的宽和高。



#### 相对路径

这种路径是以引用文件的网页所在位置为参考基础，而建立出的目录路径。因此，当保存于不同目录的网页引用同一个文件时，所使用的路径将不相同，故称之为相对路径。

- 图像文件和 HTML 文件位于同一文件夹：只需输入图像文件的名称即可，比如：`<img src="syl.png" />`。
- 图像文件位于 HTML 文件的下一级文件夹：输入文件夹名和文件名，之间用`/`隔开，比如：`<img src="img/img1/syl.png" />`。
- 图像文件位于 HTML 文件的上一级文件夹：在文件名之前加入`../` ，如果是上两级，则需要使用 `../ ../`，以此类推，比如：`<img src="../syl.png" />`。

#### 绝对路径

指当所有网页引用同一个文件时，所使用的路径都是一样的。比如`D:\webStudy\img\syl.png`或者 `https://labfile.oss.aliyuncs.com/courses/1236/syl.png`。



使用框架，你可以在同一个浏览器窗口中显示不止一个页面。

语法：

```html
<iframe src="URL">
  <!-- URL指向不同的页面 -->
</iframe>
```

#### iframe - 设置高度与宽度

属性默认以像素为单位,但是你可以指定其按比例显示 (如："60%")。

#### iframe - 移除边框

`frameborder` 属性用于定义 iframe 表示是否显示边框。设置属性值为 "0" 移除 iframe 的边框:

```html
<iframe
  src="https://www.lanqiao.cn/"
  width="400"
  height="400"
  frameborder="0"
></iframe>
```

#### 使用 iframe 来显示目标链接页面

iframe 可以显示一个目标链接的页面，目标链接的属性必须使用 iframe 的属性。

```html
<p><a href="https://www.lanqiao.cn/" target="shiyanlou">实验楼</a></p>
<iframe width="400" height="400" name="shiyanlou"></iframe>
```

注： 因为 `a` 标签的 `target` 属性是名为 `shiyanlou` 的 iframe 框架，所以在点击链接时页面会显示在 iframe 框架中。需要保证 iframe 框架的 `name` 属性的名称与 `a` 标签的 `target` 属性名一致。



### HTML5 简介

#### HTML5 代码规范

#### 使用正确的文档类型

文档类型声明位于 HTML 文档的第一行：

```html
<!doctype html>
```

#### 可以省略 html 和 body 标签但不推荐

在标准 HTML5 中， `<html>` 和 `<body>` 标签是可以省略的，比如下面的写法也是正确的：

```html
<!doctype html>
<head>
  <title>页面标题</title>
</head>

<h1>我是标题</h1>
<p>我是段落。</p>
```

但是不推荐省略掉，建议还是写成下面这样：

```html
<!doctype html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title></title>
  </head>
  <body>
    <h1>我是标题</h1>
    <p>我是段落。</p>
  </body>
</html>
```

#### 使用小写元素名

HTML5 元素名可以使用大写和小写字母，建议使用小写字母，会显得更加好看一点，千万不要使用大小写混写，那样会显得很不专业。建议的写法如下：

```html
<section>
  <p>我是段落。</p>
</section>
```

#### 关闭所有 HTML 元素

在 HTML5 中, 你不一定要关闭所有元素 (例如 `<p>` 元素)，但是建议每个元素都要添加关闭标签。比如下面这样写也不会报错：

```txt
<section>
  <p>我是段落甲。
  <p>我是段落乙。
</section>
```

建议写成下面这样：

```html
<section>
  <p>我是段落甲。</p>
  <p>我是段落乙。</p>
</section>
```

#### 关闭空的 HTML 元素

在 HTML5 中, 空的 HTML 元素也不一定要关闭,我们可以这样写：

```txt
<meta charset="utf-8">
```

建议的写法是还是关闭：

```html
<meta charset="utf-8" />
```

#### 使用小写属性名

同样的 HTML5 属性名允许使用大写和小写字母。但是我们依然建议使用小写字母：

```html
<div class="test"></div>
```

#### 属性值

HTML5 属性值可以不用引号。但是属性值我们推荐使用引号，尤其是属性值有空格的话，一定要使用引号，不然不会起作用，属性的命名如果很长我们建议使用驼峰命名法：

```html
<div class="test changeColor"></div>
```

#### 图片属性

图片通常使用 `alt` 属性。 在图片不能显示时，它能替代图片显示。建议定义好图片的尺寸，在加载时可以预留指定空间，减少闪烁。比如：

```html
<img src="syl.png" alt="HTML5" style="width:520px;height:1314px" />
```

#### 空格前后的等号

等号的前后可以使用空格，也可以不使用，推荐少用空格。

```html
<link rel="stylesheet" href="styles.css" />
```

#### 避免一行代码过长

使用 HTML 编辑器，一行代码过长时左右滚动代码来查看是不方便的。如果实在太长，建议分为几行来写。

#### 空格和缩进

不要无缘无故的添加空行，一般一个模块或一个功能添加一个空行便于区分，缩进使用两个空格，不建议使用 Tab。

#### 注释

```html
<!-- 这是注释 -->
```

快捷键为 `Ctrl + /`。当然我们首先要选中要注释的代码再使用快捷键。

注：编码风格建议统一，不要乱而杂，另外建议大家养成多写注释的习惯，因为时间久了，如果没有注释，可能你自己都不知道自己当初写的是啥。

HTML5 定义了一组新的语义化标记来描述元素的内容，可以简化 HTML 页面设计，并且使用浏览器搜索网页时，也可以利用这些元素。

首先我们来看一个普通的页面的布局方式：

![此处输入图片的描述](https://doc.shiyanlou.com/md04171522012052410570957.gif)

以上是很常见的 div+css 布局模式，通过 class 名称来区分不同的结构，包括头部、导航、文章内容、右边栏，还有底部模块。

而 HTML5 新标签带来的新的布局则是下面这种情况：

![此处输入图片的描述](https://doc.shiyanlou.com/md04171522012052410554136.gif)

代码如下所示：

```html
<!doctype html>
<html>
  <head>
    <title>my page</title>
  </head>
  <body>
    <header>header</header>
    <nav>nav</nav>
    <article>
      <section>section</section>
    </article>
    <aside>aside</aside>
    <footer>footer</footer>
  </body>
</html>
```

注：上面的代码没有 CSS 样式，只是展示 HTML 结构。拥有具体含义的标签，使得代码有很直观的感受，搜索器也能很容易地抓取合适的信息。

#### section 标签

`<section>` 表示文档中的一个区域（或节）。比如章节、页眉、页脚或文档中的其他部分，一般来说会包含一个标题。

例子：

```html
<body>
  <section>
    <h1>section是什么？</h1>
    <p>一个新章节</p>
  </section>
</body>
```

注：不要把 `<section>` 元素作为一个普通的 div 容器来使用。一般来说，一个 `<section>` 应该出现在文档大纲中。

#### article 标签

`<article>` 标签定义独立的内容。常常使用在论坛帖子，报纸文章，博客条目，用户评论等独立的内容项目之中。`article` 可以嵌套，内层的 `article` 对外层的 `article` 标签有隶属关系。

例子：

```html
<body>
  <article>
    <h1>实验楼是什么</h1>
    <p>一个在线学习的网站</p>
  </article>
</body>
```

#### nav 标签

`<nav>` 标签定义导航链接的部分：描绘一个含有多个超链接的区域，这个区域包含转到其他页面，或者页面内部其他部分的链接列表。

例子：

```html
<body>
  <nav>
    <ul>
      <li><a href="#">HTML</a></li>
      <li><a href="#">CSS</a></li>
      <li><a href="#">JavaScript</a></li>
    </ul>
  </nav>
</body>
```

注：并不是所有的链接都必须使用 `<nav>` 标签，它只用来将一些热门的链接放入导航栏。一个网页也可能含有多个 `<nav>` 标签,例如一个是网站内的导航列表,另一个是本页面内的导航列表。

#### header 标签

`<header>` 标签定义文档的页眉，通常是一些引导和导航信息。它不局限于写在网页头部，也可以写在网页内容里面。

通常 `header` 标签至少包含一个标题标记（h1-h6），还可以包括 `hgroup` 标签，还可以包括表格内容、标识、搜索表单、nav 导航等。

例子：

```html
<body>
  <header>
    <h1>网站标题</h1>
    <h2>网站副标题</h2>
  </header>
</body>
```

#### footer 标签

`<footer>` 标签定义 section 或 document 的页脚，包含了与页面、文章或是部分内容有关的信息，比如说文章的作者或者日期。 它和 `header` 标签使用基本一样，可以在一个页面中多次使用，如果在一个区段的后面加入了 `footer` 标签，那么它就相当于该区段的页脚了。

例子：

```html
<body>
  <footer>
    <span>Copyright @2013-2019 实验楼在线教育</span>
  </footer>
</body>
```

#### aside 标签

`<aside>` 标签表示一个和其余页面内容几乎无关的部分，被认为是独立于该内容的一部分并且可以被单独的拆分出来而不会使整体受影响。其通常表现为侧边栏或者嵌入内容。他们通常包含在工具条，例如来自词汇表的定义。也可能有其他类型的信息，例如相关的广告、笔者的传记、web 应用程序、个人资料信息，或在博客上的相关链接。

例子：

```html
<body>
  <aside>
    <h1>实验楼简介</h1>
    <p>一个在线学习的网站</p>
  </aside>
</body>
```



HTML5 中废除了一些纯表现的元素、只有部分浏览器支持的元素、一些会对可用性产生负面影响的元素。

#### 纯表现元素

纯表现元素指的是可以用 CSS 代替的元素。例如：`basefont`、`big`、`center`、`font`、`s`、`strike`、`tt`、`u`这些元素，他们的功能都是纯粹为页面展示服务的，html5 提倡把页面展示性功能放在 CSS 样式表中统一处理，所以将这些元素废除，用 CSS 样式进行替代。

#### 对可用性产生负面影响的元素

对于 `frameset` 元素、`frame` 元素与 `noframes` 元素，由于 frame 框架对网页可用性存在负面影响，在 html5 中已不支持 frame 框架，只支持 iframe 框架，html5 中同时将 `frameset`、`frame` 和 `noframes` 这三个元素废除。

#### 只有部分浏览器支持的元素

对于 `applet`、`bgsound`、`blink`、`marquee` 等元素，由于只有部分浏览器支持，特别是 `bgsound` 元素以及 `marquee` 元素，只被 IE 支持，所以在 html5 中被废除。其中 `applet` 元素可由 `embed` 元素或 `object` 元素替代，`bgsound` 元素可由 `audio` 元素替代，`marquee` 可以由 javascript 编程的方式替代。



### HTML5 表单

#### HTML 表单元素

#### datalist 元素

`datalist` 元素用于为文本框提供一个可供选择的列表，使用 `datalist` 元素来为表单小部件提供建议的、自动完成的值，并使用一些 `option` 子元素来指定要显示的值。然后使用 `list` 属性将数据列表绑定到一个文本域(通常是一个 `<input>` 元素)。

一旦数据列表与表单小部件相关联，它的选项用于自动完成用户输入的文本。通常，这是作为一个下拉框向用户展示的，在输入框中输入可能匹配的内容。

#### autocomplete 属性

`autocomplete` 属性规定表单是否应该启用自动完成功能：自动完成允许浏览器预测对字段的输入，当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出在字段中填写的选项。当 `autocomplete` 属性值为 `on` 时表示启用自动完成功能，为 `off` 时表示关闭。`autocomplete` 属性适用于 `<form>`，以及下面的 `<input>` 类型：`text`, `search`, `url`, `telephone`, `email`, `password`, `datepickers`, `range` 以及 `color`。

#### autofocus 属性

`autofocus` 属性规定在页面加载时，域自动地获得焦点。适用于所有 `<input>` 标签的类型。

#### form 属性

`form` 属性规定输入域所属的一个或多个表单。`form` 属性适用于所有 `<input>` 标签的类型。`form` 属性必须引用所属表单的 `id`。

`multiple` 属性规定输入域中可选择多个值，适用于以下类型的 `<input>` 标签：`email` 和 `file`。

注：如需引用一个以上的表单，请使用空格分隔的列表。

#### multiple 属性

`multiple` 属性规定输入域中可选择多个值，适用于以下类型的 `<input>` 标签：`email` 和 `file`。

#### novalidate 属性

`novalidate` 属性规定在提交表单时不应该验证 `form` 或 `input` 域。适用于 `<form>`，以及下面的 `<input>` 类型：`text`, `search`, `url`, `telephone`, `email`, `password`, `datepickers`, `range` 以及 `color`。

#### pattern 属性

```html
pattern` 属性规定用于验证 `input` 域的模式（pattern）。模式（pattern） 是正则表达式。`pattern` 属性适用于以下类型的 `<input>` 标签：`text`, `search`, `url`, `telephone`, `email` 以及 `password
```

#### placeholder 属性

`placeholder` 属性提供一种提示（hint），描述输入域所期待的值。适用于以下类型的 `<input>` 标签：`text`, `search`, `url`, `telephone`, `email` 以及 `password`。提示（hint）会在输入域为空时显示出现，会在输入域获得焦点时消失。

#### required 属性

`required` 属性规定必须在提交之前填写输入域（不能为空）。适用于以下类型的 `<input>` 标签：`text`, `search`, `url`, `telephone`, `email`, `password`, `date pickers`, `number`, `checkbox`, `radio` 以及 `file`。



#### HTML5 输入类型

HTML5 拥有多个新的表单输入类型。这些新特性提供了更好的输入控制和验证。

#### Input 类型 - email

`email` 类型用于应该包含 e-mail 地址的输入域。在提交表单时，会自动验证 email 域的值。

#### Input 类型 - url

`url` 类型用于应该包含 URL 地址的输入域。在提交表单时，会自动验证 url 域的值。

#### Input 类型 - number

`number` 类型用于应该包含数值的输入域。属性 `max` 设定允许输入的最大值，属性 `min` 设定允许输入的最小值，属性 `value` 设定默认值，属性 `step` 设定合法的数字间隔（比如 `step` 的值为 `2`，则合法的数字为 `-2`,`0`,`2`,`4` 等）。

#### Input 类型 - range

`range` 类型用于应该包含一定范围内数字值的输入域。`range` 类型显示为滑动条。同样的 `range` 也有 `max`，`min`，`value`，`step` 属性与上面所讲的 `number` 中的一致。

#### Input 类型 - Date Pickers（日期选择器）

HTML5 拥有多个可供选取日期和时间的新输入类型：

- date - 选取日、月、年

- month - 选取月、年

- week - 选取周和年

- time - 选取时间（小时和分钟）

- datetime - 选取时间、日、月、年（UTC 时间）**注意：此类型已被弃用，目前大多数浏览器都不再支持。**

- datetime-local - 选取时间、日、月、年（本地时间）

  

#### Input 类型 - color

  `color` 类型用于选择颜色。



### HTML5 Canvas API

#### Canvas元素

`canvas` 元素的外观和 `img` 元素相似，但是没有 `img` 元素的 `src` 属性和 `alt` 属性。canvas 的 `width` 属性和 `height` 属性用来设置画布的宽和高，单位是 px。默认的画布的高度是 150px，宽度是 300px。

注意: 默认情况下 `<canvas>` 元素没有边框和内容，标签通常需要指定一个 `id` 属性 (脚本中经常引用)。

canvas 元素本身并不能实现图形绘制，所有的绘制工作必须要和 JavaScript 脚本结合起来。首先，给 canvas 元素添加一个 id 属性，这样能够让我们在 JavaScript 脚本中通过 id 属性找到对应的 canvas 元素。

```html
<canvas
  id="myCanvas"
  width="200"
  height="100"
  style="border:2px solid #000000;"
>
  <!-- 添加id属性值为myCanvas -->
</canvas>
```

添加了 id 属性后，找到对应的 canvas 元素：

```js
var myCanvas = document.getElementById("myCanvas");
// 通过document.getElementById来找到id为myCanvas的元素
```

然后通过 canvas 元素的 getContext()方法获取上下文，即创建 Context 对象，以获取允许进行绘制的 2D 环境。

```js
var ctx = myCanvas.getContext("2d");
```

最后通过 Context 对象的相关方法完成绘制，比如：fillStyle()等。

```js
ctx.fillStyle = "red";
//设置矩形的位置和尺寸（位置从 左上角原点坐标开始，尺寸为100*100的矩形）
ctx.fillRect(0, 0, 100, 100);
```

整体的代码：

```html
<!doctype html>
<html>
  <head>
    <meta charset="UTF-8" />
    <title></title>
  </head>

  <body>
    <!--添加canvas元素，设置画布的大小-->
    <canvas id="mycanvas" style="width:200;height:100">
      对不起，你的浏览器不支持canvas
    </canvas>

    <script type="text/javascript">
      var myCanvas = document.getElementById("mycanvas");
      var ctx = myCanvas.getContext("2d");
      //设置颜色
      ctx.fillStyle = "red";
      //设置矩形的位置和尺寸（位置从 左上角原点坐标开始，尺寸为100*100的矩形）
      ctx.fillRect(0, 0, 100, 100);
    </script>
  </body>
</html>
```

![img](https://doc.shiyanlou.com/courses/1552/1226977/062ec50b990a308967fe89791bbb85ec-0)

**注意：**进行绘制时，需要指定确定的坐标位置，坐标原点(0,0)位于 canvas 的左上角，x 轴水平方向向右延伸，y 轴垂直向下延伸，如图：

![此处输入图片的描述](https://doc.shiyanlou.com/document-uid897174labid9222timestamp1550108838365.png)

#### 直线绘制

- strokeStyle：设置或返回笔的颜色、渐变或模式。默认值为：#000000。
- lineWidth：设置或返回当前的线条宽度 ，以像素计。
- beginPath()：起始一条路径，或重置当前路径。
- closePath()：创建从当前点回到起始点的路径。
- moveTo()：把路径移动到画布中的指定点，不创建线条。
- lineTo()：添加一个新点，然后在画布中创建从该点到最后指定点的线条。
- stroke()：绘制已定义的路径。



#### 矩形绘制

##### rect() 方法介绍

使用 `rect()` 方法创建矩形。语法为：

```html
ctx.rect(x,y,width,height);
```

参数说明：

- x 表示矩形左上角的 x 坐标。
- y 表示矩形左上角的 y 坐标。
- width 表示矩形的宽度，以像素计。
- height 表示矩形的高度，以像素计。

注：使用 `stroke()` 或 `fill()` 方法在画布上实际地绘制矩形。

##### strokeRect() 方法介绍

使用 `strokeRect()` 方法绘制矩形（不填色）。笔触的默认颜色是黑色。语法为：

```js
ctx.strokeRect(x, y, width, height);
```

注：参数与 `rect()` 方法一致，唯一的区别是这里不需要再加一句 `stroke()` 或 `fill()` 方法。无法填色。



##### fillRect() 方法介绍

使用 `fillRect()` 方法创建实心矩形。语法为：

```js
ctx.fillRect(x, y, width, height);
```

注：参数说明与前面一致，默认的填充颜色为黑色，可以使用 `fillStyle` 属性来设置用于填充绘图的颜色、渐变或模式。

##### clearRect() 方法介绍

使用 `clearRect()` 方法清空给定矩形内的指定像素。语法为：

```js
ctx.clearRect(x, y, width, height);
```

注：参数说明与前面一致。



#### 圆和扇形的绘制

使用 `arc()` 方法绘制圆或者椭圆。语法为：

```js
ctx.arc(x, y, r, sAngle, eAngle, counterclockwise);
```

参数说明：

- x 表示圆的中心的 x 坐标。
- y 表示圆的中心的 y 坐标。
- r 表示圆的半径。
- sAngle 表示起始角，以弧度计（特别需要注意的是弧的圆形的三点钟位置是 0 度而不是常规以为的 90 度）。
- eAngle 表示结束角，以弧度计。
- counterclockwise 表示绘制圆的方向，值为 false 表示顺时针，为 true 表示逆时针。是一个可选值，默认值是 false。



#### 填充和渐变

使用 `fillStyle` 属性，设置或返回用于填充绘画的颜色、渐变或模式。语法为：

```js
ctx.fillStyle = color | gradient | pattern;
```

参数说明：

- color 表示绘图填充的颜色。默认值是 `#000000`。
- gradient 表示用于填充绘图的渐变对象（线性或放射性）。
- pattern 表示用于填充绘图的 pattern 对象。



#### 渐变

使用 `createLinearGradient()` 方法创建线性渐变。语法为：

```js
ctx.createLinearGradient(x0, y0, x1, y1);
```

参数说明：

- x0 表示渐变开始点的 x 坐标。
- y0 表示渐变开始点的 y 坐标。
- x1 表示渐变结束点的 x 坐标。
- y1 表示渐变结束点的 y 坐标。

使用 `addColorStop()` 方法规定渐变对象中的颜色和停止位置。语法为：

```js
gradient.addColorStop(stop, color);
```

参数说明：

- stop 表示渐变中开始与结束之间的位置。是介于 `0.0` 与 `1.0` 之间的值。
- color 表示在结束位置显示的 CSS 颜色值。

注：`addColorStop()` 方法与 `createLinearGradient()` 或 `createRadialGradient()` 一起使用。我们可以多次调用 `addColorStop()` 方法来改变渐变。如果我们不对 `gradient` 对象使用该方法，那么渐变将不可见。为了获得可见的渐变，至少需要创建一个色标。



使用 `createRadialGradient()` 方法创建放射状/环形的渐变。语法为：

```js
ctx.createRadialGradient(x0, y0, r0, x1, y1, r1);
```

参数说明：

- x0 表示渐变的开始圆的 x 坐标。
- y0 表示渐变的开始圆的 y 坐标。
- r0 表示开始圆的半径。
- x1 表示渐变的结束圆的 x 坐标。
- y1 表示渐变的结束圆的 y 坐标。
- r1 表示结束圆的半径。

##### fill() 方法

使用 `fill()` 方法填充当前的图像（路径）。默认颜色是黑色。填充另一种颜色/渐变使用 `fillStyle` 属性。

语法为：

```js
ctx.fill();
```

注：如果路径未关闭，那么 `fill()` 方法会从路径结束点到开始点之间添加一条线，以关闭该路径，然后填充该路径。



#### 文字绘制

##### fillText() 方法

使用 `fillText()` 方法在在画布上绘制实心文本。语法为：

```js
ctx.fillText(text, x, y, maxWidth);
```

参数说明：

- text 规定在画布上输出的文本。
- x 表示开始绘制文本的 x 坐标位置（相对于画布）。
- y 表示开始绘制文本的 y 坐标位置（相对于画布）。
- maxWidth 表示允许的最大文本宽度，以像素计。可选。



##### strokeText() 方法

使用 `strokeText()` 方法在画布上绘制空心文本。语法为：

```js
ctx.strokeText(text, x, y, maxWidth);
```

注：参数说明与 `fillText()` 方法一致。



##### font 属性

使用 `font` 属性设置或返回画布上文本内容的当前字体属性。`font` 属性使用的语法与 CSS `font` 属性相同。



##### textAlign 属性

使用 `textAlign` 属性设置或返回文本内容的当前对齐方式。语法为：

```js
ctx.textAlign = "center|end|left|right|start";
```

参数说明：

- start 默认值，表示文本在指定的位置开始。
- center 表示文本的中心被放置在指定的位置。
- end 表示文本在指定的位置结束。
- left 表示文本左对齐。
- right 表示文本右对齐。

注：使用 `fillText()` 或 `strokeText()` 方法在实际地在画布上绘制并定位文本。



##### textBaseline 属性

`textBaseline` 属性设置或返回在绘制文本时的当前文本基线。语法为：

```js
ctx.textBaseline = "alphabetic|top|hanging|middle|ideographic|bottom";
```

参数说明：

- alphabetic 表示文本基线是普通的字母基线。默认值。
- top 表示文本基线是 `em` 方框的顶端。
- hanging 表示文本基线是悬挂基线。
- middle 表示文本基线是 `em` 方框的正中。
- ideographic 表示文本基线是表意基线。
- bottom 表示文本基线是 `em` 方框的底端。



#### 图片绘制

使用 `drawImage()` 方法在画布上绘制图像、画布或视频。`drawImage()` 方法也能够绘制图像的某些部分，或增加或减少图像的尺寸。

canvas 绘制图片的基本格式为：

```js
//创建一个图片对象
var image = new Image();
//设置图片的路径
image.src = "xxx";
//当图片加载完成后
image.onload = function () {
  //绘制图片
  ctx.drawImage();
};
```

语法 1，在画布上定位图像：

```js
ctx.drawImage(img, x, y);
```

语法 2，在画布上定位图像，并规定图像的宽度和高度：

```js
ctx.drawImage(img, x, y, width, height);
```

语法 3，剪切图像，并在画布上定位被剪切的部分：

```js
ctx.drawImage(img, sx, sy, swidth, sheight, x, y, width, height);
```

参数说明：

- img 规定要使用的图像、画布或视频。
- sx 表示开始剪切的 x 坐标位置。可选值。
- sy 表示开始剪切的 y 坐标位置。可选值。
- swidth 表示被剪切图像的宽度。可选值。
- sheight 表示被剪切图像的高度。可选值。
- x 表示在画布上放置图像的 x 坐标位置。
- y 表示在画布上放置图像的 y 坐标位置。
- width 表示要使用的图像的宽度（伸展或缩小图像）。可选值。
- height 表示要使用的图像的高度，（伸展或缩小图像）。可选值。