### <script>元素
向HTML页面中插入JavaScript的主要方法，就是使用<script>元素。这个元素由Netscape创造并在Netscape Navigator2中首先实现。后来，这个元素被加入到正式的HTML规范中。HTML4.01为  <script>定义了下列6个属性:  
* async：可选。表示应该立即下载脚本，但不应妨碍页面中的其他操作，比如下载其他资源或等待加载其他脚本。只对外部脚本文件有效。
* charset：可选。表示通过src属性指定的代码的字符集。由于大多数浏览器会忽略它的值，因此这个属性很少有人用。
* defer：可选。表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。IE7及更早版本对嵌入脚本也支持这个属性。
* 1anguage：已废弃。原来用于表示编写代码使用的脚本语言（如JavaScript、JavaScript1.2或vBScript）。大多数浏览器会忽略这个属性，因此也没有必要再用了。
* src：可选。表示包含要执行代码的外部文件。
* type：可选。可以看成是language的替代属性；表示编写代码使用的脚本语言的内容类型（也称为MIME类型）。虽然text/javascript和text/ecmascript都已经不被推荐使用，但人们一直以来使用的都还是text/javascript。实际上，服务器在传送JavaScript文件时使用的MIME类型通常是application/x-javascript，但在type中设置这个值却可能导致脚本被忽略。另外，在非IE浏览器中还可以使用以下值：application/javascript和application/,考虑到约定俗成和最大限度的浏览器兼容性，日前type属性的值依旧还是text/javascript。不过，这个属性并不是必需的，如果没有指定这个属性，则其默认值仍为text/javascript。
  
使用`<script>`元素有两种方式：在页面中嵌入js代码和外部引入文件：  
  嵌入代码:
```Javascript
<script type="text/javascript">
function sayHi()(
alert("Hi!");
</script>
```
引入文件：
```javascript
<script type="text/javascript"src="example.js"></script>
```
### !注意
```
不要再代码的任何地方出现</script>字符串，不然会和<script>开始标签匹配，导致出现错误，
但如果硬要出现</script>字符串，可以使用'\'转义字符，<\/script>。
另外，如何外部使用外部引入文件的方式，就不要再两个script标签中添加嵌入式代码，因为添加代码也是冗余的，浏览器会自动忽略该部分代码
```
### 标签的位置
传统的做法是将<script>标签放在head部分，但随之而来的问题则是，当有大量的js代码时，会出现延迟的情况，此时浏览器会等待js代码下在完毕
才开始加载HTML界面，此时浏览器一片空白，用户体验差。  
* 第一个解决方法：将js引入放在<body>标签最后：
  
```html
  <！DOCTYPE html>
<html><head>
<title>Example HTML Page</title>
</head>
<body>
<！--这里放内容-->
<acript type="text/javascript"src="example1.ja"></script><script type="text/javascript"arc="example2.J8"></script>
</body></html>
```
* 另一个解决方法：

为<script>标签添加“defer”属性，这相当于告诉浏览器立即下载，但延迟执行，先加载HTML界面，再下载脚本，  

```html
  <！DOCTYPE html>
<html><head>
<title>Example HTML Page</title>
<script type="text/javascript"defer="defer"arc="example1.j8"></script>
<script type="text/javascript"defer="defer"arc="example2.J8"></script>
 <b>第二个js标签会迟于第一个下载</b>
</head>
<body>
<l--这里放内容-->
</body>
```
* 最后一个解决方法

为<script>标签定义ascny（异步）属性,这个属性与defer类似，也只适用于外部文件，但不同的是<script>元素的执行顺序是随机的

```html
<！DOCTYPE html>
<htm1><head>
<title>Example HTML Page</title>
<ecript type="text/javascript"aaync arc="example1.js"></script>
<8cxipt type="text/javagcript"async src="example2.ja"></acript>
</head>
<body>
<--这里放内容->
</body></html>
```  
### 嵌入代码与外部文件
在HTML中嵌入JavaScript代码虽然没有问题，但一般认为最好的做法还是尽可能使用外部文件来包含JavaScript代码。不过，并不存在必须使用外部文件的硬性规定，但支持使用外部文件的人多会强调如下优点。   
* 可维护性：遍及不同HTML页面的JavaScript会造成维护问题。但把所有JavaScript文件都放在一个文件夹中，维护起来就轻松多了。而且开发人员因此也能够在不触及HTML标记的情况下，集中精力编辑JavaScript代码。
* 可缓存：浏览器能够根据具体的设置缓存链接的所有外部 JavaScript文件。也就是说，如果有两个页面都使用同一个文件，那么这个文件只需下载一次。因此，最终结果就是能够加快页面加载的速度。
* 适应未来：通过外部文件来包含JavaScript无须使用前面提到XHTML或注释hack。HTML和XHTML包含外部文件的语法是相同的。

### `<noscript>`元素

早期浏览器都面临一个特殊的问题，即当浏览器不支持JavaScript时如何让页面平稳地退化。对这个问题的最终解决方案就是创造一个`<noscript>`元素，用以在不支持JavaScript的浏览器中显示替代的内容。这个元素可以包含能够出现在文档`<body>`中的任何HTML元素—`<script>`元素除外。包含在`<noscript>`元素中的内容只有在下列情况下才会显示出来：
* 浏览器不支持脚本；
* 浏览器支持脚本，但脚本被禁用。
符合上述任何一个条件，浏览器都会显示`<noscript>`中的内容。而在除此之外的其他情况下，浏览器不会呈现`<noscript>`中的内容。
请看下面这个简单的例子：

```html
<html><head>
<title>Example HTML Page</title>
<script type="text/javascript"defer="defer"src="examplel.js"></script>
<script type="text/javascript"defer="defer"src=*example2.js*></script>
</head>
<body>
<noscript>
<p>本页面需要浏览器支持（启用）Javascript。
</noacript>
</body></html>
```
这个页面会在脚本无效的情况下向用户显示一条消息。而在启用了脚本的浏览器中，用户永远也不会看到它——尽管它是页面的一部分。

## 小结
把JavaScript 插入到HTML页面中要使用`<script>`元素。使用这个元素可以把JavaScript嵌入到HTML页面中，让脚本与标记混合在一起；也可以包含外部的JavaScript文件。而我们需要注意的地方有：
* 在包含外部 JavaScript文件时，必须将src属性设置为指向相应文件的URL。而这个文件既可以是与包含它的页面位于同一个服务器上的文件，也可以是其他任何域中的文件。
* 所有`<script>`元素都会按照它们在页面中出现的先后顺序依次被解析。在不使用defer和async属性的情况下，只有在解析完前面`<script>`元素中的代码之后，才会开始解析后面`<script>`元素中的代码。
* 由于浏览器会先解析完不使用defer属性的`<script>`元素中的代码，然后再解析后面的内容，所以一般应该把`<script>`元素放在页面最后，即主要内容后面，`</body>`标签前面。
* 使用defer属性可以让脚本在文档完全呈现之后再执行。延迟脚本总是按照指定它们的顺序执行。
* 使用async属性可以表示当前脚本不必等待其他脚本，也不必阻塞文档呈现。不能保证异步脚本按照它们在页面中出现的顺序执行。  
另外，使用`<noscript>`元素可以指定在不支持脚本的浏览器中显示的替代内容。但在启用了脚本的情况下，浏览器不会显示`<noscript>`元素中的任何内容。
