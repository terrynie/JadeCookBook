#3.3 Filters
过滤器允许你在Jade模板中使用其他语言，然后Jade自动调用所需的解释器进行转换。所使用的符号就是`:`并在分号后加上使用的语言名称，目前支持的过滤器有以下几种：

| :sass | 需要安装sass.js |
| -- | -- |
| :less | less.js |
| :markdown | 需要安装markdow-js或node-discount |
| :cdata | - |
| :coffeescript | 需要安装coffee-script |

filter.jade:
```jade
:markdown
  # Markdown

  I often like including markdown documents.
script
  :coffee-script
    console.log 'This is coffee script'
```
filter.html:
```html
<h1>Markdown</h1>
<p>I often like including markdown documents.</p>
<script>console.log('This is coffee script')</script>
```