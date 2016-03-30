#2.2 标签-Tag
##2.2.1 标签
默认情况下，每行的第一个单词会被认为是HTML标签(单词前只能有空格，不能有其他字符)，缩进的单词是子标签。

Jade代码：
```jade
html
	head
		title Tag Demo
	body
		p This is a Tag Demo
```
HTML代码：
```html
<html>
  <head>
    <title>Tag Demo</title>
  </head>
  <body>
    <p>This is a Tag Demo</p>
  </body>
</html>
```
##2.2.2 Block Expansion
为了省略空格，Jade为嵌套子标签提供了一种行内语法，就是在父标签后跟上`:`和空格之后再跟嵌套子标签。使用时要注意，如果想取消嵌套，只能在下一个和嵌套父标签有相同缩进的标签处退出(需要特别注意)，否则整个程序会一层一层嵌套下去(下边会举例说明)。

Jade代码：
```jade
html
	head: title Tag Demo
	body
		p This is a Tag Demo
```
HTML代码：
```html
<html>
  <head>
    <title>Tag Demo</title>
  </head>
  <body>
    <p>This is a Tag Demo</p>
  </body>
</html>
```
这个例子中我们在第二行head处嵌套了一个title，因此我们想要结束嵌套，需要有一个标签和head同级，也就是有相同缩进。但是如果像下边的Jade代码一样会怎样？
```jade
//导致意料之外的代码
html: head: title Tag Demo
	body
		p This is a Tag Demo
```
乍一看，你可能会认为这不就是html嵌套head，然后head里边嵌套title。然后body位于html下边有一层缩进，应该是html的子标签，并且就像上例那样和head同级，body里嵌套一个p标签。

我只能告诉你如果你那样想的话就全错了，先附上生成的HTML代码：
```html
<!--导致意料之外的代码-->
<html>
  <head>
    <title>Tag Demo
      <body>
        <p>This is a Tag Demo</p>
      </body>
    </title>
  </head>
</html>
```
看到这是不是整个人都疯了，结构完全和我们想的不一样。因为我们使用的是行内语法实现嵌套，Jade认为整行是一个整体，此时我们body使用了一个缩进，这时已经不是行内语法了，二是正常的缩进实现嵌套，所以就被认为是相对于整行的子标签。因此在这里Jade不认为body和head同级，而是认为body是title的子标签。

##2.2.3 自封闭标签
Jade能够识别HTML中的自封闭标签，例如`img`、`input`、`meta`等等。

jade:
```jade
img(src="/img.png")
meta(charset="utf-8")
```
HTML：
```html
<img src="/img.png"/>
<meta charset="utf-8"/>
```
##2.2.4自定义自封闭标签
除了HTML中的自封闭标签外，我们还可以自定义自封闭标签，而且方法也是十二分地简单--只需要在标签后加上`/`即可：

jade:
```jade
customized/
customized(id="customized")/
```
HTML:
```html
<customized/>
<customized id="customized"/>
```


