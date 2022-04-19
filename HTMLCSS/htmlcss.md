## 认识网页

```html
<!-- 文档声明，告诉浏览器当前页面是HTML5页面，按HTML5标准解析 -->
<!DOCTYPE html>
<!-- <html>：根元素，一个文档只能有一个 -->
<!-- lang：帮助翻译工具要是用的翻译规则 -->
<!-- lang="en"：告诉浏览器这个HTML文档的语言是英文 -->
<html lang="en">
  <head>
    <!-- charset="UTF-8"：字符编码规则，将文字存储到计算机中，之后解析出来显示 -->
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 引入外部链接 -->
    <link rel="stylesheet" href="">
    <!-- 样式 -->
    <style>
      .hh {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1 class="hh" title="hahha">哈哈哈</h1>
  </body>
  <script>
    // alt + shift + 下箭头 复制本行至下一行
    // ctrl + enter 回到下一行
    // tab
    // tab + shift  选中的块回退
    // alt + shift 选中多个模块
  </script>
</html>
```

单标签

双标签

标签名可以大写

元素嵌套元素

## html基础元素

`<h1></h1>`：标题

`<p></p>`：段落，不建议在`<p>`标签内嵌入`<div>`

`<strong></strong>`：加粗

SEO优化

`<br>`，`<hr>`

`<code></code>`

`<pre></pre>`

`&nbsp`：空格

字符实体：现实一些特殊字符

`&gt`：大于，`&lt`：小于

`<span>`

`<img>`

像素（px）

`<a href=""></a>`

`<iframe src="" frameborder="0"></iframe>`

`<base href="">`

锚点链接

伪链接

## CSS基础

### CSS引入

内联样式

```html
<h1 style="color: red; font-size: 100px;">haah我是小当家</h1>
```

文档样式表

```html
<style>
  h1 {
  	color: yellow;
  }
</style>
<!-- -------------------- -->
<body>
  <h1>haah我是小当家</h1>
</body>
```

外部样式表：从外部引入一个css文件

```html
<link rel="stylesheet" href="../css/base.css">
<!-- -------------------- -->
<style>
  @import url("../css/base.css");
</style>
```

### CSS选择器

并集选择器

通配符

元素（标签）选择器

类选择器

id选择器

后代选择器

## 文字相关CSS属性

`text-decoration`

`text-transform`

`text-indent`：第一行缩进

`font-size`

`text-align`：最后一行不会居中

`font-family`：在本地查找

`font-weight`

`font-style`

`font-variant`

`line-height`

<img src="D:\web\note\HTMLCSS\image-20220419215154735.png" alt="image-20220419215154735" style="zoom:80%;" />

