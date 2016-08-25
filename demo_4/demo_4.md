# 笔记



## 基本选择器

|            选择器            |         描述         |  返回  |       示例        |
| :-----------------------: | :----------------: | :--: | :-------------: |
|           \#id            |    根据给定的ID匹配元素     | 单个元素 |   $("#test")    |
|          .class           |    根据class匹配元素     | 集合元素 |   $(".test")    |
|          element          |     根据给定的元素名匹配     | 集合元素 |     $("p")      |
|             *             |        所有元素        | 集合元素 |     $("*")      |
| selector1, selector2, ... | 将每一个选择器匹配到的元素合并后返回 | 集合元素 | $("div,span,p") |



## 层次选择器

|           选择器            |                描述                 |  返回  |       示例        |
| :----------------------: | :-------------------------------: | :--: | :-------------: |
| $("ancestor descendant") | 选取ancestor元素里的所有descentdant（后代）元素 | 集合元素 |  $("div span")  |
|   $("parent > child")    |      选取parent下面的child元素（子元素）      | 集合元素 | $("div > span") |
|     $("prev + next")     |      选取紧接在prev元素后的next元素（同辈）      | 集合元素 | $(".one + div") |
|    $("prev~siblings")    |    选取prev元素之后的所有siblings元素（同辈）    | 集合元素 | $("#two ~ div") |



可以用`next()`方法来代替$("prev + next")选择器；

可以用`nextAll()`方法来代替$("prev ~ siblings")

|      |       选择器        |            方法             |
| :--: | :--------------: | :-----------------------: |
| 等价关系 | $(".one + div")  |   $(".one").next("div")   |
| 等价关系 | $("#prev ~ div") | $("#prev").nextAll("div") |



## 过滤选择器

1. 基本过滤选择器

   |      选择器       |           描述           |  返回  |                 示例                  |
   | :------------: | :--------------------: | :--: | :---------------------------------: |
   |     :first     |        选取第一个元素         | 单个元素 |   $("div : first")选取div中的第一个div元素   |
   |     :last      |        选取最后一个元素        | 单个元素 |           $("div : last")           |
   | :not(selector) |    去除所有与给定选择器匹配的元素     | 集合元素 |      $("input:not(.myclass)")       |
   |     :even      |     选取索引是偶数元素，从0开始     | 集合元素 |           $("input:even")           |
   |      :odd      |       选取索引是奇数的元素       | 集合元素 |           $("input:odd")            |
   |   :eq(index)   |     选取索引等于index的元素     | 单个元素 | $("input:eq(1)")选取索引等于1的\<input\>元素 |
   |   :gt(index)   |     选取索引大于index的元素     | 集合元素 |           $("input:gt()")           |
   |   :lt(index)   |     选取索引小于index的元素     | 集合元素 |          $("input:lt(1)")           |
   |    :header     | 所有的标题元素，如\<h1\>、\<h2\> | 集合元素 | $(":header")选取所有的\<h1\>、\<h2\>...元素 |
   |   :animated    |      选取正在执行动画的元素       | 集合元素 |          $("div:animated")          |
   |     :focus     |      选取当前获得焦点的元素       | 集合元素 |             $(":focus")             |

2. 内容过滤选择器

   |       选择器       |         描述         |  返回  |                    示例                    |
   | :-------------: | :----------------: | :--: | :--------------------------------------: |
   | :contains(text) | 选取含有文本内容为“text”的元素 | 集合元素 |          $("div:contians('我')")          |
   |     :empty      |  选取不包含子元素或者文本的空元素  | 集合元素 | $("div:empty")选取不包含子元素（包括文本元素）的\<div\>空元素 |
   | :has(selector)  |  选取含有选择器所匹配的元素的元素  | 集合元素 |   $("div:has(p)")选取包含\<p\>元素的\<div\>元素   |
   |     :parent     |   选取含有子元素或者文本的元素   | 集合元素 | $("div:parent")选取拥有子元素（包括文本元素）的\<div\>元素 |

3. 可见性过滤选择器


|   选择器    |    描述     |  返回  |                    示例                    |
| :------: | :-------: | :--: | :--------------------------------------: |
| :hidden  | 选取所有不可见元素 | 集合元素 | $(:hidden)，包括\<input type="hidden"\>，\<div style="display:none;"\>和\<div style="visibility:hidden;"\>等元素 |
| :visible | 选取所有可见元素  | 集合元素 |             $("div:visible")             |

 4.属性过滤选择器

|            选择器             |                   描述                   |  返回  |                    示例                    |
| :------------------------: | :------------------------------------: | :--: | :--------------------------------------: |
|        [attribute]         |               选取拥有此元素的元素               | 集合元素 |         $("div[id]")选取拥有属性id的元素          |
|     [attribute=value]      |             选取属性值为value的元素             | 集合元素 |           $("div[title=test]")           |
|     [attribute!=value]     |                                        |      |          $("div[title!=test]")           |
|     [attribute^=value]     |            选取属性值以value开头的元素            |      | \$("a[href^=#]")选取所有以#开头的链接。$("div[title^=test]")选取属性title以test开始的div元素。 |
|     [attribute$=value]     |            选取属性值以value结束的元素            | 集合元素 |          $("div[title\$=test]")          |
|     [attribute*=value]     |            选取属性值含有value的元素             |      | $("div[title*=test]")选取属性title含有test的div元素 |
|    [attribute\|=value]     | 选取属性等于给定字符串或以该字符串为前缀（该字符串后面跟一个连字符-）的元素 |      |          $('div[title\|="en]')           |
|     [attribute~=value]     |         选取属性用空格分隔的值中包含一个给定值的元素         |      |         $('div[title~="test"]')          |
| [attribute1]\[attribute2\] |                  复合选取                  |      |       \$("div\[id][title$=title]")       |
