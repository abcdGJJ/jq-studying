## DOM操作的分类

1. **DOM Core**

DOM Core 并不专属于javascript，支持一种支持DOM的程序设计语言都可以使用它。

javascript中的getElementById()、getElementsByTagName()、getAttribute()、setAttribute()等方法都是DOM Core 的组成部分

2. **HTML-DOM**

它提供了一些简明的记号来描述各种HTML元素的属性

例：document.forms、element.src

3. **CSS-DOM**

针对CSS的操作

例：element.style.color = "red"



## JQuery中的DOM操作

##### 查找元素节点

```javascript
var $li = $("ul li:eq(1)");//第2个<li>节点
var li_txt = $li.text();//文本内容
alert(li_txt);
```

##### 查找属性节点

```javascript
var $para = $("p");
var p_txt = $para.attr("title");//获取title值
alert(p_txt);
```

##### 创建元素节点

创建两个\<li\>元素，并把它们作为\<ul\>元素节点的子节点添加到DOM树

使用JQuery工厂函数$(html)

```javascript
var $li_1 = $("<li></li>");
var $li_2 = $("<li></li>");
$("ul").append($li_1);
$("ul").append($li_2);
//或者使用链式写法：$("ul").append($li_1).append($li_2);
```

##### 创建文本节点

```javascript
var $li_1 = $("<li>香蕉</li>");
var $li_2 = $("<li>梨</li>");
$("ul").append($li_1);
$("ul").append($li_2);
//或者使用链式写法：$("ul").append($li_1).append($li_2);
```

##### 插入节点

|       方法       |                    描述                    |                    示例                    |
| :------------: | :--------------------------------------: | :--------------------------------------: |
|    append()    |                向元素内部追加内容                 | $("p").append("\<b>你好</b>")    <p>我想说<b>你好</b></p> |
|   appendTo()   | 将所有匹配的元素追加到指定的元素中。即颠倒常规的$(A).append(B)方法，把A增加到B中 |       $("<b>你好</b>").appendTo("p")       |
|   prepend()    |                向元素内部前置内容                 |                                          |
|  prependTo()   |                  参照上上条                   |                                          |
|    after()     |               在匹配元素之后插入内容                | $("p").after("<b>你好</b>")        <p>我想说</p><b>你好</b> |
| insertAfter()  |                  颠倒上一条                   |                                          |
|    before()    |                在元素之前添加内容                 |                                          |
| insertBefore() |                  颠倒上一条                   |                                          |

##### 删除节点

- remove()方法

```javascript
var $li = $("ul li:eq(1)").remove();//删除第二个li元素
$li.appendTo("ul");//把刚才删除的节点又重新添加到ul元素里
```

也可以使用appendTo()方法来简化以上代码

```javascript
$("ul li:eq(1)").appendTo("ul");
//appendTo()也可以用于移动元素
//移动元素时首先从文档上删除此元素，然后将元素插入到文档节点
```

也可以通过传参来选择性地删除元素

```javascript
$("ul li").remove("li[title!=菠萝]");
```


