#                            --------------------- JSON ---------------------

<p id="title"></p>

## 目录

:arrow_down:<a href="#01">语法</a>

:arrow_down:<a href="#02">解析与序列化</a>

:arrow_down:<a href="#03">总结</a>


<p id="01"></p>

<a href="#title">返回目录</a>

### 语法

JSON的语法可以表示以下三种类型的值。
* 简单值：使用与JavaScript相同的语法，可以在JSON中表示字符串、数值、布尔值和nu11。
但JSON不支持JavaScript中的特殊值undefined。
* 对象：对象作为一种复杂数据类型，表示的是一组有序的键值对儿。而每个键值对儿中的值可以是简单值，也可以是复杂数据类型的值。
* 数组：数组也是一种复杂数据类型，表示一组有序的值的列表，可以通过数值索引来访问其中的值。数组的值也可以是任意类型——简单值、对象或数组。
JSON不支持变量、函数或对象实例，它就是一种表示结构化数据的格式，虽然与JavaScript中表示数据的某些语法相同，但它并不局限于JavaScript的范畴。



1.简单值：JSON字符串必须用双引号""（单引号''会导致语法错误）

2.对象：
JSON表示上述对象的方式如下：
```
        {
            "name" : "Nicholas",
            "age": 29
        }

```
属性的值可以是简单值，也可以是复杂类型,在对象属性中嵌套对象。
```
{
    "name":"Nicholas",
    "age":29,
    "school":{
        "name":"Merrimack College",
        "location":"North Andover,MA"
    }
}
```


3.数组：JSON中的第二种复杂数据类型是数组。JSON数组采用的就是JavaScript中的数组字面量形式。例如，下面是JavaScript中的数组字面量：
`var values=[25,"hi",true];`

在JSON中，可以采用同样的语法表示同一个数组：`[25,"hi",true]`

同样要注意，JSON数组也没有变量和分号。把数组和对象结合起来，可以构成更复杂的数据集合。
```
{
  "title":"Professional JavaScript",
  "authors":[
      "Nicholas C. Zakas"
  ],//这就是数组和对象结合。
    edition:3,
    year:2011
}
```

<p id="02"></p>

<a href="#title">返回目录</a>

### 解析与序列化
在将JSON数据结构解析为JavaScript对象后，可以大量减少代码的输入量。如：
`books[2].title`
和
`doc.getElementsByTagName("book")[2].getAttribute("title")` ，他们有同样的效果，但前者的代码量大大减少。

JSON对象有两个方法：stringify（）和parse（）。在最简单的情况下，这两个方法分别用于把JavaScript对象序列化为JSON字符串和把JSON字符串解析为原生JavaScript值。例如：
```javascript
var book={
      title:"Professional Javascript", authors:[
      "Nicholas C. Zakas"
      ],
      edition:3, 
      year:2011
); 
var jsonrext=JsoN. stringify(book);
```
这个例子使用JSoN.stringify（）把一个JavaScript对象序列化为一个JSON字符串，然后将它保存在变量sonrext中。默认情况下，JsoN.stringify（）输出的ISON字符串不包含任何空格字符或缩进，因此保存在sonText中的字符串如下所示：
```
{"title"："Professional JavaScript"，"authors"：["Nicholas C.Zakas"]，“edition"：3，"year"：2011}
```
在序列化JavaScript对象时，所有函数及原型成员都会被有意忽略，不体现在结果中。此外，值为undefined的任何属性也都会被跳过。结果中最终都是值为有效JSON数据类型的实例属性。

```
将JSON字符串直接传递给 JsoN.parse（）就可以得到相应的JavaScript值。例如，使用下列代码就可以创建与book类似的对象：
var bookCopy=JSON.parse（jsonText）；注意，虽然book与bookCopy具有相同的属性，但它们是两个独立的、没有任何关系的对象。
如果传给JSON.parse（）的字符串不是有效的JSON，该方法会抛出错误。
```

#### 序列化选项（传参实现）
实际上，JSON.stringify（）除了要序列化的JavaScript对象外，还可以接收另外两个参数，这两个参数用于指定以不同的方式序列化JavaScript对象。第一个参数是个过滤器，可以是一个数组，也可以是一个函数；第二个参数是一个选项，表示是否在JSON字符串中保留缩进。单独或组合使用这两个参数，可以更全面深入地控制JSON的序列化。

1.过滤结果
```
var book={
“title"："Professional Javascript"，
"authors"：[
    "Nicholas C.Zakas"
],
edition：3，
year：2011
}
var isonText=JsoN.stringify（book，["title"，"edition"l）；
```

`JsoN.stringify（）`的第二个参数是一个数组(那么就只会包含数组中的属性)，其中包含两个字符串：title“和“edition”。这两个属性与将要序列化的对象中的属性是对应的，因此在返回的结果字符串中，就只会包含这两个属性：`{"title"："Professional Javascript"，"edition"：3}`

如果第二个参数是函数，行为会稍有不同。传人的函数接收两个参数，属性（键）名和属性值。根据属性（键）名可以知道应该如何处理要序列化的对象中的属性。属性名只能是字符串，而在值并非键值对儿结构的值时，键名可以是空字符串。

```javascript
var book={
        "title":"Professional Javascript",
        "authors":[
        "Nicholas C. Zakas"
        ],  
        edition:3,
        year:2011
}; 

var jsonText=JSoN. stringify(book, function(key, value){
                switch(key){
                case "authora":
                    return value. join(",")

                case "year":
                    return 5000; 

                 case "edition":
                    return undefined;

                default: return value;
                }
});
```
这里，函数过滤器根据传入的键来决定结果。如果键为“authors”，就将数组连接为一个字符串；如果键为"year"，则将其值设置为5000；如果键为“edition"，通过返回undefined删除该属性。
最后，一定要提供default项，此时返回传人的值，以便其他值都能正常出现在结果中。实际上，第一次调用这个函数过滤器，传人的键是一个空字符串，而值就是book对象。序列化后的JSON字符串如下所示：
`{"title"："Professional JavaScript"，"authors"："Nicholas C.Zakas"，"year"：5000}`

2.字符串缩进

JSON.stringify（）方法的第三个参数用于控制结果中的缩进和空白符。如果这个参数是一个数值，那它表示的是每个级别缩进的空格数。例如，要在每个级别缩进4个空格，可以这样写代码：
```javacript
var book={
  "title"："Professional Javascript"，  
  "authors"：[
    "Nicholas C.Zakas"
  ]，
  edition：3，
  year：2011
}
  var jsonText=JsoN. stringify(book, null,4);
```

缩进后看起来没有变化，是因为一开始就有4个缩进

```javascript
  "title":"Professional Javascript",
  "authors":[
    "Nicholas C. Zakas"
  ],
  "edition":3,
  "year":2011
```


缩进会自动添加换行符，最大缩进空格数为10，所有大于10的值都会自动转换成10

如果缩进参数是一个字符串而非数值，则这个字符串将在JSON字符串中被用作缩进字符（不再使用空格）。在使用字符串的情况下，可以将缩进字符设置为制表符，或者两个短划线之类的任意字符。
```javascript
var jsonText=JsoN.stringify（book，null，"--"）；这样，sonText中的字符串将变成如下所示：
{
--"title"："Professional JavaScript"，
--"authors"：[
--—-"Nicholas C.Zakas"
--]
"edition"：3，
--"year"：2011
}
```

缩进字符串最长不能超过10个字符长。如果字符串长度超过了10个，结果中将只出现前10个字符。


3.toJSON方法
```javscript
var book={
"title":"Professional Javascript",
"authors":[
"Nicholas C. Zakas"
]
edition:3, 
year:2011, 
  toJSON: function(){
        return this. title;
}; 

var isonText=JsoN. stringify(book);
```

以上代码在book对象上定义了一个toJsoN（）方法，该方法返回图书的书名。与pate对象类似，这个对象也将被序列化为一个简单的字符串而非对象。可以让toJSON（）方法返回任何序列化的值，它都能正常工作。也可以让这个方法返回undefined，此时如果包含它的对象嵌入在另一个对象中，会导致该对象的值变成nu11，而如果包含它的对象是顶级对象，结果就是undefined。

toJSON（）可以作为函数过滤器的补充，因此理解序列化的内部顺序十分重要。假设把一个对象传入JsoN.stringify（），序列化该对象的顺序如下。
* （1）如果存在toJSoN（）方法而且能通过它取得有效的值，则调用该方法。否则，按默认顺序执行序列化。
* （2）如果提供了第二个参数，应用这个函数过滤器。传入函数过滤器的值是第（1）步返回的值。
* （3）对第（2）步返回的每个值进行相应的序列化。
* （4）如果提供了第三个参数，执行相应的格式化。
无论是考虑定义toJSON（）方法，还是考虑使用函数过滤器，亦或需要同时使用两者，理解这个顺序都是至关重要的。




#### 解析选项
JSoN.parse（）方法也可以接收另一个参数，该参数是一个函数，将在每个键值对儿上调用。为了区别JsoN.stringify（）接收的替换（过滤）函数（replacer），这个函数被称为还原函数（reviver），但实际上这两个函数的签名是相同的——它们都接收两个参数，一个键和一个值，而且都需要返回一个值。
如果还原函数返回undefined，则表示要从结果中删除相应的键；如果返回其他值，则将该值插入到结果中。在将日期字符串转换为Date对象时，经常要用到还原函数。例如：
```javascript
var book={
        "title":"Professional Javascript",
        "authors":[
            "Nicholas C. Zakas"
        ],
          edition:3,
          year:2011, 
          releaseDate: new Date(2011,11,1)
        };
        
        var jsonrext=JsoN. stringify(book); var bookcopy=asoN. parae(jeongext, function(key, value){
        if(key == "releageDate"){
            return new Date(value);
        }
         else{
             return value;
        }
        }); 

    alert(bookCopy. releaseDate. getFullYear());
```
以上代码先是为book对象新增了一个releaseDate属性，该属性保存着一个Date对象。这个对象在经过序列化之后变成了有效的JSON字符串，然后经过解析又在bookCopy中还原为一个Date对象。还原函数在遇到"releaseDate"键时，会基于相应的值创建一个新的 Date对象。结果就是bookCopy.releaseDate属性中会保存一个Date对象。正因为如此，才能基于这个对象调用getFu11year（）方法。

<p id="03"></p>

### 总结

<a href="#title">返回目录</a>

JSON是一个轻量级的数据格式，可以简化表示复杂数据结构的工作量。JSON使用JavaScript语法的子集表示对象、数组、字符串、数值、布尔值和nu11。即使XML也能表示同样复杂的数据结果，但JSON没有那么烦琐，而且在JavaScript中使用更便利。
ECMAScript5定义了一个原生的JsoN对象，可以用来将对象序列化为JSON字符串或者将 JSON数据解析为JavaScript对象。JsON.stringify（）和JsoN.parse（）方法分别用来实现上述两项功能。
这两个方法都有一些选项，通过它们可以改变过滤的方式，或者改变序列化的过程。




