```html
Web 上的许多内容都是列表，HTML 有一些特别的列表元素。标记列表通常包括至少两个元素。最常用的列表类型为：

无序列表（Unordered List）中项目的顺序并不重要，就像购物列表。用一个 <ul> 元素包围。
有序列表（Ordered List）中项目的顺序很重要，就像烹调指南。用一个 <ol> 元素包围。
列表的每个项目用一个列表项目（List Item）元素 <li> 包围。
```
```html
    <p title="LOL is short for league of legends">LOL</p>
```

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>

<body>

<b>这个文本是加粗的</b>

<br />

<strong>这个文本是加粗的</strong>

<br />

<big>这个文本字体放大</big>

<br />

<em>这个文本是斜体的</em>

<br />

<i>这个文本是斜体的</i>

<br />

<small>这个文本是缩小的</small>

<br />

这个文本包含
<sub>下标</sub>     <!--htlm的下标可用于化学源于 H2O  H<sub>2</sub>-->

<br />

这个文本包含
<sup>上标</sup>   <!--2个氧离子：2O<sup>2-</sup>-->

</body>
</html>
```

代码段标签
```html
<pre>
代码...
</pre>
```


```html
<code>计算机输出</code>
<br />
<kbd>键盘输入</kbd>
<br />
<tt>打字机文本</tt>
<br />
<samp>计算机代码样本</samp>
<br />
<var>计算机变量</var>
<br />

<p>
<b>注释：</b>这些标签常用于显示计算机/编程代码。
</p>
```

:star:地址
```html
<address>
Written by <a href="mailto:webmaster@example.com">Jon Doe</a>.<br> 
Visit us at:<br>
Example.com<br>
Box 564, Disneyland<br>
USA
</address>
```

:star:首字母缩写，单词简写
```html
<abbr title="etcetera">etc.</abbr>
<br />
<acronym title="World Wide Web">WWW</acronym>
```

:star:文字从右往左显示
```html
<p><bdo dir="rtl">该段落文字从右到左显示。</bdo></p>  
```


:star:引用文字,,显示出来带引号
```html
<q>Build a future where people live in harmony with nature.</q>
```

:star:删除文字和插入文字
```html
<del>blue</del> <ins>red</ins>
```


:star:链接target属性
```html
_blank	在新窗口中打开被链接文档。
_self	默认。在相同的框架中打开被链接文档。
_parent	在父框架集中打开被链接文档。
_top	在整个窗口中打开被链接文档。
```

链接下载文件
```html
<a href="/images/logo.png" download="/images/logo.png">
<img border="0" src="/images/logo.png" alt="runoob.com" >
</a>
```

电子邮件1
```html
<p>
这是一个电子邮件链接：
<a href="mailto:someone@example.com?Subject=Hello%20again" target="_top">
发送邮件</a>
</p>
```

电子邮件2
```html
<p>
这是另一个电子邮件链接：
<a href="mailto:someone@example.com?cc=someoneelse@example.com&bcc=andsomeoneelse@example.com&subject=Summer%20Party&body=You%20are%20invited%20to%20a%20big%20summer%20party!" target="_top">发邮件!</a>
</p>
```

默认链接
```html
写在头部
<base href="//www.runoob.com/images/" target="_blank">
```

meta元素

```html
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
<meta name="description" content="免费在线教程">
<meta name="keywords" content="HTML,CSS,XML,JavaScript">
<meta name="author" content="runoob">
</head>
```

:star:表格
```html
单元格可以嵌入别的代码

    <h3>水平标题:</h3>
    <table border="1">
        <tr>
            <th>第一列</th>
            <th>第二列</th>
            <th>第三列</th>
        </tr>
        <tr>
            <td>英语</td>
            <td>语文</td>
            <td>数学</td>
        </tr>
    </table>
    <h3>垂直标题:</h3>
    <table border="1">
        <tr>
            <th>第一列</th>
            <td>英语</td>
        </tr>
        <tr>
            <th>第二列</th>
            <td>语文</td>
        </tr>
        <tr>
            <th>第三列</th>
            <td>数学</td>
        </tr>
    </table>
```

```html
  <th colspan="2">Telephone</th>  单元格跨两行
```
```html
  <th rowspan="2">Telephone:</th>  单元格跨2列

<table border="1" 
cellpadding="10">   --设置单元格的内边距
  
  <table border="1" cellspacing="10">    --设置单元格间距
```

[漂亮的表格](https://c.runoob.com/codedemo/3187)

    

:star:有序列表 
      
```html

默认的列表
 <ol>
   
   
<h4>大写字母列表：</h4>
<ol type="A">

  
  
  
<h4>小写字母列表：</h4>
<ol type="a">    

    
    
<h4>罗马数字列表：</h4>
<ol type="I">    
    
<h4>小写罗马数字列表：</h4>
<ol type="i">
```    

:star:无序列表
  
```html
<ul style="list-style-type:disc">
<ul style="list-style-type:circle">
<ul style="list-style-type:square">  
```  
  
自定义列表
```html
<dl>
  <dt>Coffee</dt>
  <dd>- black hot drink</dd>
  <dt>Milk</dt>
  <dd>- white cold drink</dd>
</dl>
```  

  
:star: 区块
```html
  
<div>	定义了文档的区域，块级 (block-level)  用来组合多种标签元素
<span>	用来组合文档中的行内元素， 内联元素(inline)
  
```
  

:star: 表单
  ```html
  --文本和密码字段
<form action="">
Username: <input type="text" name="user"><br>
Password: <input type="password" name="password">
</form>
  
  --单选按钮
<input type="radio" name="sex" value="male">Male<br>
<input type="radio" name="sex" value="female">Female
  --复选框
<input type="checkbox" name="vehicle" value="Bike">I have a bike<br>
<input type="checkbox" name="vehicle" value="Car">I have a car 
  --提交按钮
  <input type="submit" value="Submit">
  ---下拉列表
  <select name="cars">
<option value="volvo">Volvo</option>
<option value="saab">Saab</option>
<option value="fiat">Fiat</option>
<option value="audi">Audi</option>
<option value="fiat" selected>Fiat</option>   --预选中这个元素，若不指定，则默认选中第一个元素
</select>
  ```
  
  label标签
  ```html
  <label for="male">Male</label>
  <input type="radio" name="sex" id="male" value="male"><br>
```
  fieldset 定义了一组相关的表单元素，并使用外框包含起来
  ```html
 <fieldset>
  <legend>Personalia:</legend>  --制定了fieldset标签的标题
  Name: <input type="text"><br>
  Email: <input type="text"><br>
  Date of birth: <input type="text">
 </fieldset>
```

output 定义了计算结果
```html
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100
+<input type="number" id="b" value="50">
=<output name="x" for="a b"></output>
</form>
```
[字符实体](https://www.runoob.com/html/html-entities.html)  

  
  
  
