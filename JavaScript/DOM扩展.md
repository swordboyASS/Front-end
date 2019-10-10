# ---------------------- DOM扩展 ----------------------

<p id="title"></p>

## 目录

:arrow_down:<a href="#01">选择符API</a>

:arrow_down:<a href="#02">元素遍历</a>

:arrow_down:<a href="#03">HTML5</a>

:arrow_down:<a href="#04">专有扩展</a>

:arrow_down:<a href="#05">总结</a>

对DOM的两个主要的扩展是Selectors API（选择符API）和HTML5。这两个扩展都源自开发社区，而将某些常见做法及API标准化一直是众望所归。此外，还有一个不那么引人瞩目的Element Traversal(元素遍历)规范，为DOM添加了一些属性。

Selectors API Level1的核心是两个方法：querySelector（）和queryselectorA11（）

### 选择符API<p id="01"></p>

### :arrow_double_up:<a href="#title">返回目录</a>

##### queryselector（）方法
queryselector（）方法接收一个CSS选择符，返回与该模式匹配的第一个元素，如果没有找到匹配的元素，返回nu11。请看下面的例子。
```javascript
//取得body元素
  var body=document.querySelector（"body"）；
  
//取得ID为“myDiv”的元素
  var myDiv=document.queryselector（"#myDiv"）；
  
//取得类为“selected“的第一个元素
  var selected=document.querySelector（".selected"）；
  
//取得类为“button”的第一个图像元素
  var img=document，body.querySelector（"img.button"）；
```
如果被传入了不支持的选择符，queryselector()会抛出错误。


### 元素遍历<p id="02"></p>

### :arrow_double_up:<a href="#title">返回目录</a>

##### querySelectorA11（）方法
querySelectorA11（）方法接收的参数与queryselector（）方法一样，都是一个CSS选择符，但返回的是所有匹配的元素而不仅仅是一个元素。这个方法返回的是一个NodeList的实例。

与queryselector（）类似，能够调用queryselectorA11（）方法的类型包括Document、DocumentFragment和Element。下面是几个例子。
```javascript
  //取得某<div>中的所有<em>元素（类似于getElementsBy TagName（"em"））
  var ems=document.getElementById（"myDiv"）.querySelectorA11（"em"）；

  //取得类为“selected“的所有元素
  var selecteds=document.querySelectorAll（".selected"）；

  //取得所有<p>元素中的所有<strong>元素
  vas strongs=document.querySelectorAl1（"p strong"）；
```

要取得返回的NodeList中的每一个元素，可以使用item（）方法，也可以使用方括号语法，比如：
```javascript
var i，len，strong；
for（i=0，len=strongs.length；i< len；i++）{
strong=strongs[i]；//或者strongs.item（i）
strong.className="important"；
}
同样与queryselector（）类似，如果传入了浏览器不支持的选择符或者选择符中有语法错误，querySelectorA11（）会抛出错误。
```

##### matchesSelector（）方法
Selectors API Level2规范为Element类型新增了一个方法matchesselector（）。这个方法接收一个参数，即CSS选择符，如果调用元素与该选择符匹配，返回true；否则，返回false。看例子。
```javascript
if（document.body.matchesselector（"body.pagel"））{  //如果有这个类名的话，返回true
//true
}
```


##### 元素遍历
Element Traversal API为DOM元素添加了以下5个属性。
* childElementCount：返回子元素（不包括文本节点和注释）的个数。
* firstElementChild：指向第一个子元素；firstchild的元素版。口lastElementchild：指向最后一个子元素；1astchild的元素版。
* previousElementsibling：指向前一个同辈元素；previoussibling的元素版。
* nextElementSibling：指向后一个同辈元素；nextSibling的元素版。
支持的浏览器为DOM元素添加了这些属性，利用这些元素不必担心空白文本节点，从而可以更方便的查找DOM元素了。





### HTML5<p id="03"></p>

### :arrow_double_up:<a href="#title">返回目录</a>

1.getElementByClassName("参数"),一个参数

2.classList属性:非常好用（大量简化代码，优化程序  ）
此外，这个新类型还定义如下方法。
* add（value）：将给定的字符串值添加到列表中。如果值已经存在，就不添加了。
* contains（value）：表示列表中是否存在给定的值，如果存在则返回true，否则返回false。
* remove（value）：从列表中删除给定的字符串。
* toggle（value）：如果列表中已经存在给定的值，删除它；如果列表中没有给定的值，添加它。


它的方法能极大地减少类似基本操作的复杂性，如下面的例子所示。
```javascript
//删除“disabiedn类
div.classList.remove（"disabled"）；

//添加“current“类
div.classList.add（"current"）；

//切换“user“类
div.classList.toggle（"user"）；

//确定元素中是否包含既定的类名
if（div.classList.contains（"bd"）&&！div.classList.contains（"disabled"））（
//执行操作
)

//选代类名
for（var i=0，len=div.classList.1ength；i<len；i++）{
    doSomething（div.classList[i]）；
}
 ```
有了classList属性，除非你需要全部删除所有类名，或者完全重写元素的class属性，否则也就用不到className属性了。


##### 焦点管理

HTML5也添加了辅助管理DOM焦点的功能。首先就是document.activeElement属性，这个属性始终会引用DOM中当前获得了焦点的元素。元素获得焦点的方式有页面加载、用户输入（通常是通过按Tab键）和在代码中调用`focus（）`方法。来看几个例子。
```javascript
var button=document.getElementById（"myButton"）；
button.focus（）；
alert（document.activeElement===button）；//true
```
默认情况下，文档刚刚加载完成时，document.activeElement中保存的是document.body元素的引用。文档加载期间，document.activeElement的值为nul1。
另外就是新增了`document.hasFocus（）`方法，这个方法用于确定文档是否获得了焦点。
```javascript
var button=document.getElementById（"myButton"）；
  button. focus(); 
alert(document, hasFocus());//true
```

##### readyState属性
有2个可能的值：
1.loading：正在加载文档，  
2.complete：文档加载完成。  

基本使用方法如下：
```javascript
  if(document.readyState=="complete"){
    //要执行的语句。
  }
```


##### 自定义数据属性：

HTML5规定可以为元素添加非标准的属性，但要添加前缀data-，目的是为元素提供与渲染无关的信息，或者提供语义信息。这些属性可以任意添加、随便命名，只要以data-开头即可。来看一个例子。
`<div id="myDiv"data-appId="12345"data-myname="Nicholas"></div>`
添加了自定义属性之后，可以通过元素的 dataset属性来访问自定义属性的值。
```javaacript
var div=document.getElementById（"myDiv"）；

//取得自定义属性的值
var appId=div.dataset.appId；
var myName=div.dataset.myname；

//设置值
div.dataset.appld=23456；
div.dataset.myname="Michael"；

//有没有“myname“值呢？
if{div.dataset.myname）{
    alert("Hello,"+div.dataset.nmyname)
}
```



#### 插入标记
1.innerHTML属性：可以只插入文本，也可以带有HTML标签，直接编译成HTML的标签。  调元元素的innerHTML属性，会返回整个DOM·子·树。
```javascript
div.innerHTML="Hello world！"； //只设置文本

为innerHTML设置的包含HTML的字符串值与解析后innerHTML的值大不相同。来看下面的例子。

div.innerHTML="Hel1o&welcome，<b>\"reader\"！</b>"； //设置HTML标签。
```

2.outerHTML属性 ：在读模式下，outerHTML返回调用·它的元素及所有子节点·（请区别与innerHTML）的HTML标签。在写模式下，outerHTML会根据指定的HTML字符申创建新的DOM子树，然后用这个DOM子树完全替换调用元素。下面是一个例子。
```javascript
<div id="content">
  <p>This is a <strong>paragraph</strong>with a list following it.</p>
  <ul>
       <1i>Item 1</1i><li>Item 2</li><1i>Item 3</li>
  </ul>
</div>
```

使用outerHTL属性以下面这种方式设置值：
```javascript

div.outerHTML="<p>This is a paragraph.</p>"；// 他会取代上面的div标签，成为父标签。
```

3.insertADjacentHTML()方法。  
插入标记的最后一个新增方式是insertAdjacentHTML（）方法。这个方法最早也是在正中出现的，它接收两个参数：插入位置和要插入的HTML文本。第一个参数必须是下列值之一：
* “beforebegin"，在当前元素之前插入一个紧邻的同辈元素；
* “afterbegin·，在当前元素之下插入一个新的子元素或在第一个子元素之前再插入新的子元素；
* “beforeend”，在当前元素之下插入一个新的子元素或在最后一个子元素之后再插入新的子元素；
* “afterend"，在当前元素之后插入一个紧邻的同辈元素。

注意，这些值都必须是小写形式。第二个参数是一个HTML字符串（与innerHTML和outerHTML的值相同），如果浏览器无法解析该字符串，就会抛出错误。以下是这个方法的基本用法示例。

//作为前一个同辈元素插入
`element.insertAdjacentHTML（"beforebegin"，"<p>lHello worldt</p>"）；`

//作为第一个子元素插入
`element.insertAdjacentHTML（"afterbegin"，"<p>Hello world！</p>"）；`

//作为最后一个子元素插入
`element.insertAdjacentHTML（"beforeend"，"<p>Hello world！</p>"）；`

//作为后一个同辈元素插入
`element.insertAdjacentHTML（"afterend"，"<p>Hello world！</p>"）；`



##### scrollIntoView()方法。

```

<html>
	<head>
		<title>HTML5_ScrollInToView方法</title>
		<meta  charset="utf-8">
		<script type="text/javascript">
			window.onload = function(){
				/*
					如果滚动页面也是DOM没有解决的一个问题。为了解决这个问题，浏览器实现了一下方法，
				以方便开发人员如何更好的控制页面的滚动。在各种专有方法中，HTML5选择了scrollIntoView()
				作为标准方法。
					scrollIntoView()可以在所有的HTML元素上调用，通过滚动浏览器窗口或某个容器元素，
				调用元素就可以出现在视窗中。如果给该方法传入true作为参数，或者不传入任何参数，那么
				窗口滚动之后会让调动元素顶部和视窗顶部尽可能齐平。如果传入false作为参数，调用元素
				会尽可能全部出现在视口中（可能的话，调用元素的底部会与视口的顶部齐平。）不过顶部
				不一定齐平，例如：
				//让元素可见
				document.forms[0].scrollIntoView();
				当页面发生变化时，一般会用这个方法来吸引用户注意力。实际上，为某个元素设置焦点也
				会导致浏览器滚动显示获得焦点的元素。
					支持该方法的浏览器有 IE、Firefox、Safari和Opera。
				*/
				
				
				document.querySelector("#roll1").onclick = function(){
					document.querySelector("#roll_top").scrollIntoView(false);
				}
				document.querySelector("#roll2").onclick = function(){
					document.querySelector("#roll_top").scrollIntoView(true);
				}
			}
		</script> 
		<style type="text/css">
			#myDiv{
				height:900px;
				background-color:gray;
				
			}
			#roll_top{
				height:900px;
				background-color:green;
				color:#FFF;
				font-size:50px;
				position:relative;
			}
			#bottom{
				position:absolute;
				display:block;
				left;0;bottom:0;
			}
		</style>
	</head>
	<body>
		<button id="roll1">scrollIntoView(false)</button>
		<button id="roll2">scrollIntoView(true)</button>
		<div id="myDiv"></div>
		<div id="roll_top">
			scrollIntoView(ture)元素上边框与视窗顶部齐平
			<span id="bottom">scrollIntoView(false)元素下边框与视窗底部齐平</span>
		</div> 
	</body>

</html>
```
当页面发生变化时，一般会用这个方法来吸引用户的注意力。实际上，为某个元素设置焦点也会导致浏览器滚动并显示出获得焦点的元素。



### 专有扩展<p id="04"></p>

### :arrow_double_up:<a href="#title">返回目录</a>


##### .2 children属性
这个属性是HTMLCo11ection的实例，只包含元素中同样或者元素的子节点。除此之外，children属性与childNodes没有什么区别，即在元素只包含元素子节点时，这两个属性的值相同。   
下面是访问 children属性的示例代码：
```
var childCount=element.children.length；
var firstchild=element.children[0]；
```

##### .3contains方法
在实际开发中，经常需要知道某个节点是不是另一个节点的后代。IE为此率先引入了contains（）方法，以便不通过在DOM文档树中查找即可获得这个信息。调用contains（）方法的应该是祖先节点，也就是搜索开始的节点，这个方法接收一个参数，即要检测的后代节点。如果被检测的节点是后代节点，该方法返回true；否则，返回false。以下是一个例子：
`alert（document.documentElement.contains（document.body）}；//true`
这个例子测试了<body>元素是不是<htm1>元素的后代，在格式正确的HTL页面中，以上代码返回true。

##### .4插入文本

innerText属性  
* 调用元素的这个属性，会返回他本身及其子节点的文本内容（只有文本内容，没有HTML标签）
* 修改含有子节点元素的这个属性，会直接删除掉其子节点（只是子节点从英文单词便可以看出这一点）。
```
    div. innerText="Hello world!";
```
outerText属性
除了作用范围扩大到了包含调用它的节点之外，outerText与innerText基本上没有多大区别。
在读取文本值时，outerText与innerText的结果完全一样。但在写模式下，outerrext就完全不同了：outerrext不只是替换调用它的元素的子节点，而是会替换整个元素（包括子节点）。比如：

`div.outerrext="Hello world！"；`
这行代码实际上相当于如下两行代码：
```
var text=document.createTextNode（"Hello wor1d！"）；
div.parentNode.replaceChild（text，div）；
```
本质上，新的文本节点会完全取代调用outerText的元素。此后，该元素就从文档中被删除，无法访问。

##### .5滚动(有机会用到再写)

### 总结<p id="05"></p>

### :arrow_double_up:<a href="#title">返回目录</a>

虽然DOM为与XML及HTML文档交互制定了一系列核心API，但仍然有几个规范对标准的DOM进行了扩展。这些扩展中有很多原来是浏览器专有的，但后来成为了事实标准，于是其他浏览器也都提供了相同的实现。本章介绍的三个这方面的规范如下。
* SelectorsAPl，定义了两个方法，让开发人员能够基于CSS选择符从DOM中取得元素，这两个方法是queryselector（）和queryselectorA11（）。
* Element Traversal，为DOM元素定义了额外的属性，让开发人员能够更方便地从一个元素跳到另一个元素。之所以会出现这个扩展，是因为浏览器处理DOM元素间空白符的方式不一样。
* HTML5，为标准的DOM定义了很多扩展功能。其中包括在innerHTML属性这样的事实标准基础上提供的标准定义，以及为管理焦点、设置字符集、滚动页面而规定的扩展API。
虽然目前DOM扩展的数量还不多，但随着Web技术的发展，相信一定还会涌现出更多扩展来。很多浏览器都在试验专有的扩展，而这些扩展一旦获得认可，就能成为“伪”标准，甚至会被收录到规范的更新版本中。
