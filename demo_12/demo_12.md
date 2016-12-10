# 编写jQuery插件

jQuery提供了两个用于扩展jQuery功能的方法，即jQuery.fn.extend()方法和jQuery.extend()方法

前者把两个对象或者多个对象合并到第一个对象当中；后者把对象挂载到jQuery的prototype上以扩展一个新的jQuery实例方法

```javascript
eg:

jQuery.extend(target [, object1] [, objectN])

var obj1 = {
    name: 'Tom',
    age: 21
}
var obj2 = {
    name: 'Jerry',
    sex: 'boy'
}
$.extend(obj1, obj2);

obj1 // {name: "Jerry", age: 21, sex: "boy"}
obj2 // {name: "Jerry", sex: "boy"}

jQuery.extend(object)

jQuery.extend({
    /* 返回两个元素中较小的值 */
    min: function(a, b) {
        return a < b ? a : b;
    },
    /* 返回两个元素中较大的值 */
    max: function(a, b) {
        return a > b ? a : b;
    }
});
jQuery.min(2, 3); // 2 
jQuery.max(4, 5); // 5

jQuery.fn.extend({
    setRed: function() {
        return $(this).css("color", "red");
    }
});
$('.tip').setRed();
```

