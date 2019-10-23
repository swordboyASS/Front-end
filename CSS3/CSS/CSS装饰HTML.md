### <a  id="top" href="#top">:closed_book:目录 </a>



- [x] <a href="#01">**`各种属性`**</a>
- [x] <a href="#02">**`边距`**</a>
- [x] <a href="#03">**`分组和嵌套选择器`**</a>
- [x] <a href="#04">**`定位`**</a>
- [x] <a href="#05">**`组合选择符`**</a>


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
![div1](https://github.com/swordboyASS/Front-end/blob/master/CSS3/CSS/Picture/div1.png)

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

![div2](https://github.com/swordboyASS/Front-end/blob/master/CSS3/CSS/Picture/div2.png)

```css
p 
{
	border:1px solid red;
	outline:green dotted thick;
}
```

:star: margin(外边距)    
margin 清除周围的（外边框）元素区域。margin 没有背景颜色，是完全透明的。
margin 可以单独改变元素的上，下，左，右边距，也可以一次改变所有的属性。

可能的值

|值|说明|
|:--|:--|
|auto|结果依赖于浏览器|
|length|定义一个固定的margin（使用像素，pt，em、cm等）|
|%|定义一个使用百分比的边距|

:star: padding(填充)

|||
|:--|:--|
|length|定义一个固定的填充(像素, pt, em,等)|
|%|使用百分比值定义一个填充|


---
### &nbsp;&nbsp; <a id="03">分组和嵌套选择器</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 分组选择器
```css
h1,h2,p
{
    color:green;
}
```



:star:嵌套选择器

在下面的例子设置了三个样式：
-  p{ }: 为所有 p 元素指定一个样式。
- .marked{ }: 为所有 class="marked" 的元素指定一个样式。
- .marked p{ }: 为所有 class="marked" 元素内的 p 元素指定一个样式。
- p.marked{ }: 为所有 class="marked" 的 p 元素指定一个样式。



---
### &nbsp;&nbsp; <a id="04">定位</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 尺寸(Dimension)

1. 设置元素的高度`Height:20px Width`
2. 百分比设置`Height:50%`
3. 像素`Height:20--也是像素`
4. 元素最大高度`max-Hieght:20`
5. 百分比最大高度`max-Height:50%`
6. 最低高度`min-Height:20`

:star:显示(display)与可见性(Visibility)

```css
h1.hidden {visibility:hidden;}  --这样做只是隐藏元素，但原本元素仍要占据原本的空间。
```

```
h1.hidden {display:none;}   --这样做就能让某个元素'消失',意味着不会占用空间了。
```


- 块和内联元素

块元素是一个元素，占用了全部宽度，在前后都是换行符。    
块元素的例子：   
- <h1> 
- <p>
- <div>
	
内联元素只需要必要的宽度，不强制换行。   
内联元素的例子：   
- <span>
- <a>

- 改变元素显示
```css
li {display:inline;}  --把列表项显示为内联元素
span {display:block;} --把span元素作为块元素
```
:star: Position(定位)

position有5个值:
1. static  --定位的元素，无特殊定位，遵循正常的文档流对象
2. relative  --相对定位元素的定位是相对其正常位置。
3. fixed   --元素的位置相对于浏览器窗口是固定位置。即使窗口是滚动的它也不会移动，不占据空间
4. absolute  --绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>
5. sticky   --表示"粘性的"，它的行为就像 position:relative; 而当页面滚动超出目标区域时，它的表现就像 position:fixed;，它会固定在目标位置。   

- 重叠的元素   
元素的定位于文档流无关，所以他们可以覆盖页面上的其他元素    
`z-index:number`制定了一个元素的堆叠顺序,正值往前覆盖，负值往后覆盖

- 例子
```css
img 
{
	position:absolute;
	clip:rect(0px,60px,200px,0px);   --裁剪元素的外形
}
```
```css
div.ex1 {
    background-color: lightblue;
    width: 110px;
    height: 110px;
    overflow: scroll;     --设置滚动条显示未完全显示的内容
    overflow: hidden;	-- 隐藏未完全显示的内容
    overflow: auto   --滚动条由浏览器决定
    overflow: visible  --(默认)显示
}
```

[更改光标](https://www.runoob.com/try/try.php?filename=trycss_cursor)


:star: Float(浮动)    
CSS 的 Float（浮动），会使元素向左或向右移动，其周围的元素也会重新排列。    
Float（浮动），往往是用于图像，但它在布局时一样非常有用。

元素的水平方向浮动，意味着元素只能左右移动而不能上下移动。一个浮动元素会尽量向左或向右移动，直到它的外边缘碰到包含框或另一个浮动框的边框为止。    
浮动元素之后的元素将围绕它。      浮动元素之前的元素将不会受到影响。

```css
彼此相邻的浮动元素 :
.thumbnail 
{
    float:left;
    width:110px;
    height:90px;
    margin:5px;
}
```

```css
清除浮动 - 使用 clear  使元素两侧不出现浮动元素
.text_line
{
    clear:both;
}
```

:star: 对齐

1. 要水平居中对齐一个元素(如 <div>), 可以使用 margin: auto;
	
2. 如果仅仅是为了文本在元素内居中对齐，可以使用 text-align: center;

3. 要让图片居中对齐, 可以使用 margin: auto; 并将它放到 块 元素中:

4. 我们可以使用 position: absolute; 属性来对齐元素  `注释：绝对定位元素会被从正常流中删除，并且能够交叠元素。`
```css
.right {
    position: absolute;
    right: 0px;
    width: 300px;
    background-color: #b0e0e6;
}
```

左右对齐 - 使用 float 方式
```css
.right {
    float: right;
    width: 300px;
    border: 3px solid #73AD21;
    padding: 10px;
}
-- 如果子元素的高度大于父元素，且子元素设置了浮动，那么子元素将溢出，这时候你可以使用 "clearfix(清除浮动)" 来解决该问题。

我们可以在父元素上添加 overflow: auto; 来解决子元素溢出的问题:

.clearfix {
    overflow: auto;
}



垂直居中 - 使用 position 和 transform
除了使用 padding 和 line-height 属性外,我们还可以使用 transform 属性来设置垂直居中:
.center { 
    height: 200px;
    position: relative;
    border: 3px solid green; 
}
 
.center p {
    margin: 0;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```







---
### &nbsp;&nbsp; <a id="05">组合选择符</a>&nbsp;&nbsp;<a href="#top">:blue_book:</a>

:star: 四种组合方式

1. 后代选择器(以空格分隔)
2. 子元素选择器(以大于号分隔）
3. 相邻兄弟选择器（以加号分隔）
4. 普通兄弟选择器（以破折号分隔）


- 后代选择器
```css
后代选择器用于选取某元素的后代元素。
div p
{
  background-color:yellow;
}
```

- 子元素选择器
```css
与后代选择器相比，子元素选择器（Child selectors）只能选择作为某元素子元素的元素。
div>p
{
  background-color:yellow;
}
```

- 相邻兄弟选择器
```css
如果需要选择紧接在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟选择器
以下实例选取了所有位于 <div> 元素后的第一个 <p> 元素:
div+p
{
  background-color:yellow;
}
```

- 普通兄弟选择器
```css
后续兄弟选择器选取所有指定元素之后的相邻兄弟元素。
以下实例选取了所有 <div> 元素之后的所有相邻兄弟元素 <p> : 
div~p
{
  background-color:yellow;
}
```


##### :star: 伪类
```css
a:link {color:#FF0000;} /* 未访问的链接 */
a:visited {color:#00FF00;} /* 已访问的链接 */
a:hover {color:#FF00FF;} /* 鼠标划过链接 */
a:active {color:#0000FF;} /* 已选中的链接 */


--匹配第一个p元素
p:first-child
{
    color:blue;
}


--选择相匹配的所有<p>元素的第一个 <i> 元素：
p > i:first-child
{
    color:blue;
}

匹配所有作为第一个子元素的 <p> 元素中的所有 <i> 元素
p:first-child i
{
    color:blue;
}
```
[伪类集合](https://www.runoob.com/css/css-pseudo-classes.html)
[伪元素集合](https://www.runoob.com/css/css-pseudo-elements.html)


---












