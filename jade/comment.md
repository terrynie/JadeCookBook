#2.1 注释
##2.1.1 单行注释
Jade中的单行注释和JavaScript一样，使用双斜线`//`注释：

Jade代码：
```jade
//first comment
p first comment
```
HTML代码：
```html
<!--first comment-->
<p>first comment</p>
```

##2.1.2 块注释
块注释的写法是在`//`后换行并缩进，之后的多行注释内容保持缩进即可，当不需要注释时取消缩进：

Jade代码：
```jade
//
  first line comment
  second line comment
p first comment
```
HTML代码：
```html
<!--
first line comment
second line comment
-->
<p>first comment</p>
```
#2.1.3 条件注释

在做浏览器适配时，经常要使用条件注释判断浏览器版本是否是IE某个版本以下(无意黑IE，事实如此)。然而Jade中并没有特殊的语法用于条件注释，所以只能使用HTML语句来进行条件注释。恰好在Jade中行首如果以`<`开头的话，本行内容会被看做普通文本，所以用HTML的条件注释也刚刚好。

Jade代码：
```jade
<!--[if IE 8]>
html(lang="en" class="lt-ie9")
<![endif]-->
<!--[if gt IE 8]><!-->
html(lang="en")
<!--<![endif]-->
```
HTML代码
```html
<!--[if IE 8]>
<html lang="en" class="lt-ie9"></html>
<![endif]-->
<!--[if gt IE 8]><!-->
<html lang="en"></html>
<!--<![endif]-->
```


