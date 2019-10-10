#                                        ------------------------------ DOM ------------------------------
<p id="title"></p>

## 目录

:arrow_down:<a href="#01">节点层次</a>

:arrow_down:<a href="#02">DOM操作技术</a>

:arrow_down:<a href="#03">总结</a>



DOM（文档对象模型）是针对HTML和XML文档的一个API（应用程序编程接口）。DOM描绘了一个层次化的节点树，允许开发人员添加、移除和修改页面的某一部分。DOM脱胎于Netscape及微软公司创始的DHTML（动态HTML），但现在它已经成为表现和操作页面标记的真正的跨平台、语言中立的方式。


<p id="01"></p>

### 节点层次
:arrow_double_up:<a href="#title">返回目录</a>

1.用一幅图直观的描述节点之间的关系：
![节点关系图](https://github.com/swordboyASS/JavaScript./blob/master/Picture/node.png)


2.操作节点
appendChild（），在childNodes列表的末尾添加一个节点。
```javascript
    <script>
        window.onload = function()
        {
         
           

            var ul1 = document.querySelector("#ul1") //取得要添加子节点的元素
            var li = document.createElement("li")//新建一个li元素节点，新建之后才可以添加进去。

            ul1.appendChild(li);
            li.innerHTML="hh";
            // ul.innerHTML = "777";
        }
    </script>
</head>

<body>
    <div>
        <ul id="ul1">
            <li>111</li>
            <li>222</li>
            <li>333</li>
        </ul>
    </div>
</body>
```

如果需要把节点放在childNodes列表中某个特定的位置上，而不是放在末尾，那么可以使用insertBefore（）方法。这个方法接受两个参数：要插入的节点和作为参照的节点。插入节点后，被插入的节点会变成参照节点的前一个同胞节点（previoussibling），同时被方法返回。
如果参照节点是nu11，则insertBefore（）与appendchild（）执行相同的操作，如下面的例子所示。
```javascript
            //  插入成为最后一个子节点
            var ul1 = document.querySelector("#ul1") //取得要添加子节点的元素
            var li = document.createElement("li")//新建一个li元素节点，新建之后才可以添加进去。
            ul1.insertBefore(li,null);
            li.innerHTML="hh"; 
```

```javascript
        //插入成为第一个节点。
        ul1.insertBefore(li,ul1.firstChild);  //其余部分和上面的例子相同。
```

```javascript
      //插入到最后一个子节点前面
      ul1.insertBefore(li,ul1.lastChild);
```

```javascript
    //插入到最后一个子节点前面
    ul1.insertBefore(li,ul1.lastChild); //因为最后一个节点是文本节点，但文本节点的内容是空的，所以看起来插入的节点还是在最后。
  

       // 这个ul中有4个文本节点。
        <ul id="ul1">1
            <li>111</li>3
            <li>222</li>5
            <li>333</li>7
        </ul>

```

替换节点：
```javascript
    //替换第一个子节点
  var returnedNode=someNode.replaceChild（newNode，someNode.firstChild）；

  //替换最后一个子节点
  returnedNode=someNode.replaceChild（newNode，someNode.lastChild）；
```

移出节点
```javascript
//移除第一个子节点
var formerFirstChild=someNode.removeChild（someNode.firstChild）；

//移除最后一个子节点
var formerLastChild=someNode.removeChild（someNode.lastChild）；
```
与使用replacechi1d（）方法一样，通过removechild（）移除的节点仍然为文档所有，只不过在文档中已经没有了自己的位置。


其他方法：
有两个方法是所有类型的节点都有的。第一个就是cloneNode（），用于创建调用这个方法的节点的一个完全相同的副本。cloneNode（）方法接受一个布尔值参数，表示是否执行深复制。在参数为true的情况下，执行深复制，也就是复制节点及其整个子节点树；在参数为false的情况下，执行浅复制，即只复制节点本身。复制后返回的节点副本属于文档所有，但并没有为它指定父节点。因此，这个节点副本就成了一个"孤儿"，除非通过上面的方法为它添加子节点。

我们要介绍的最后一个方法是normalize（），这个方法`唯一的作用就是处理文档树中的文本节点。`
由于解析器的实现或DOM操作等原因，可能会出现文本节点不包含文本，或者接连出现两个文本节点的情况。当在某个节点上调用这个方法时，就会在该节点的后代节点中查找上述两种情况。如果找到了空文本节点，则删除它；如果找到相邻的文本节点，则将它们合并为一个文本节点。本章后面还将进一步讨论这个方法。




#### Document类型


##### 文档的子节点
1.documentElement属性，该属性直接指向HTML界面的<html>元素。 
2.body属性，该属性直接指向HTML界面的<body>元素。 
3.childNodes列表属性访问文档元素  `document.childNodes[0]`

##### 文档信息
1.title属性，
`var title = document.title;//取得文档的标题,同样使用这个属性可以修改文档标题`
2.URL、domain、referrer
```javascript
//取得完整的URL 
var url=document.URL；

//取得域名
var domain=document.domain;

////取得来源页面的URL 
var referrer=document.referrer；
```

##### 查找元素
getElementById（）//返回有该id的元素
getElementsByTagName（）//返回一个列表（NodeList）

```
  var images=document. getElementsByTagName("img");
  alert{images.1ength）；//输出图像的数量
  alert（images[0].src）；//输出第一个图像元素的srC特性
  alert（images.item（0）.src）；//输出第一个图像元素的src特性
```
HTMLCo11ection 对象还有一个方法，叫做namedItem（），使用这个方法可以通过元素的name特性取得集合中的项。例如，假设上面提到的页面中包含如下<img>元素：
```JavaScript
<img src="myimage.gif"name="my Image">

//那么就可以通过如下方式从images变量中取得这个<img>元素：
var myImage=images.namedItem（"myImage"）；


//也可以使用放过好的方式取得有name属性的img标签
var myImage=images["myImage"]；

```

getElementsByTagName（"\*"）,取得所有元素。



#### 特殊集合、DOM一致性检测、文档写入（有机会用到再写）
文档写入：有一个document对象的功能已经存在很多年了，那就是将输出流写人到网页中的能力。这个能力体现在下列4个方法中：write（）、writeln（）、open（）和close（）。其中，write（）和writeln（）方法都接受一个字符串参数，即要写入到输出流中的文本。write（）会原样写入，而writeln（）则会在字符串的末尾添加一个换行符（\n）。在页面被加载的过程中，可以使用这两个方法向页面中动态地加入内容，如下面的例子所示。
```javascript
<htm1>
<head>
<title>document. write() Example</title>
</head>

<body>
  <p>The current date and time is:
  <script type="text/javascript">
      document. write("<strong>"+(new Date()). toString()+"</strong>");
  </script>
  </p>
</body>
</html>
```

如果在页面加载完后再使用这个方法，会重写整个页面内容！
```
window. onload=function(){
    document. write("Hello world!");
};
```
方法open（）和close（）分别用于打开和关闭网页的输出流。如果是在页面加载期间使用write（）或wriseln（）方法，则不需要用到这两个方法。




#### Element类型

2.取得特性(属性)
每个元素都有一或多个特性，这些特性的用途是给出相应元素或其内容的附加信息。操作特性的DOM方法主要有三个，分别是getAttribute（）、setAttribute（）和removeAttribute（）。这三个方法可以针对任何特性使用，包括那些以HIMLE1ement类型属性的形式定义的特性。来看下面的例子：
```javascript
var div=document.getElementById（"myDiv"）；
alert（div.getAttribute（"id"））；//"myDiv"
alert（div.getAttribute（"class"））；//"bd"
alert{div.getAttribute（"title"））；//"Body text"
alert（div.getAttribute（"lang"））；//"en"
alert（div.getAttribute（"dir"））;//"itr"
```

3.设置特性
与getAttribute（）对应的方法是setAttribute（），这个方法接受两个参数：要设置的特性名和值。如果特性已经存在，setAttribute（）会以指定的值替换现有的值；如果特性不存在，setAttribute（）则创建该属性并设置相应的值。来看下面的例子：
```javascript
div. setAttribute("id","someotherId"); d
iv. setAttribute("class","ft"); 
div. setAttribute("title","Some other text"); 
div. setAttribute("lang","fr"); 
div. setAttribute("dir","rt1");
```
值得注意的是，特性的名称是不区分大小写的。

要介绍的最后一个方法是removeAttribute（），这个方法用于彻底删除元素的特性。调用这个方法不仅会清除特性的值，而且也会从元素中完全删除特性，如下所示：
`div.removeAttribute（“class"）；`

4.attributes属性(有用的时候再写)



5.创建元素
使用document.createElement（）方法可以创建新元素。
```
var div=document. createElement("div");
div.id="myNewDiv"; 
div.className="box";  //可以为它设置一些属性，
//最后使用下面的方法，添加到文档中。
document.body.appendChild(div);
```

也可以用这个方法传入完整的元素标签，也可以包含属性：
```javascript
var div=document. createElement("<div id=\"myNewDiv\"class=\"box\"></div >");
```


6.元素的子节点


##### Text类型

在默认情况下，每个可以包含内容的元素最多只能有一个文本节点，而且必须确实有内容存在。来看几个例子。
```javascript
<！--没有内容，也就没有文本节点-->
<div></div>

<！--有空格，因而有一个文本节点-->
<div> </div>

<--有内容，因而有一个文本节点-->
<div>Hel1o world！</divs
```
值为“He11o World！"。可以使用以下代码来访问这些文本子节点。
`var textNode=div.firstchild；//或者div.childNodes[0]`

在取得了文本节点的引用后，就可以像下面这样来修改它了。里面插入的HTML代码也会被编码。
`div.firstChild.nodeValue="Some other message"；` 

1.创建文本节点
```javascript
var element=document. createElement("div"); 
element. className="message";

var textNode=document. createTextNode("He1lo world!");
element. appendChi1d(textNode); 

document. body. appendchild(element);
```


2.规范化文本节点

3.分割文本节点

##### Comment类型

##### CDATASection类型

##### DocumentType类型

##### DocumetFragment类型

##### Attr类型


<p id="02"></p>

### DOM操作技术
:arrow_double_up:<a href="#title">返回目录</a>



 1.动态脚本（外部引入文件）
 
 2.动态样式(外部引入文件)
 
 
 ##### 3.操作表格
 <table>元素是HTML中最复杂的结构之一。要想创建表格，一般都必须涉及表示表格行、单元格、表头等方面的标签。由于涉及的标签多，因而使用核心DOM方法创建和修改表格往往都免不了要编写大量的代码。假设我们要使用DOM来创建下面的HTML表格。
 
 ```javascript
    <table border="1"width="100%">
<tbody>
        <tr>
         <td>Cel11,1</td><td>Cel12,1</td>
        </tr>
        <tr>
            <td>Cel11,2</td><td>Cel12,2</td>
        </tr>
</tbody>
    </table>
 ```

要使用DOM来创建下面的HTML表格，要需要大量的代码（此处不做演示），工作量大，所以为了方便构建表格，HTMLDOM为<table><tbody><tr>添加了一些属性

为table>元素添加的属性和方法如下。

|||
|:---|:---|
|caption：|保存着对`<caption>`元素（如果有）的指针。|
|tBodies：|是一个`<tbody>`元素的HTMLCo1lection。|
|tFoot：|保存着对`<tfoot>`元素（如果有）的指针。
|tHead：|保存着对<thead>元素（如果有）的指针。|
|rows：|是一个表格中所有行的HTMLCo11ection。|
|createTHead（）：|创建`<thead>`元素，将其放到表格中，返回引用。
|createTFoot（）：|创建`<tfoot>`元素，将其放到表格中，返回引用。|
|createcaption（）：|创建`<caption>`元素，将其放到表格中，返回引用。|
|deleterHead（）：|删除`<thead>`元素。
|deleteTFoot（）：|删除`<tfoot>`元素。|
|deletecaption（）：|删除`<caption>`元素。|
|deleteRow（pos）：|删除指定位置的行。|
|insertRow（pos）：|向rows集合中的指定位置插入一行。|
    
为<tbody>元素添加的属性和方法如下。
    
|||
|:---|:---|    
|rows：|保存着`<tbody>`元素中行的HTMLCo1lection。|
|deleteRow（pos）：|删除指定位置的行。|
|insertRow（pos）：|向rows集合中的指定位置插入一行，返回对新插入行的引用。|
    
为<tr>元素添加的属性和方法如下。  
    
|||
|:---|:---|   
|ce11s：|保存着`<tr>`元素中单元格的HMLCollection。|
|deletece11（pos）：|删除指定位置的单元格。|
|insertCe11（pos）：|向ce11s集合中的指定位置插入一个单元格，返回对新插入单元格的引用。|


例子：
```javascript
//创建table 
var table=document.createElement（"table"）；
table.border=1；
table.width=“100%"；

//创建 tbody 
var tbody=document.createElement（"tbody"）；
table.appendChild（tbody）；

//创建第一行
tbody.inaertRow（0）;
tbody.rowe[0].insertcel1（0）；
tbody.rows[0].ce11s[0].appendchi1d（document.createrextNode（"Cel1 1，1"））；
tbody.rows[01.insertcel1（1）；
tbody.rows[0].ce11s[1].appendchild（document.createrextNode（"Cel1 2，1"））；


//创建第二行
tbody.ingertRow（1）；
tbody.rowa[11.insertcel1（0）；
tbody.rows[11.ce11s[0].appendchi1d（document.createrextNode（"Ce11 1，2"））；
tbody.rows[1].insertCel1（1）；
tbody.rows[11.ce118[1].appendchi1d（document.createrextNode（"Cel1 2，2"））；

//将表格添加到文档主体中
document.body.appendChild（table）；
```

#####  使用NodeList
理解NodeList及其近亲NamedNodeMap和HTMLCo11ection，是从整体上透彻理解DOM的关键，这三个集合都是动态的，换句话说，就是每当文档结构发生变化时，它们都会得到更新。

以下代码会导致无限循环。
```javascript
var divs=document. getElementsBy TagName("div"), 
i, 
div;
for(i=0;i< divs. length;i++){
div=document. createElement("div");
document. body. appendChild(div);
}
```
一般来说，应该尽量减少访问NodeList的次数。因为每次访问NodeList，都会运行一次基于文档的查询。所以，可以考虑将从NodeList中取得的值缓存起来。


<p id="03"></p>

### 总结
:arrow_double_up:<a href="#title">返回目录</a>

DOM是语言中立的API，用于访问和操作HTML和XML文档。DOM1级将HTML和XML文档形象地看作一个层次化的节点树，可以使用JavaScript来操作这个节点树，进而改变底层文档的外观和结构。

DOM由各种节点构成，简要总结如下。
* 最基本的节点类型是Node，用于抽象地表示文档中一个独立的部分；所有其他类型都继承自Node。
* Document类型表示整个文档，是一组分层节点的根节点。在JavaScript中，document对象是Document的一个实例。使用document对象，有很多种方式可以查询和取得节点。
* Element节点表示文档中的所有HTML或XML元素，可以用来操作这些元素的内容和特性。
* 另外还有一些节点类型，分别表示文本内容、注释、文档类型、CDATA区域和文档片段。

访问DOM的操作在多数情况下都很直观，不过在处理<script>和<style>元素时还是存在一些复杂性。由于这两个元素分别包含脚本和样式信息，因此浏览器通常会将它们与其他元素区别对待。这些区别导致了在针对这些元素使用innerHTML时，以及在创建新元素时的一些问题。

理解DOM的关键，就是理解DOM对性能的影响。DOM操作往往是JavaScript程序中开销最大的部分，而因访问NodeList导致的问题为最多。NodeList对象都是“动态的”，这就意味着每次访问NodeList对象，都会运行一次查询。有鉴于此，最好的办法就是尽量减少DOM操作。
