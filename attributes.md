#2.3 属性-Attributes
##2.3.1 基本属性

我们在编写HTML文件时，肯定要给HTML标签添加属性，那使用Jade如何实现呢？

在官方文档中说“Jade标签看起来就像html标签一样，但是属性值和常规的JavaScript值。”乍一看很就懵了，但其实很简单。在Jade中，在一个标签后边紧跟上一对圆括号，在圆括号中使用表达式赋值。其中表达式的左值(要是不知道左值是什么，就百度吧...)，表达式的右值是JavaScript值，如下例：
```jade
a(href="google.com")
```
生成html后就是：
```html
<a href="google.com"></a>
```
<br>
而且，除此之外还可以定义变量，然后使用标准的JavaScript表达式给Attributes赋值：
```jade
- var x = 1;
body(id=x==1?1:0)
```
编译后：
```html
<body id="1"></body>
```
其中，在Jade中定义变量使用`-`开头，后边跟一个空格，之后是JavaScript声明的变量。

如果一个标签有多个属性，使用逗号分隔：
```jade
input(id="username",type="text",name="username")
//甚至可以分开多行来写
input(
  id="username",
  type="text",
  name="username"
) //和上边效果一样
```
##2.3.2 非转义属性
为了阻止跨站脚本，在默认情况下所有的属性都会被转义，但是如果你真的需要一些特殊字符，比如：“<”或“>”等，可以使用`!=`替代`=`。
```jade
div(escaped="<code>")
div(unescaped!="<code>")
```
对应会生成HTML代码：
```html
<div escaped="&lt;code&gt;"></div>
<div escaped="<code>"></div>
```
##2.3.3 布尔属性
Jade可以直接接受`true`和`false`赋值给布尔属性，而且当你缺省赋值时，默认为`true`。
```jade
input(type="checkbox",checked)
input(type="checkbox",checked="true")
input(type="checkbox",checked="false")
```
对应HTML代码：
```html
<input type="checkbox" checked>
<input type="checkbox" checked>
<input type="checkbox">
```
##2.3.4 样式属性
在之前的属性中每个属性只有一个值，但在style属性中会有多个值，比如：`<p style="color:red;font-size:17px;"></p>`，这个该怎么办呢？<br>其实很简单，既然Jade支持JavaScript语法赋值，那我们是不是可以把style属性的值看做是一个JavaScript对象呢(也可以称为字典)？答案是：当然可以喽！
```jade
p(style={color:red,font-size:17px})
```
HTML代码对应为：
```html
<p style="color:red;font-size:17px;"></p>
```
##2.3.5 字面量声明class属性和id属性
当使用字面量声明class和id属性时，Jade支持使用CSS的类选择器和id选择器的方式，这也是最简单的方法。
```jade
a.commit
a#commit
```
对应的HTML为：
```html
<a class="commit">
<a id="commit">
```
而且这种方法还可以声明分类：
```jade
a.commit.first
```
```html
<a class="commit first"></a>
```
而且对于分类，Jade还有另一种声明方法，就是把分类拆分成数组，然后直接使用数组对class属性赋值：
```jade
- var classes = ['commit','first'];
a(class=classes)
```
生成HTML代码后和字面量赋值效果相同：
```html
<a class="commit first"></a>
```

##2.3.6 &Attributes
Jade提供`&attributes`是为了方便我们将整个对象传递给属性，主要用于为属性整体赋值和将属性穿个Mixin(详见：3.5.3)。

attributes.jade:
```jade
- var attributes = {'data-foo': 'bar'};
div#foo(data-bar="foo")&attributes(attributes)
```
attributes.html:
```html
<div id="foo" data-bar="foo" data-foo="bar"></div>
```