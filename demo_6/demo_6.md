# JQuery中的事件

#####  加载DOM

在常规的JS中，页面加载完毕后给DOM添加事件通常采用window.onload方法，而在JQuery中，使用的是$(document).ready()方法。它们的区别如下：

JS方法是在网页中所有的元素（包括所有的关联文件）完全加载到浏览器后才执行。而JQ方法注册的事件处理程序在DOM就绪时就可以被调用，并不意味这些元素关联的文件都以下载完毕

JQ中另一个关于页面加载的方法load()方法。如果绑定在window对象上，则会在所有内容加载完毕后触发，如果绑定在元素上，则会在元素加载完毕后触发

```javascript
$(window).load(function () {})
//等价于
window.onload = function () {}
```

##### 事件绑定

```javascript
bind(type [, data], fn)
```

type包括：blur、focus、load、resize...等事件

第二个为可选参数，作为event.data属性值传递给事件对象的额外数据对象

第三个参数则是用来绑定的处理函数

注：bind用法在之后的jQuery版本被取消，替换成on

##### 合成事件

```javascript
hover(enter, leave)
// 模拟鼠标悬停事件，移动到元素上会触发第一个函数
toggle(fn1, fn2, ...fnN)
// $('').toggle(function(){},function(){})
```

##### 事件冒泡

由事件元素向外层冒泡

停止事件冒泡：

```javascript
$('').bind('click', function(e) {
  e.stopProgation()
})
```

阻止默认行为：

```javascript
e.preventDefault()
```

##### 事件捕获

由外向事件元素冒泡

##### 事件对象属性

event.type

```javascript
$('a').click(function (event) {
  alert(event.type)
  return flase // 阻止链接跳转
})
```

event.target

```javascript
$("a[href='http://www.baidu.com']").click(function (event) {
  var tg = event.target
  alert(tg.href)
  return flase // 阻止链接跳转
})
```

event.pageX和event.pageY

获取光标x和y坐标

##### 移除事件

```javascript
$(function () {
  $('#btn').bind('click', function () {
    $('#test').append('<p>我的绑定函数1</p>')
  }).bind('click', function () {
    $('#test').append('<p>我的绑定函数2</p>')
  })
  $('deleteAll').bind('click', function() {
    $('#btn').unbind('click')
  })
})
```

##### 触发后接触绑定

```javascript
$(function () {
  $('#btn').one('click', function () {
    $('#test').append('<p>我的绑定函数1</p>')
  })
})
```

##### 模拟操作

常用模拟

```javascript
$('#btn').trigger('click')
// 或
$('#btn').click()
```

触发自定义事件

```javascript
$（'#btn').bind('myClick', function () {
  $('#test').append('<p>我的自定义事件</p>')
})
$('#btn').trigger('myClick')
```

##### 事件命名空间

引入：

看下面的代码

```javascript
$('#element').on('click',doSomething)
		     .on('click', doSomethingElse)
// 解绑
$('#element').off('click', doSomething)
```

如果执行的是匿名函数该如何解绑呢？

```javascript
$('#element').on('click',function () {
  console.log('doSomething')
})
```

事件命名空间

```javascript
$('#element').on('click.myNamespace',function () {
  console.log('doSomething')
})
$('#element').off('click.myNamespace')
```