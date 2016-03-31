#3.4 Iteration
在Jade中和JavaScript一样可以使用迭代器，在官方文档中说Jade支持两种主要的迭代器：`each`和`while`，另外还有一个`for`，用法和`each`相同。

##3.4.1 each
通过each迭代器可以快速迭代数组和对象，并且可以获取数组的索引和对象的键：

each.jade:
```jade
ul
  each val in [1, 2, 3, 4, 5]
    li= val
```
each.html:
```html
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
  <li>4</li>
  <li>5</li>
</ul>
```
上面的例子只是简单的迭代获取数组中的内容，下面的这个例子将同时获取数组的索引和对应的内容：

each2.jade:
```jade
ul
  each val, index in ['zero', 'one', 'two']
    li= index + ': ' + val
```
each2.html:
```html
<ul>
  <li>0: zero</li>
  <li>1: one</li>
  <li>2: two</li>
</ul>
```
在免费送一个同时获取对象中键和值得例子吧：

each3.jade:
```jade
ul
  each val, index in {1:'one',2:'two',3:'three'}
    li= index + ': ' + val
```
each3.html:
```html
<ul>
  <li>1: one</li>
  <li>2: two</li>
  <li>3: three</li>
</ul>
```
同样，上边的几个例子中的`each`完全可以可以使用`for`来替换，`for`可以被作为`each`的别名来使用。

##3.4.2 while
除了使用`each`之外还有就是可以使用`while`来循环，用法也很简单。

while.jade:
```jade
- var n = 0
ul
  while n < 4
    li= n++
```
while.html:
```html
<ul>
  <li>0</li>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>
```
这就是while的用法，和其他语言的使用方法几乎都是一样的。