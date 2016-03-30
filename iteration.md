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
