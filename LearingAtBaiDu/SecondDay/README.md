

#### :star: SomeQuestions
1. HTML是什么，HTML5是什么?
```
HTML:HyperTextMarkupLanguage,是用于创建网页的标准标记语言
HTML5: 是下一代HTML标准，在HTML的基础上引入了新特性
```
2. 文档类型是什么概念，起什么作用？
```
概念：
HTML文档类型是为浏览器提供一项声明，目的是为了告诉浏览器HTML文档的版本信息，因此没有闭合/结束标签。

作用：
因为HTML文档有许多不同的版本，就像计算机中的不同的文件类型，只有通过特定的软件才能正确地打开相应的文件；HTML文档相当于一个文件，我们需要告诉浏览器HTML文档是什么类型，浏览器才能够准确地打开HTML文档。
```
3. meta标签都用来做什么的？
```
<meta> 标签提供了 HTML 文档的元数据。元数据不会显示在客户端，但是会被浏览器解析。
META元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者及其他元数据。
<head>
<meta charset="utf-8"> 
<title>菜鸟教程(runoob.com)</title> 
<meta name="description" content="免费在线教程">
<meta name="keywords" content="HTML,CSS,XML,JavaScript">
<meta name="author" content="runoob">
</head>

meta的作用远不于此，它非常的有用！

```

4. Web语义化是什么，是为了解决什么问题
```
是为了适应越来越大的web规模，统一标准
应该在发布内容的时候，就用机器可读的、被广泛认可的语义信息来描述内容，来降低机器处理 Web 内容的难度（HTML 本身就已经是朝这个方向迈出的一小步了）。
```
5. 链接是什么概念，对应什么标签？
```
<a> 标签定义超链接，用于从一个页面链接到另一个页面。,也可以在当前页面变化，比如[回到顶部]这一网页常用按钮
<a> 元素最重要的属性是 href 属性，它指定链接的目标。


在所有浏览器中，链接的默认外观如下：
未被访问的链接带有下划线而且是蓝色的
已被访问的链接带有下划线而且是紫色的
活动链接带有下划线而且是红色的
```
6. 常用标签都有哪些，都适合用在什么场景
```
a,p,h,body,head,html,div,br...等等标签
```
7. 表单标签都有哪些，对应着什么功能，都有哪些属性
```
form,input,textarea,label,
fielddset:定义了一组相关的表单元素，并使用外框包含起来
legend:定义了fieldset的标题
select:定义了下拉列表
button:定义了一个点击按钮
datalist:在文本框中的一个下拉列表（<option value=""> 为子项）,例如登陆qq可以看到有许多登陆过的qq，可以选择一个登陆

output标签，定义输出
<form oninput="x.value=parseInt(a.value)+parseInt(b.value)">0
<input type="range" id="a" value="50">100
+<input type="number" id="b" value="50">
=<output name="x" for="a b"></output>
</form>


```
8. ol, ul, li, dl, dd, dt等这些标签都适合用在什么地方，举个例子
```
ol,定义了一个有序列表，列表排序以数字显示，默认从1开始，但是可以修改
    <ol start="50">
        <li>咖啡</li>
    </ol>
ul:定义了一个无序列表，当列表嵌套的时候，无序列表样式会发生变化
    <ul>
      <li>咖啡</li>
    </ul>
li:作为列表的子元素，呈现列表数据
dl: <dl> 标签定义一个描述列表。
<dl> 标签与 <dt> （定义项目/名字）和 <dd> （描述每一个项目/名字）一起使用。
<dl>
  <dt>Coffee</dt>
    <dd>Black hot drink</dd>
  <dt>Milk</dt>
    <dd>White cold drink</dd>
</dl>
```

9.HTML元素标签、属性都是什么概念？
```
标签：
HTML标签标记了HTML文档和HTML元素
HTML标签由开始标签和结束标签组成.开始标签为尖括号包围的元素名,结束标签为尖括号包围的斜杠和元素名

属性
HTML属性为HTML元素提供附件信息,例如在超链接标签<a href = “http://www.cnblogs.com>博客园</a>使用了href 来指定超链接的地址.
属性总是以名称/值的形式出现,例如:name = “value”
属性总是在开始标签中定义.
```
