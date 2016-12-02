# 表格应用

常用的表单选择器：

```javascript
$(':input')
$('[name = XXX]:checkbox')
$('option:selected')
```

tab切换核心代码：

```javascript
$(this).addClass('selected').siblings().removeClass('selected')
```

