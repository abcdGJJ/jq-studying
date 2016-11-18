# jQuery中的动画

##### show()方法和hide()方法

这两个方法作用是隐藏和显示元素

```javascript
$('element').hide() // 等价于$('element').css('display', 'none')
$('element').show()
```

这两个方法可以带参数

```javascript
$('element').show('slow') // normal、slow、fast
// 或
$('element').show(1000)
```

##### fadeIn()方法和fadeOut()方法

只改变不透明度

```javascript
$('element').fadeIn() // 渐现
$('element').fadeOut() // 渐隐
```

##### slideUp()方法和slideDown()方法

只改变元素高度

```javascript
$('element').slideUp() // 由下到上缩短
$('element').slideDown() // 由上到下延长
```

##### 自定义动画方法animate()

animate(params,  speed,  callback)

```javascript
$('element').animate({left: "500px"}, 3000)
$('element').animate({left: "+=500px"}, 3000)
// 同时执行多个动画
$('element').animate({left: "500px", height: "+=200px"}, 3000)
// 顺序执行多个动画
$('element').animate({left: "+=500px"}).animate({height: "+=300px"}, 4000)
```

##### 动画回调函数

如果想在动画结束时切换CSS样式，按照常规方式链式调用.css("", "")，会发现开始执行动画的时候css()方法就被执行了。出现这个问题的原因时：css()方法不会加入到动画队列中，而是立即执行。我们可以通过回调函数对非动画方法实现排队

```javascript
$('element').animate({left: "+=200px"}, 2000, function () {
  $(this).css("border": "1px solid blue")
})
```

##### 停止动画stop()

stop([clearQueue], [gotoEnd])

clearQueue代表是否清空未执行完的动画队列，gotoEnd代表是否直接将正在执行的动画跳转到末状态

```javascript
$('element').hover(function () {
  $(this).stop().animate({height: "+=150px", width: "+=150px"}, 2000)
}, function () {
  $(this).stop().animate({height: "-=100px", width: "-=100px"}, 1000)
})
```

结束当前正在进行的动画，并立即执行队列中的下一个动画

如果遇到组合动画：

```javascript
$('element').hover(function () {
  $(this).stop().animate({height: "150"}, 200).animate({width: "200"}, 300)
}, function () {
  $(this).stop().animate({height: "20"}, 200).animate({width: "50"}, 300)
})
```

此时一个stop()就力不从心了，因为stop()只会停止正在进行的动画，而继续执行后面的width: 200这个动画。这时可以把stop()的第一个参数设置为true，此时程序会把当前元素接下来尚未执行完的动画队列都清空

##### 判断是否处于运动状态

```javascript
if (!$('element').is(":animated")) {
  // code
}
```

##### 延迟动画

```javascript
$('element').hover(function () {
  $(this).stop().animate({height: "150"}, 200).animate({width: "200"}, 300).delay(1000).animate({top: "200px"}, 300)
})
```



