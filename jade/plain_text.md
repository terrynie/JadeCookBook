#2.5 Plain Text
Jade提供三种常用的方法获取文本，这三种方式适合不同的情况。
##2.5.1 管道文本
第一种方法是使用管道符`|`，也就是键盘`Enter`键上方的按键。管道符出现在每行第一个非空格字符时，改行就会被认为是文本。

Jade:
```jade
| Plain text can include <strong>html</strong>
p
  | It must always be on its own line
```
HTML:
```html
Plain text can include <strong>html</strong>
<p>It must always be on its own line</p>
```
##2.5.2 标签行内文本
这是我们用的最多的一种方式，只需要将文本放在标签之后，并用空格与标签隔开即可。

Jade:
```jade
p this is a inline text in a tag
```
HTML:
```html
<p>this is a inline text in a tag</p>
```

##2.5.3 标签块文本
有时候你可能会希望在一个标签中使用大量文本，就比如我们希望在`script`或`style`标签内包含大量的脚本代码或样式代码。为了达到这样的效果我们可以使用`.`符号来达到目的，只需要将`.`符号紧跟在标签后即可(不能有空格)。

Jade:
```jade
script.
  if (usingJade)
    console.log('you are awesome')
  else
    console.log('use jade')
```
HTML:
```html
<script>
  if (usingJade)
    console.log('you are awesome')
  else
    console.log('use jade')
</script>
```
