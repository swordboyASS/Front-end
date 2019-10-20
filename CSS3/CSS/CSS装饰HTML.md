### <a  id="top" href="#top">:closed_book:目录 </a>



- [x] <a href="#01">**`各种属性`**</a>
- [x] <a href="#02">**``**</a>
- [x] <a href="#03">**``**</a>
- [x] <a href="#04">**``**</a>
- [x] <a href="#05">**``**</a>
- [x] <a href="#06">**``**</a>
- [x] <a href="#07">**``**</a>
- [x] <a href="#08">**``**</a>

### &nbsp;&nbsp; <a id="01">各种属性</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star:background

- background-color:`body {background-color:#b0c4de;}`
- background-image:`body {background-image:url('paper.gif');}`
- background-repeat:
```html
--默认情况下 background-image 属性会在页面的水平或者垂直方向平铺。
body
{
background-image:url('gradient2.png');
background-repeat:repeat-x;     --设置背景图像水平平铺
background-repeat:no-repeat;   --设置图片不平铺
}
```

- background-attachment

|||
|:--|:--|
scroll	|背景图片随着页面的滚动而滚动，这是默认的。
fixed	|背景图片不会随着页面的滚动而滚动。
local	|背景图片会随着元素内容的滚动而滚动。
initial	|设置该属性的默认值。 
inherit	|指定 background-attachment 的设置应该从父元素继承。 

- background-position  :`background-position:right top;  --设置图像位置`

简写规则:

:star:文本

1. color :`h1 {color:#00ff00;}`
2. text-align(文本对齐方式):center、right、justify
3. text-decoration(文本修饰):none、overline、line-through、underline
3. text-transform(文本转换，如大小写转换):uppercase、lowercase、capitalize
4. text-indent（文本缩进）:  `p {text-indent:50px;}`
5. 字符间隔:`h1 {letter-spacing:2px;}`
6. 行间距:`p {line-height:170%;}`
7. 单词间隔:`word-spacing:30px;`
8. 禁止文字环绕:`	white-space:nowrap;`
9. 垂直对齐图像:
```css
img.top {vertical-align:text-top;}
img.bottom {vertical-align:text-bottom;}
```
10.简写规则: 

:star: 字体

1. font-family 属性设置文本的字体系列。font-family 属性应该设置几个字体名称作为一种"后备"机制，如果浏览器不支持第一种字体，他将尝试下一种字体。
2. font-style(字体样式): normal、italic(斜体)、oblique（倾斜文字）
3. font-size(字体大小):`h1 {font-size:40px;}`
```css
em代替像素设置字体大小
为了避免Internet Explorer 中无法调整文本的问题，许多开发者使用 em 单位代替像素。
em的尺寸单位由W3C建议。
1em和当前字体大小相等。在浏览器中默认的文字大小是16px。
因此，1em的默认大小是16px。可以通过下面这个公式将像素转换为em：px/16=em

h1 {font-size:2.5em;} /* 40px/16=2.5em */
h2 {font-size:1.875em;} /* 30px/16=1.875em */
p {font-size:0.875em;} /* 14px/16=0.875em */


--对于body使用百分比，浏览器默认100%
body {font-size:100%;}
```

4. font-weight（字体是否加粗）:normal、lighter、bold、900


5. 简写规则:



:star: 链接

链接的四种状态: 且必须遵循如下的顺序
1. a:link - 正常，未访问过的链接
2. a:visited - 用户已访问过的链接
3. a:hover - 当用户鼠标放在链接上时
4. a:active - 链接被点击的那一刻

```html
text-decoration:none; --去掉链接下划线
```

:star: 列表

1. 列表起始就不适用css额外写了，直接写在行间
2. 列表标记的图像：` ul{list-style-image: url('sqpurple.gif');}`
3. ...
4. 简写规则: list-style-type,list-style-position,list-style-image


:star:表格

---
### &nbsp;&nbsp; <a id="02"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 

---
### &nbsp;&nbsp; <a id="03"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 

---
### &nbsp;&nbsp; <a id="04"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 

---
### &nbsp;&nbsp; <a id="05"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 

---
### &nbsp;&nbsp; <a id="06"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 

---
### &nbsp;&nbsp; <a id="07"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star:

### &nbsp;&nbsp; <a id="08"></a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star:

---











