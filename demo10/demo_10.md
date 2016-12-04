# jQuery与Ajax的应用

Ajax全称为"Asynchronous JavaScript and XML"（异步JavaScript和XML）

##### load()方法

```javascript
$.load(url [, data] [,callback])

eg:
$('XX').load('test.html') // 将test页面的内容加载并插入元素中
$('XX').load('test.html .a') // 将内容插入到class=a的元素中
$('XX').load('test.php', {name: 'rain', age: '22'}, function(resText, textStatus, XMLHttprequest) {
  // code
  // responseText: 请求返回内容
  // textStatus: 请求状态：success、error、notmodified、timeout 4种
  // XMLHttpRequest: XMLHttpRequest对象
})
```

##### get()方法

```javascript
$.get(url [, data] [,callback] [,type])

eg:
$.get('get.php', {
  user: $('#user').val()
  content: $('#con').val()
}, function (data, textStatus) {
  var user = data.user
  var con = data.con
  var html = '<div>' + user + con + </div>'
  $('text').html(html)
}, 'json')
```

##### post()方法

与get方法差不多，区别如下：

- GET请求会将参数跟在URL后进行传递，POST请求是作为HTTP消息的实体内容
- GET请求对传输数据大小有限制（2KB），POST方式传递的数据量更大
- GET方法请求的数据会被浏览器缓存起来，其他人可以从历史纪录中读取到

##### getScript()方法：加载JS文件

```javascript
$.getScript('test.js', function () {
  // code
})
```

##### getJSON()方法：与上一方法相同

```javascript
$.getJSON('test.json', function (data) {
  // data：返回的数据
})
```

##### $.each()方法

不同于selector.each()，用于遍历对象和数组

```javascript
// json
// {"comments":[{"content":"很不错嘛","id":1,"nickname":"纳尼"},{"content":"哟西哟西","id":2,"nickname":"小强"}]}
$.getJSON('test.json', function (data) {
  var html = ''
  $.each(data.comments, function (index, item) {
    $('#info').append('<div>'+item.id + item.nickname + nick.content'</div>'')
  })
})
```



