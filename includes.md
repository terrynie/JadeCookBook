#3.2 Includes
##3.2.1 引入Jade文件
Includes是代码复用的另一种方式，允许你将一个Jade文件中的内容引入到另一个Jade文件中。

head.jade:
```jade
head
    title This is head
```
footer.jade:
```jade
footer this is a footer
```
page.jade:
```jade
html
    include ./head.jade
    body
        h1 this is a include demo
        include ./footer.jade
```
page.html:
```html
<html>
  <head>
    <title>This is head</title>
  </head>
  <body>
    <h1>this is a include demo</h1>
    <footer>this is a footer</footer>
  </body>
</html>
```
##3.2.2 引入文本文件
除了可以使用`includes`引入Jade文件，还可以使用它引入文本文件，比如CSS或JavaScript脚本文件。引入样式文件和脚本文件时，文件内容被作为纯文本引入到Jade文件中。

index.jade:
```jade
doctype html
html
  head
    style
      include style.css
  body
    h1 My Site
    p Welcome to my super lame site.
    script
      include script.js
```
style.css:
```css
h1 { color: red; }
```
script.js:
```js
console.log('You are awesome');
```
index.html:
```html
<!doctype html>
<html>
  <head>
    <style>
      h1 { color: red; }
    </style>
  </head>
  <body>
    <h1>My Site</h1>
    <p>Welcome to my super lame site.</p>
    <script>
      console.log('You are awesome');
    </script>
  </body>
</html>
```