### <a  id="top" href="#top">:closed_book:目录 </a>



- [x] <a href="#01">**`各种属性`**</a>
- [x] <a href="#02">**`边距`**</a>
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

1. 边框,值得注意的是th,和td有单独的边框
```css
table,th,td
{
	border:1px solid black;
}
```
2 折叠边框
```css
table
{
    border-collapse:collapse;
}
table,th, td
{
    border: 1px solid black;
}
```
3.表格宽度，行高
```css
table 
{
    width:100%;
}
th
{
    height:50px;
}
```

4. 表格文字对齐
```css
text-align属性设置水平对齐方式，向左，右，或中心：
td
{
    text-align:right;
}

垂直对齐属性设置垂直对齐，比如顶部，底部或中间：
td
{
    height:50px;
    vertical-align:bottom;
}

```

5. 表格内边距
```css
td
{
    padding:15px;
}
```

6. 表格颜色
```css
table, td, th
{
    border:1px solid green;
}
th
{
    background-color:green;
    color:white;
}
```



---
### &nbsp;&nbsp; <a id="02">边距</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 盒子模型
所有HTML元素可以看作盒子，在CSS中，"box model"这一术语是用来设计和布局时使用。   
CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。

下面是模型说明
![div1]()

- Margin(外边距) - 清除边框外的区域，外边距是透明的。
- Border(边框) - 围绕在内边距和内容外的边框。
- Padding(内边距) - 清除内容周围的区域，内边距是透明的。
- Content(内容) - 盒子的内容，显示文本和图像。

```css
--边框也可以设置颜色
div {
    width: 300px;
    border: 25px solid green;
    padding: 25px;
    margin: 25px;
}
```

:star:边框

1. border-style:
- dotted: 定义一个点线边框
- dashed: 定义一个虚线边框
- solid: 定义实线边框
- double: 定义两个边框。 两个边框的宽度和 border-width 的值相同
- groove: 定义3D沟槽边框。效果取决于边框的颜色值
- ridge: 定义3D脊边框。效果取决于边框的颜色值
- inset:定义一个3D的嵌入边框。效果取决于边框的颜色值
- outset: 定义一个3D突出边框。 效果取决于边框的颜色值

2. border-width
```css
p.one
{
    border-style:solid;
    border-width:5px;
}
```

3. border-color
```css
p.one
{
    border-style:solid;
    border-color:red;
}
```

4. border-'position'
```css
--单独设置边框各边
p
{
    border-top-style:dotted;
    border-right-style:solid;
    border-bottom-style:dotted;
    border-left-style:solid;
}

如果写4个样式:依次顺序为:上、右、下、左
写3个样式:上、左右、下
写2个样式:上下，左右
其他可以分开写的参照此顺序
```

5. 简写规则:
```css
border-width
border-style (required)
border-color


border:5px solid red;
```


:star:outline(轮廓)  [轮廓](https://www.runoob.com/css/css-outline.html)

轮廓（outline）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。   
轮廓（outline）属性指定元素轮廓的样式、颜色和宽度。

1. 在元素周围画线
```css
p 
{
	border:1px solid red;
	outline:green dotted thick;
}
```


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











