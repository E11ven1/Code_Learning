# JSON基础

[ApiPost](https://www.apipost.cn/)

## 1. JSON简述

JSON（JavaScript Object Notation，JS对象简称）是一种轻量级的**数据交换格式**。它基于==ECMAScript（欧洲计算机协会制定的JS规范）的一个子集，采用完全独立于编程语言的**文本格式**来存储和保存数据。简洁和清晰的层次结构是的JSON称为理想的数据交换语言。易于人阅读和理解，同时也易于机器解析和生成，并有效地提升网络传输效率

JSON特点：

- JSON是一种轻量级的数据交换格式
- JSON采用完全独立于编程语言的文本格式，就是说不同的编程语言JSON数据是一样的
- JSON易于人阅读和编写，同时也易于机器解析和生成（一般用于提升网络传输速率

## 2. XML与JSON的区别

> JSON 和 XML 都用于接收 web 服务端的数据。

1. XML：可扩展标记语言，是一种用于标记电子文件使其具有结构性的标记语言

2. JSON：JSON（JavaScript Object Notation，JS对象简称）是一种轻量级的**数据交换格式**。

3. 相同点：

   - 他们都可以作为一种数据交换格式
   - JSON 是纯文本
   - JSON 具有"自我描述性"（人类可读）
   - JSON 具有层级结构（值中存在值）
   - JSON 可通过 JavaScript 进行解析
   - JSON 数据可使用 AJAX 进行传输
   - JSON 和 XML 数据都是 "自我描述" ，都易于理解。
   - JSON 和 XML 数据都是有层次的结构
   - JSON 和 XML 数据可以被大多数编程语言使用

4. 不同点：
   - XML是重量级的，JSON是轻量级的，XML在传输过程中比较占用宽带，JSON占用宽带较少，易于**压缩**
   - XML和JSON都用在项目交互下，XML多用于做配置文件，JSON多用于数据交换
   - JSON 不需要结束标签
   - JSON 更加简短
   - JSON 读写速度更快
   - JSON 可以使用数组
   - JSON能够使用内建的 JavaScript eval() 方法进行解析
   - JSON不使用保留字

5. 为什么使用JSON

   - 对于AJAX应用程序来说，JSON比XML更快更易使用：

     - #### 使用 XML

       - 读取 XML 文档
       - 使用 XML DOM 来循环遍历文档
       - 读取值并存储在变量中

     - #### 使用 JSON

       - 读取 JSON 字符串
       - 用 eval() 处理 JSON 字符串

## 3. JSON语法格式

### 3.1 JSON语法介绍

```json
{
    "id":110,
    "name":"demo",
    "age":11
}
```

语法注意：

1. 外面由 **{}** 括起来
2. 数据以“键：值”对的形式出现（其中键多以字符串形式出现，值可取字符串，数值，甚至其他JSON对象
3. 每两个“键：值”对以**逗号**分隔（最后一个“键：值”对省略逗号
4. 参数返回值如果是string类型，就必须加引号，如果是数字类型，引号可加可不加

### 3.2 JSON语法

> JSON 语法是 JavaScript 语法的子集。

#### 1. JSON语法规则

 JSON 语法是 JavaScript 对象表示语法的子集。

- 数据在 **`名称/值`** 对中
- 数据由逗号 **` , `** 分隔
- 使用斜杆 **`\`** 来转义字符
- 大括号  **`{}`**  保存对象
- 中括号  **`[]`**  保存数组，数组可以包含多个对象

#### 2. JSON的两种结构

1. **对象：**大括号 **`{}`** 保存的对象是一个无序的**`名称/值`**对集合。一个对象以左括号 **{** 开始， 右括号 **}** 结束。每个"键"后跟一个冒号 **`:`**，**`名称/值`**对使用逗号 **`,`** 分隔。

   ![](https://www.runoob.com/wp-content/uploads/2013/09/object.png)

2. **数组：**中括号 **[]** 保存的数组是值（value）的有序集合。一个数组以左中括号 **[** 开始， 右中括号 **]** 结束，值之间使用逗号 **,** 分隔。

   ![](https://www.runoob.com/wp-content/uploads/2013/09/array.png)

   值（value）可以是双引号括起来的**字符串（string）、数值(number)、true、false、 null、对象（object）或者数组（array）**，它们是可以**嵌套**。

   ![](https://www.runoob.com/wp-content/uploads/2013/09/value.png)

#### 3. **JSON名称/值对**

   JSON数据的书写格式：

   ```json
   key:value
   ```

   名称/值对包括字段名称（在双引号中），后面跟一个冒号，然后是值

   ```json
   "name" : "A"
   ```

#### 4. JSON值

JSON值可以是：

- 数字（整数或浮点数）：整形或者浮点型
- 字符串（在双引号中）
- 逻辑值（true 或 false）
- 数组（在中括号中）
- 对象（在大括号中）
- null

#### 5. JSON对象

JSON对象在大括号`{}` 书写：

```json
{key1 : value1, key2 : value2, ... keyN : valueN }
```

#### 6. JSON数组

JSON数组在中括号`[]` 中书写

数组可包含多个对象：

```json
[
    { key1 : value1-1 , key2:value1-2 }, 
    { key1 : value2-1 , key2:value2-2 }, 
    { key1 : value3-1 , key2:value3-2 }, 
    ...
    { key1 : valueN-1 , key2:valueN-2 }, 
]
```

#### 7. JSON布尔值

- **JSON布尔值可以是`true` 或者`false`**

#### 8. JSON使用 **`JavaScript`** 语法

#### 9. JSON文件

- JSON 文件的文件类型是 **.json**
- JSON 文本的 MIME 类型是 **application/json**

### 3.3 JSON对象

#### 1.对象语法

```json
{ "name":"runoob", "alexa":10000, "site":null }
```

- JSON 对象使用在大括号 **{...}** 中书写。

  对象可以包含多个 **key/value（键/值）**对。

  key 必须是字符串，value 可以是合法的 JSON 数据类型（字符串, 数字, 对象, 数组, 布尔值或 null）。

  key 和 value 中使用冒号 **:** 分割。

  每个 key/value 对使用逗号 **,** 分割

#### 2.访问对象值

1. **可以使用点号 **.** 来访问对象的值：**

    ```json
    var myObj, x;
    myObj = { "name":"runoob", "alexa":10000, "site":null };
    x = myObj.name;
    ```

2. **也可以使用中括号（[]）来访问对象的值：**

    ```json
    var myObj, x;
    myObj = { "name":"runoob", "alexa":10000, "site":null };
    x = myObj["name"];
    ```

#### 3.循环对象

1. 可以使用 for-in 来循环对象的属性：

   ```json
   var myObj = { "name":"runoob", "alexa":10000, "site":null };
   for (x in myObj) {
       document.getElementById("demo").innerHTML += x + "<br>";
   }
   ```

2. 在 for-in 循环对象的属性时，使用中括号（[]）来访问属性的值：

   ```json
   var myObj = { "name":"runoob", "alexa":10000, "site":null };
   for (x in myObj) {
       document.getElementById("demo").innerHTML += myObj[x] + "<br>";
   }
   ```

#### 4.嵌套JSON对象

1. JSON 对象中可以包含另外一个 JSON 对象：

   ```json
   myObj = {
       "name":"runoob",
       "alexa":10000,
       "sites": {
           "site1":"www.runoob.com",
           "site2":"m.runoob.com",
           "site3":"c.runoob.com"
       }
   }
   ```

2. 可以使用点号 **.** 或者中括号 **[...]** 来访问嵌套的 JSON 对象

   ```json
   x = myObj.sites.site1;
   // 或者
   x = myObj.sites["site1"];
   ```

#### 5.修改值

1. 可以使用点号 **.** 来修改 JSON 对象的值：

   ```json
   myObj.sites.site1 = "www.google.com";
   ```

2. 可以使用中括号 **[...]** 来修改 JSON 对象的值：

   ```json
   myObj.sites["site1"] = "www.google.com";
   ```

#### 6.删除对象属性

1. 可以使用 **delete** 关键字来删除 JSON 对象的属性

   ```json
   delete myObj.sites.site1;
   ```

2. 可以使用中括号 **[...]** 来删除 JSON 对象的属性：

   ```json
   delete myObj.sites["site1"]
   ```

### 3.4 JSON数组

#### 1.数组作为JSON对象

```json
[ "Google", "Runoob", "Taobao" ]
```

- JSON 数组在中括号中书写。

  中括号 **[]** 保存的数组是值（value）的有序集合。一个数组以左中括号 **[** 开始， 右中括号 **]** 结束，值之间使用逗号 **,** 分隔。

- JSON 中数组值必须是合法的 JSON 数据类型（字符串, 数字, 对象, 数组, 布尔值或 null）。

#### 2.JSON对象中的数组

- 对象属性的值可以是一个数组：

  ```json
  {
  "name":"网站",
  "num":3,
  "sites":[ "Google", "Runoob", "Taobao" ]
  }
  ```

- 可以使用索引值来访问数组

  ```json
  x = myObj.sites[0];
  ```

#### 3.循环数组

- 可以使用 for-in 来访问数组：

  ```json
  for (i in myObj.sites) {
      x += myObj.sites[i] + "<br>";
  }
  ```

- 可以使用 for 循环：

  ```json
  for (i = 0; i < myObj.sites.length; i++) {
      x += myObj.sites[i] + "<br>";
  }
  ```

#### 4.嵌套JSON对象中的数组

- JSON 对象中数组可以包含另外一个数组，或者另外一个 JSON 对象：

  ```json
  myObj = {
      "name":"网站",
      "num":3,
      "sites": [
          { "name":"Google", "info":[ "Android", "Google 搜索", "Google 翻译" ] },
          { "name":"Runoob", "info":[ "菜鸟教程", "菜鸟工具", "菜鸟微信" ] },
          { "name":"Taobao", "info":[ "淘宝", "网购" ] }
      ]
  }
  ```

- 可以使用 for-in 来循环访问每个数组：

  ```json
  for (i in myObj.sites) {
      x += "<h1>" + myObj.sites[i].name + "</h1>";
      for (j in myObj.sites[i].info) {
          x += myObj.sites[i].info[j] + "<br>";
      }
  }
  ```

#### 5.修改数组值

- 可以使用索引值来修改数组值：

  ```json
  myObj.sites[1] = "Github";
  ```

  

#### 6.删除数组元素

- 可以使用 **delete** 关键字来删除数组元素：

  ```json
  delete myObj.sites[1];
  ```

### 3.5 JSON.parse()

> JavaScript 中将 JSON字符串 转换为 对象变量

- **JSON.parse()**

  JSON 通常用于与服务端交换数据。

  在接收服务器数据时一般是字符串。

  我们可以使用 JSON.parse() 方法将数据转换为 JavaScript 对象。

  ```json
  JSON.parse(text[, reviver])
  ```

  - 参数说明：
  - **text:**必需， 一个有效的 JSON 字符串。
  - **reviver:** 可选，一个转换结果的函数， 将为对象的每个成员调用此函数。

### 3.6 JSON.stringify

> JavaScript 中将 对象变量 转换为 JSON字符串

- JSON 通常用于与服务端交换数据。

  在向服务器发送数据时一般是字符串。

  我们可以使用 JSON.stringify() 方法将 JavaScript 对象转换为字符串

  ```json
  JSON.stringify(value[, replacer[, space]])
  ```

  - 参数说明：

  - **value**：必需， 要转换的 JavaScript 值（通常为对象或数组）。

  - **replacer**：可选。用于转换结果的函数或数组。

    如果 replacer 为函数，则 JSON.stringify 将调用该函数，并传入每个成员的键和值。使用返回值而不是原始值。如果此函数返回 undefined，则排除成员。根对象的键是一个空字符串：""。

    如果 replacer 是一个数组，则仅转换该数组中具有键值的成员。成员的转换顺序与键在数组中的顺序一样。当 value 参数也为数组时，将忽略 replacer 数组。

  - **space**：可选，文本添加缩进、空格和换行符，如果 space 是一个数字，则返回值文本在每个级别缩进指定数目的空格，如果 space 大于 10，则文本缩进 10 个空格。space 也可以使用非数字，如：\t。

### 3. JSON案例

1. 创建一个Maven类型的项目，名称为json_demo
2. 在json_demo项目的src/main下创建一个webapp目录
3. 在File - Project Structure - Facets选项下配置项目的web.xml文件
4. 声明JSON格式的对象、数组以及集合的数据格式。在项目的webapp目录下创建一个json_demo.html的页面

```json
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>
<h2>JavaScript 创建 JSON 对象</h2>
<p>
网站名称: <span id="jname"></span><br /> 
网站地址: <span id="jurl"></span><br /> 
网站 slogan: <span id="jslogan"></span><br /> 
</p>
<script> var JSONObject= {
    "name":"菜鸟教程",
    "url":"www.runoob.com", 
    "slogan":"学的不仅是技术，更是梦想！"
};
document.getElementById("jname").innerHTML=JSONObject.name 
document.getElementById("jurl").innerHTML=JSONObject.url 
document.getElementById("jslogan").innerHTML=JSONObject.slogan </script>
 
</body>
</html>
```



## 4. JSON数据的转换