#2.4 插入
在Jade中，提供了集中插入变量的操作符，可以让你根据自己的需要进行选择。
##2.4.1 转义字符串插入
这种插入方式会将特殊字符串进行转移，在遇到类似于'<'、'>'以及'&copy;'等特殊字符时会进行转义。

Jade:
```jade
- var title = "On Dogs: Man's Best Friend";
- var author = "enlore";
- var theGreat = "<span>escape!</span>";

h1= title
p Written with love by #{author}
p This will be safe: #{theGreat}
```
HTML:
```html
<h1>On Dogs: Man's Best Friend</h1>
<p>Written with love by author</p>
<p>This will be safe: &lt;span&gt;escape!&lt;/span&gt;</p>
```
在插入变量时，如果是直接赋值的话和JavaScript相同，但是如果你想把变量和字符串拼接，就需要用到`#{}`
操作符了，就像上例中的`#{author}`和`#{theGreat}`就是这样。

而且在`#{}`中不仅可以插入变量，其实还可以插入JavaScript代码：

Jade：
```jade
- var msg = "hello world"
p message is #{msg.toUpperCase()}
```
HTML:
```html
<p>message is HELLO WORLD</p>
```
##2.4.2 非转义字符串插入
非转义字符串插入和转义字符串插入用法一样，只是使用的是`!{}`，而且在遇到特殊字符是不对其进行转义：
Jade:
```jade
- var title = "On Dogs: Man's Best Friend";
- var author = "enlore";
- var theGreat = "<span>escape!</span>";

h1= title
p Written with love by !{author}
p This will be safe: !{theGreat}
```
HTML:
```html
<h1>On Dogs: Man's Best Friend</h1>
<p>Written with love by enlore</p>
<p>This will be safe: <span>escape!</span></p>
```
##2.4.3 标签插入
标签插入使用的操作符是`#[]`，在操作符中使用Jade标签声明代码即可。

Jade：
```jade
p this is a link #[a(href="http://jade.terrynie.com")]
```
HTML:
```html
<p>this is a link <a href="http://jade.terrynie.com"></a></p>
```



