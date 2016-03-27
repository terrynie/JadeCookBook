# Jade基础语法

##前点
在正式介绍语法之前，先来看一个Jade的例子，大致了解一下Jade。

新建一个hello.jade文件:<br>
hello.jade
```jade
doctype html
html
	head
		title Hello Jade
	body
		h1 Welcome To Jade Cook Book For Chinese
```
保存过后，在当前目录执行下面命令：
```
jade -P hello.jade //-P是将输出格式化
```
此时，当前目录会多出一个hello.html的文件：<br>
hello.html
```html
<!DOCTYPE html>
<html>
  <head>
    <title>Hello Jade</title>
  </head>
  <body>
    <h1>Welcome To Jade Cook Book For Chinese</h1>
  </body>
</html>
```
现在大家应该多少能看出来点什么了吧？没错，hello.html正是由我们写的hello.jade文件生成的。怎么实现的？接下来就让我们来从基础讲起。

##基础语法
对前面写的简单程序，我们从第一行开始逐行讲解。

第一行的`doctype html`是文档声明，这里声明的是HTML5文档。同样，你也可以声明成其他类型的文档，只需要替换掉html字段即可，比如声明为XML、XHTML等等。而且这一行和下班其他行还有不同，下边会具体讲解。

从第二行开始是我们HTML文件正式的内容。从这里开始，每行的第一个单词会被认为是一个HTML标签，即使你这个单词并不是HTML中的标签，Jade依然会认为它是。而且标签和后边标签中的内容之间要有一个空格符。因此在这里会将html解析生成`<html></html>`。有人会怀疑如果是这样解析的话，那在hello.html中为什么后边的内容会嵌入到`html`标签之中呢？别急，下边来讲。

根据前边讲的，每行的第一个单词会被认为是一个HTML标签，那么在这里会生成一对标签，即：`<head></head>`。那更不对了呀，在目标文件hello.html中`<html>`标签和`<head>`标签都没有在一起呀，而且中间都还嵌套的有其他内容，而且`<head>`标签就嵌套在`<html>`标签中。这是我们就要看这两行的差别了，可以看出的是在`head`处比`html`处多了一层缩进。正如Python中一样，Jade中的缩进也是嵌套关系，所以我们的目标文件才会向我们看到的那样。但是这并不意味着我们前边说的不正确，当Jade解析到第二行的`html`时，确实生成了一对`<html></html>`标签，不过当执行到第三行的时候Jade发现这里有个嵌套关系，就会通知之前生成的`<html></html>`标签说“嘿老兄，你们中间还有其他哥们呢，他们得排在你们中间了”。

光听我讲不一定是对的，那怎么验证呢？很简单，我们新建一个jade文件，只写一个标签`html`即可，执行jade命令，产看目标文件中是否是`<html></html>`即可。当然了，结果肯定是的，如果不是我岂不是没法继续装下去了，哈哈...

在第四行中，在`title`标签后是`Hello Jade`，这就是`title`的内容。

第五行的`body`标签在缩进上是和`head`同级的，所以他们在`DOM树`中应该也是同级的，所以在`<head>`同级的地方生成的`<body></body>`。


