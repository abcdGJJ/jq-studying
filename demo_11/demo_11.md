# 序列化元素

##### serialize()方法

```javascript
<form id="form1">
  <input type="text" name="username" id="username">
  <input type="text" name="userage" id="userage">
</form>
$.get('get.php', $('#form1').serialize(), function (data, textStatus){})
```

##### serializeArray()方法

该方法不是返回字符串，而是将DOM元素序列化后，返回JSON格式的数据

##### param()方法

```javascript
var obj = {a:1, b:2, c:3}
var k = $.param(obj) // a=1&b=2&c=3
```



# jQuery中的Ajax全局事件

ajaxStart()：ajax请求开始时的回调函数

ajaxStop()：ajax请求结束时的回调函数

```javascript
$('#loading').ajaxStart(function () {
  $(this).show()
})
```

