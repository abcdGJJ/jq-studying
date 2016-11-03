# JQuery中的事件

#####  加载DOM

在常规的JS中，页面加载完毕后给DOM添加事件通常采用window.onload方法，而在JQuery中，使用的是$(document).ready()方法。它们的区别如下：

1. 执行时机

JS方法是在网页中所有的元素（包括所有的关联文件）完全加载到浏览器后才执行。而JQ方法注册的事件处理程序在DOM就绪时就可以被调用，并不意味这些元素关联的文件都以下载完毕

JQ中另一个关于页面加载的方法load()方法。如果绑定在window对象上，则会在所有内容加载完毕后触发，如果绑定在元素上，则会在元素加载完毕后触发

```javascript
$(window).load(function () {})
//等价于
window.onload = function () {}
```

2. 事件绑定

```javascript
bind(type [, data], fn)
```

type包括：blur、focus、load、resize...等事件

第二个为可选参数，作为event.data属性值传递给事件对象的额外数据对象

第三个参数则是用来绑定的处理函数

