#3.1 Block
在Jade中，允许使用block结合extends关键字预定义一个模板供其他模板调用。调用时，如果父模板中定义了某块内容，而子模板中没有定义时，默认显示父模板中的内容。Jade通过这种方法实现模板的继承和重用。

除了继承模板，还可以使用append和prepend对继承的模板进行扩展。
##3.1.1 模板继承
在Jade中，block的内容是可选的，如果需要也可以指定默认内容。

block声明方式：
```jade
block blockName
  content
```
layout.jade
```jade
- var title = 'blog'
html
  head
    title My Site - #{title}
    block scripts
      script(src='/jquery.js')
  body
    block content
```
page.jade
```jade
extends ./layout.jade

block scripts
  script(src='/bootstrap.js')
```
page.html
```html
<html>
  <head>
    <title>My Site - blog</title>
    <script src="/bootstrap.js"></script>
  </head>
  <body>
    <h1>title</h1>
  </body>
</html>
```
在上例中，在layout.jade中声明了两个block，其中block scripts制定了默认内容，而block content没有指定默认内容。在page.jade中使用extends继承了layout.jade，并且默认覆盖了layout.jade中的block scripts，但是没有指定block content的内容，所以block content中还是layout.jade中的内容。

##3.1.2 Block Append
在2.2.1节中说过默认情况下子模板重写父模板中的block是直接覆盖，但是我们有时候需要的不是完全覆盖，二是添加新内容。那么我们就需要用到append和prepend。

append是在父模板中block内容后边追加内容：
page2.jade
```jade
extends ./layout.jade

block append scripts
  script(src='/bootstrap.js')
```
page2.html
```html
<html>
  <head>
    <title>My Site - blog</title>
    <script src="/jquery.js"></script>
    <script src="/bootstrap.js"></script>
  </head>
  <body>
  </body>
</html>
```
很显然，在父模板中block scripts的内容是`<script src="/jquery.js"></script>`，然后我们在page2.jade中使用block append

