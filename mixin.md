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
在mixin中还可以包含block，而且可以和参数同时存在。调用包含block的mixin时传入block的方法就是在mixin调用行下缩进即可，当结束block时只需结束当前缩进即可。

mixinBlock.jade:
```jade
mixin addTitle(title)
  h1= title
  if block
    block
  else
    p no block
+addTitle('Hello world')
+addTitle('Hello world')
  p this is a block
```
mixinBlock.html:
```html
<h1>Hello world</h1>
<p>no block</p>
<h1>Hello world</h1>
<p>this is a block</p>
```
详细过程来说就是，当第一次调用时我们只传入了参数title，而并没有传入block，所以第一次调用生成的HTML是前两行。当第二次调用时，我们除了传入了参数title外，还在下边传入了一个blcok。

##3.5.3 Mixin Attributes
mixin可以获取一个隐式的atrributes，可以通过这个隐式的attributes对象向mixin中传入属性，并且可以在Mixin中通过attributes过去其属性。

attributes.jade:
```jade
mixin addTitle(title)
	title(class=attributes.class)= title
+addTitle("Demo")(class="test")
```
attributes.html:
```html
<title class="test">Demo</title>
```
这个例子就是给mixin传入了一个class属性为"test"的隐式的attributes，并且在mixin中通过隐式的attributes获取到了这个属性。

而且，我们还可以使用`&attributes`来直接将attributes对象传给mixin，而且事实上`&attributes`在处理这件事情上也是最擅长的。

attributes2.jade:
```jade
mixin p(text)
  p&attributes(attributes)!= text
+p("this is &attributes demo")(id="demo")
```
attributes2.html
```html
<p id="demo">this is &attributes demo</p>
```


##3.5.4 Rest Arguments
我们在重用代码时可能会遇到一些问题，比如我们两种标签都有好多个重复的，但是这两种标签数量又不一定一样，而且还可以重用一段代码来生成模板，那么此时我们就可以使用Rest Arguments来达到数量不确定的目的。

rest.jade:
```jade
mixin list(id, items)
  ul(id=id)
    each item in items
      li= item

+list('first', [1, 2, 3, 4])
+list('second',['a', 'b', 'c', 'd', 'e'])
```
rest.html:
```html
<ul id="first">
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
</ul>
<ul id="second">
  <li>a</li>
  <li>b</li>
  <li>c</li>
  <li>d</li>
  <li>e</li>
</ul>
```
