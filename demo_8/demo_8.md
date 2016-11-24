# 表单操作

##### focus方法

```javascript
$(':input').focus(function () {
  // code
})
```

全选 / 全不选 / 反选

```javascript
// 注意：不能用attr获取
$('#checkAll').click(function () {
  $('[name = items]:checkbox').prop('checked', true)
})
$('#checkNo').click(function () {
  $('[name = items]:checkbox').prop('checked', false)
})
$('#checkRev').click(function () {
  $('[name = items]:checkbox').each(function () {
    $(this).prop('checked', !$(this).prop('checked'))
    //或 this.checked = !this.checked
  })
})
```

