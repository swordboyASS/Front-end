# --------------------- Ajax与Comet -----------------

## 目录

<p id="title"></p>


:arrow_down:<a href="#01">XMLHttpRequest对象</a>

:arrow_down:<a href="#02">XMLHttpRequest 2级</a>

:arrow_down:<a href="#03">进度事件</a>

:arrow_down:<a href="#04">跨源资源共享</a>

:arrow_down:<a href="#05">其他跨域技术</a>

:arrow_down:<a href="#06">安全</a>

:arrow_down:<a href="#07">总结</a>


<p id="01"></p>

:arrow_double_up:<a href="#title">返回目录</a>

### XMLHttpRequest对象


```javascript
    <script type="text/javascript">
        var xhr = new XMLHttpRequest();//创建XMLHttpRequest对象
        /*
            在使用XHR对象时，要调用的第一个方法是open（），
            它接受3个参数：要发送的请求的类型（“get"、"postn等）、请求的URL和表示是否异步发送请求的布尔值。
            但这并不是真正的发送请求，而是，启动一个请求以备发送。
        */
        xhr.open("get","examp.php",false);//发送GET请求，第二个参数是请求的URL，同步执行。
        xhr.send(null);//将上面的get请求发送，最好为send方法传一个null参数。
    </script>
```

 由于这次请求是同步的，JavaScript代码会等到服务器响应之后再继续执行。在收到响应后，响应的数据会自动填充XHR对象的属性，相关的属性简介如下。
* responseText：作为响应主体被返回的文本。
* responsext：如果响应的内容类型是“text/xm1或“application/xm1，这个属性中将保存包含着响应数据的XMLDOM文档。
* status：响应的HTTP状态。
* statusrext:HTTP状态的说明。

HTTP状态码如下，在这个条件下，就是响应已经成功返回：
```javacript
        if(xhr.status>=200 && xhr.status<300 || xhr.status == 304){
            alert(xhr.responseText);
        } else{
            alert("faild"+xhr.status);
        }
```

但多数情况下，我们还是要发送异步请求，才能让JavaScript继续执行而不必等待相应。那么此时就检测XHR对象的readyState属性：
* 0：未初始化。尚未调用open（）方法。
* 1：启动。已经调用open（）方法，但尚未调用send（）方法。
* 2：发送。已经调用send（）方法，但尚未接收到响应。
* 3：接收。已经接收到部分响应数据。
* 4：完成。已经接收到全部响应数据，而且已经可以在客户端使用了。

只要readystate 属性的值由一个值变成另一个值，都会触发一次 readystatechange事件。可以利用这个事件来检测每次状态变化后readystate的值。通常，我们只对readystate值为4的阶段感兴趣，因为这时所有数据都已经就绪。不过，必须在调用open（）之前指定onreadystatechange事件处理程序才能确保跨浏览器兼容性。下面来看一个例子。
```javascript
        xhr.open("get","examp.php",true);
        xhr.onreadystatechange = function(){
            if(xhr.readyState==4){
                    if(xhr.status>=200 && xhr.status<300 || xhr.status == 304){
                alert(xhr.responseText);
            } else{
                alert("faild"+xhr.status);
            }
            
            }
        }
```

在接收到响应之前可以调用abort（）方法来取消异步请求：
`xhr.abort()`

##### HTTP头部信息
后面再写。


#### GET请求
GET请求时最常见的请求类型，用于向服务器查询某些信息。


#### POST请求
通常用于向服务器发送应该被保存的数据。发送的数据没有大小限制，而GET请求有。

<p id="02"></p>

:arrow_double_up:<a href="#title">返回目录</a>

### XMLHttpRequest 2级


FormData：用于表单数据序列化


##### 超时设定
IE8为XHR对象添加了一个timeout属性，表示请求在等待响应多少毫秒之后就终止。在给timeout 设置一个数值后，如果在规定的时间内浏览器还没有接收到响应，那么就会触发timeout事件，进而会调用ontimeout事件处理程序。这项功能后来也被收入了XMLHttpRequest2级规范中。来看下面的例子。
```javascript
        xhr.open("get","example.php",true)
        xhr.timeout = 1000;
        xhr.ontimeout = function(){
            alert("timeout!");
        };
        xhr.send(null);
```








<p id="03"></p>

:arrow_double_up:<a href="#title">返回目录</a>


### 进度事件
* loadstart：在接收到响应数据的第一个字节时触发。
* progress：在接收响应期间持续不断地触发。
* error：在请求发生错误时触发。
* abort：在因为调用abort（）方法而终止连接时触发。
* 1oad：在接收到完整的响应数据时触发。
* 1oadend：在通信完成或者触发error、abort或load事件后触发。  
每个请求都从触发1oadstart事件开始，接下来是一或多个progress事件，然后触发error、abort或load事件中的一个，最后以触发1oadend事件结束。


1. load事件

load事件只用于替换readystatechange事件,差别不大
```javascript
var xhr=createXHR(); xhr, onload=function(){
if((xhr. statu8 >= 200&& xhr, Btatus<300) ll xhr. atatus ==304)(
alert(xhr. responseText);
] else{
alert("Request was unsucceasful:"+xhr. status);
}
}; xhr. open("get","altevents. php", true); xhr. send(null);

<p id="04"></p>
```


2.progress事件
Mozilla对XHR的另一个革新是添加了progress事件，这个事件会在浏览器接收新数据期间周期性地触发。而onprogress事件处理程序会接收到一个event对象，其target属性是XHR对象，但包含着三个额外的属性：1engthcomputable、position 和totalsize。其中，1engthComputable是一个表示进度信息是否可用的布尔值，position表示已经接收的字节数，totalsize表示根据Content-Length响应头部确定的预期字节数。有了这些信息，我们就可以为用户创建一个进度指示器了。下面展示了为用户创建进度指示器的一个示例。

```javascript
        var xhr=createXHR(); 
        xhr. onload=function(event){
            if((xhr. status >=200 && xhr. status< 300) || xhr. status==304){
            alert(xhr. responseText);
            } else{
            alert("Request was unsuccessful:"+xhr. status);
            }   
        }; 
        //再open方法之前调用
        xhr. onprogress= function(event){
                var divstatug = document. getElementById("statua"); 
                if(event.lengthComputable){
                divstatua. innerHTML="Received"+event. pogltion +"of"+event. totalsize +"bytes";
                }
        }; 
        xhr. open("get","altevents. php", true); 
        xhr. send(nul1);
```







<p id="04"></p>

:arrow_double_up:<a href="#title">返回目录</a>

### 跨源资源共享
1.跨域概念

      因为跨域问题是浏览器对于ajax请求的一种安全限制：一个页面发起的ajax请求，只能是于当前页同域名的路径，这能有效的阻止跨站攻击。因此：跨域问题 是针对ajax的一种限制。

【解决跨域问题的方法】

 1.1、Jsonp最早的解决方案，利用script标签可以跨域的原理实现。
  限制：
  （1）需要服务的支持；
  （2）只能发起GET请求；

1.2、nginx反向代理

    思路是：利用nginx反向代理把跨域为不跨域，支持各种请求方式；
    缺点：需要在nginx进行额外配置，语义不清晰。

1.3、CORS  规范化的跨域请求解决方案，安全可靠。
  优势：
  -（1）在服务端进行控制是否允许跨域，可自定义规则；
  （2）支持各种请求方式；
  缺点： 会产生额外的请求；

2.cors概念

     CORS是一个W3C标准，全称是"跨域资源共享"（Cross-origin resource sharing）。它允许浏览器向跨源服务器，发出XMLHttpRequest请求，从而克服了AJAX只能同源使用的限制。CORS需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能，IE浏览器不能低于IE10。
（1）浏览器端：  目前，所有浏览器都支持该功能（IE10以下不行）。整个CORS通信过程，都是浏览器自动完成，不需要用户参与。   
（2） 服务端：  CORS通信与AJAX没有任何差别，因此你不需要改变以前的业务逻辑。只不过，浏览器会在请求中携带一些头信息，我们需要以此判断是否运行其跨域，然后在响应头中加入一些信息即可。这一般通过过滤器完成即可。   

2.1、简单请求

只要同时满足以下两大条件，就属于简单请求。

（1) 请求方法是以下三种方法之一：
* HEAD
* GET
* POST
（2）HTTP的头信息不超出以下几种字段：
* Accept
* Accept-Language
* Content-Language
* Last-Event-ID
* Content-Type：只限于三个值application/x-www-form-urlencoded、multipart/form-data、text/plain   
当浏览器发现发现的ajax请求是简单请求时，会在请求头中携带一个字段：Origin.

     Origin中会指出当前请求属于哪个域（协议+域名+端口）。服务会根据这个值决定是否允许其跨域。如果服务器允许跨域，需要在返回的响应头中携带下面信息：

Access-Control-Allow-Origin: http://manage.wzy.com  
Access-Control-Allow-Credentials: true  
Content-Type: text/html; charset=utf-8   
ccess-Control-Allow-Origin：可接受的域，是一个具体域名或者\*，代表任意；   

Access-Control-Allow-Credentials：是否允许携带cookie，默认情况下，cors不会携带cookie，除非这个值是true。

注意：如果跨域请求要想操作cookie，需要满足3个条件：  
（1） 服务的响应头中需要携带Access-Control-Allow-Credentials并且为true；  
（2） 浏览器发起ajax需要指定withCredentials 为true；  
 (3) 响应头中的Access-Control-Allow-Origin一定不能为\*，必须是指定的域名。  

2.2、特殊请求

      不符合简单请求的条件，会被浏览器判定为特殊请求,，例如请求方式为PUT。特殊请求会在正式通信之前，增加一次HTTP查询请求，称为"预检"请求（preflight）。浏览器先询问服务器，当前网页所在的域名是否在服务器的许可名单之中，以及可以使用哪些HTTP动词和头信息字段。只有得到肯定答复，浏览器才会发出正式的XMLHttpRequest请求，否则就报错。
一个“预检”请求的样板：
```
OPTIONS /cors HTTP/1.1
Origin: http://manage.leyou.com
Access-Control-Request-Method: PUT
Access-Control-Request-Headers: X-Custom-Header
Host: api.leyou.com
Accept-Language: en-US
Connection: keep-alive
User-Agent: Mozilla/5.0...
```
与简单请求相比，除了Origin以外，多了两个头：

Access-Control-Request-Method：接下来会用到的请求方式，比如PUT；

Access-Control-Request-Headers：会额外用到的头信息。

服务的收到预检请求，如果许可跨域，会发出响应（也就是预请求的响应）：  
```
HTTP/1.1 200 OK
Date: Mon, 01 Dec 2008 01:15:39 GMT
Server: Apache/2.0.61 (Unix)
Access-Control-Allow-Origin: http://manage.wzy.com
Access-Control-Allow-Credentials: true
Access-Control-Allow-Methods: GET, POST, PUT
Access-Control-Allow-Headers: X-Custom-Header
Access-Control-Max-Age: 1728000
Content-Type: text/html; charset=utf-8
Content-Encoding: gzip
Content-Length: 0
Keep-Alive: timeout=2, max=100
Connection: Keep-Alive
Content-Type: text/plain
```
 除了Access-Control-Allow-Origin和Access-Control-Allow-Credentials以外，这里又额外多出3个头：

Access-Control-Allow-Methods：允许访问的方式；

Access-Control-Allow-Headers：允许携带的头；

Access-Control-Max-Age：本次许可的有效时长，单位是秒，过期之前的ajax请求就无需再次进行预检。








<p id="05"></p>

:arrow_double_up:<a href="#title">返回目录</a>

### 其他跨域技术




<p id="06"></p>

:arrow_double_up:<a href="#title">返回目录</a>


### 安全



<p id="07"></p>

:arrow_double_up:<a href="#title">返回目录</a>

### 总结
