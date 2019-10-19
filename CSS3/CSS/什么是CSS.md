### <a  id="top" href="#top">:closed_book:目录 </a>

- [x] <a href="#01">**`CSS?`**</a>
- [x] <a href="#02">**`语法`**</a>
- [x] <a href="#03">**`ID和Class选择器`**</a>


### &nbsp;&nbsp; <a id="01">CSS?</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: name

Cascading Style Sheets-层叠样式表。其用于装饰html元素,将网页变得更漂亮

---
### &nbsp;&nbsp; <a id="02">语法</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: html内的css
```html
<style>
p {
  color:red;
}
</style>
```

:star: 外部引入的css
```html
    <link rel="stylesheet" type="text/css" href="css.css">
```

:star: 内联的css

```html
<p style="color:skyblue">第一自然段<p/>
```

多重样式优先级:内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式

css注释 : \/*注释内容\*/

---
### &nbsp;&nbsp; <a id="03">ID和Class选择器</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star:  ID选择器
```html
#para1 {
    text-align:center;
    color:red;
}
```

:star: Class选择器
```html
.center {text-align:center;}
```

```html
p.center {text-align:center;}   --指定元素的类名
```
---












