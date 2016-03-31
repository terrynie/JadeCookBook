#3.5 Mixin
在Jade中，除了前面讲的两种代码反复用方式：`extends`和`includes`之外，还有一个更加强大且常用的方式，那就是本节要讲的`Mixin`。`Mixin`更像一个函数，可以是无参的，也可以是有参的，定义之后只需要在希望使用它的地方调用即可，方便得很。
##3.5.1 Mixin声明及调用
声明一个`Mixin`很简单，形式类似于声明一个函数，调用时也只需要使用`+`号后紧跟mixin名称即可，如果有参数的话需要在mixin名称之后紧跟括号，并在括号中传入参数。

mixin.jade:
```jade
mixin list
  ul
    li foo
    li bar
    li baz
+list
```
mixin.html:
```html
<ul>
  <li>foo</li>
  <li>bar</li>
  <li>baz</li>
</ul>
```
这个例子就是定义了一个无参的名称为list的mixin，然后调用了一次。如果需要多次调用，只需要多次使用`+list`即可。

下边在列举一个含参的mixin。

mixin.jade
```
mixin student(name)
  h1 #{name}
+student("terry")
```
mixin.html
```html
<h1>terry</h1>
```
注意：在调用传入参数时，除了可以使用`#{}`外，还可以直接使用`=`调用，但是左值必须和等号相连，中间不能有任何空格：
```
mixin student(name)
  h1= name
+student("terry")
```
也就是这样写。这样写效果和使用`#{}`效果相同。

##3.5.2 Mixin Blocks
