# 属性-Attributes

我们在编写HTML文件时，肯定要给HTML标签添加属性，那使用Jade如何实现呢？

在官方文档中说“Jade标签看起来就像html标签一样，但是属性值和常规的JavaScript值。”乍一看很就懵了，但其实很简单。在Jade中，在一个标签后边紧跟上一对圆括号，在圆括号中使用表达式赋值。其中表达式的左值(要是不知道左值是什么，就百度吧...)，表达式的右值是JavaScript值，如下例：
```
a(href="google.com")
```
生成html后就是：
```
<a href="google.com"></a>
```
<br>
而且，除此之外还可以定义变量，然后使用标准的JavaScript表达式给Attributes赋值：
```
- var x = 1;
body(id=x==1?1:0)
```
编译后：
```
<body id="1"></body>
```
其中，在Jade中定义变量使用`-`开头，后边跟一个空格，之后是JavaScript声明的变量。

如果一个标签有多个属性，使用逗号分隔：
```
input(id="username",type="text",name="username")
//甚至可以分开多行来写
input(
  id="username",
  type="text",
  name="username"
) //和上边效果一样
```
