>什么是服务器
>>网页浏览过程分析
>>如何配置自己的服务器程序（AMP）
```
<！-—基本概念
1..什么是服务器？
服务器也是电脑，只不过是一台24小时不断电，不关机的电脑
>根据提供的服务功能不同：文件服务器、邮件服务器、Web服务器等等；
>简而言之：服务器其实就是一台"提供了某种服务功能”的超级电脑

2.如何让电脑能够提供某种服务？
>如何让电脑可以聊天？听歌？浏览网页？
>想让电脑提供聊天服务，可以安装相应的聊天软件，例如：QQ/旺旺.…>想让电脑可以提供听歌服务，可以安装相应音乐软件，例如：酷我/酷狗.
>想让电脑可以提供浏览网页服务，可以安装相应浏览网页软件，例如：谷歌/欧朋.

3.如何让电脑提供管理网站的服务？
>安装Web服务相关软件，例如：Apache、IIS、Tomcat、Nginx、NodeJS等；
>安装了Web服务软件的电脑，我们称之为"Web服务器"
>Web服务器软件：Apache、IIS、Tomcat、Nginx、NodeJS等；

<！--Web服务器搭建
1.什么是WAMPServer软件？
W:Windows操作系统
h:Arache 世界排名第一的服务器软件，特点是简单，速度快，性能稳定
M:MySQL开源免费的数据库软件，特点是体积小、速度快、使用成本低
P:PHP超文本预处理器，直接将代码嵌入HTML文档中执行，特点是简单易学，容易上手
```

`>什么是Ajax
>>无刷新数据读取
>>用户注册、在线聊天室
>>异步、同步`

#### php基础语法
* 服务器后端语言必须放在服务器对应的文件夹下，不能直接运行，必须通过浏览器=》找到服务器=》服务器对应的文件夹=》文件夹中对应的文件
？如何通过服务器运行，通过ip地址找到服务器对应的文件夹，然后再找到对应的文件夹运行。
！(;)用于结束语句的分号是必须的。

```
//1.注释方法和js一样
//和 /* */ 

//2.JS中如何定义变量？  var num = 10;
$num = 10;

//3.JS中如何打印内容？
echo $num(echo和console.WriteLine()功能相同，都不能输出集合，必须通过遍历输出)
http://127.0.0.1/Untitled-1.php

echo("666"); 等同于 echo "666";

//4.JS中如何定义集合
//4.1数组  var arr=[];
$arr=array(1,3,5);

//4.2字典（对象）
$trr = array("name"=>"gaoju","age"=>"19");  //定义一个字典
print_r($trr);    //输出字典所有内容。
echo("<br>"); 
echo($trr["name"]);   //输出字典的键的单个值。


//5.JS中如何获取集合的值？
echo($trr["name"]);   //输出字典的键的单个值。

//6.JS中的分支循环语句
//if/switch/三目/for/while

//if和 js相同。

//switch相同


//三目也和 js一样
$sum = $num>10?100:50;

echo($sum); //50

//for  //有count(数组名)方法,没有length属性。
$arr = array(1,3,5);
for($i = 0;$i < count($arr); $i++)
{
    echo ($arr[$i]);
    echo ("<br>");
}

//while 循环
$arr = array(1,3,5);
$index = 0;
while($index<count($arr))
{
    echo($arr[$index]);
    echo("<br>");
    $index++;
}

```


### get请求处理
get请求会将表单提交信息直接显示在浏览器url上,像下面这个？后面的内容就是input的name属性+用户输入的信息。
` http://127.0.0.1/02.php?userName=213&userPwd=123`



![](https://github.com/swordboyASS/JavaScript./blob/master/%E5%AE%9E%E6%88%98/01.png)

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <form action="02-post.php" method="get">
        <input type="text" name="userName"><br>
        <input type="password" name="userPwd"><br>
        <input type="submit" value="提交"><br>
    </form>
</body>
</html>
```

```php
<?php
print_r($_GET);
echo ($_GET["userName"]);
echo ($_GET["userPwd"]);
?>
```


### post请求
![post图片](https://github.com/swordboyASS/JavaScript./blob/master/%E5%AE%9E%E6%88%98/picture/post.png)


### get-post异同
```
1.可以通过form标签的method属性指定发送请求的类型  
2.如果是get请求会将提交的数据拼接到URL后面   
？userName=1n j&userPwd=1234563.    
如果是post请求会将提交的数据放到请求头中  

4.GET请求和POST请求的异同
4.1相同点：
都是将数据提交到远程服务器

4.2不同点：
4.2.1提交数据存储的位置不同GET请求会将数据放到URL后面POST请求会将数据放到请求头中
4.2.2提交数据大小限制不同GET请求对数据有大小限制


POST请求对数据没有大小限制
5.GET/POST请求应用场景GET请求用于提交非敏感数据和小数据POST请求用于提交敏感数据和大数据
```

### post文件上传

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <p>重点在于form的`enctype="multipart/form-data"`属性，有了它才能上传文件</p>
    <form action="03-postfile.php" method="post"  enctype="multipart/form-data">
        <input type="file" name="file1"><br>
        <input type="submit" value="上传">
    </form>
</body>
</html>
```

```php
<?php

// echo "post page";

// print_r($_FILES);
// $fileInfo = $_FILES["upfile"];

//1.获取上传文件对应的字典。
$fileInfo = $_FILES["file1"];
// print_r($fileInfo);

//2.获取上传文件的名称，该名称即代表了该文件
$fileName = $fileInfo["name"]; echo("<br>");
// print_r($fileName); 

//3.获取上传文件的临时（tmp）路径。
$filePath = $fileInfo["tmp_name"];echo("<br>");
// print_r($filePath);  

//4.移动并保存文件。 通过上面的3个步骤得到的只是一个临时文件，必须通过第四步保存下来才能在文件夹中看到上传的文件。
move_uploaded_file($filePath,"./source/".$fileName);  //move_uploaded_file()，这个方法的第一个参数是临时文件的路径，第二个参数
?>
```



### AJAX-get基本使用


```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script>
        window.onload  =function(ev)
        {
            var oBtn = document.querySelector("button");
            oBtn.onclick  = function(ev1){
                //1.创建一个异步对象
                var xmlhttp  = new XMLHttpRequest();
                //2.设置请求方式和请求地址
                xmlhttp.open("GET","04-ajax-get.php",true);
                            /* 规定请求
                            open(method, url, async, user, psw)
                             method：请求类型 GET 或 POST
                             url：文件位置
                             async：true（异步）或 fa lse（同步）
                             user：可选的用户名称
                             psw：可选的密码 
                            */
                //3.发送请求
                xmlhttp.send();
                //4.监听状态的变化(状态发生变化就会执行这个回调函数)
                xmlhttp.onreadystatechange = function(ev2){
                //5.处理返回的结果
                    if(xmlhttp.readyState===4){
                        /*
                            0: 请求未初始化
                            1: 服务器连接已建立
                            2: 请求已接收
                            3: 请求处理中
                            4: 请求已完成，且响应已就绪
                        */
                        //http状态码，大于等于200，小于等于300 或者等于304就是发送请求成功。
                        if(xmlhttp.status>=200 && xmlhttp.status<=300 || xmlhttp.status===304){
                            console.log("接收到服务器返回的数据");
                        }else{
                            console.log("没有接收到服务器返回的数据");
                        }
                    }
                }
            }
        }
    </script>
</head>
<body>
    <!--什么是Ajax
        AJAX是与服务器交换数据并更新部分网页的艺术，在不重新加载整个界面的情况下。
    -->
    <button>发送请求</button>
</body>
</html>
```


### IE兼容问题

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script>
        window.onload = function(ev)
        {
            var oBtn = document.querySelector("button");

                        oBtn.onclick = function(ev1)
                        {
                            var xhr;
                if (window.XMLHttpRequest)
                {// code for IE7+, Firefox, Chrome, Opera, Safari
                    xhr=new XMLHttpRequest();
                }
                else
                {// code for IE6, IE5
                    xhr=new ActiveXObject("Microsoft.XMLHTTP");
                }

                // var xhr = new XMLHttpRequest();
                /* 
                
                    在IE浏览器中，如果通过Ajax发送GET请求，那么IE浏览器认为同一个URL只有一个结果。
                    意味着，IE会保存第一次的结果，之后再修改那个文件IE不会更新。（自动缓存）    
                */

                 //给URL传递一个参数，保证每次URL不一样，兼容IE,为ULR添加参数不影响，URL的地址。
                xhr.open("GET","jrie.txt?t="+(new Date().getTime()),true);
                xhr.send();
                xhr.onreadystatechange = function (ev2)
                {
                        if(xhr.readyState===4)
                        {
                            if(xhr.status>=200 && xhr.status<=300 || xhr.status===304)
                            {
                                // alert("提交请求成功！");
                                alert(xhr.responseText);
                            }
                            else
                            {
                                alert("提交请求失败！");
                            }
                        }
                }
            }
        }
    </script>
</head>
<body>
    <button>提交请求</button>
</body>
</html>
```


### GET封装
##### html文件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="GET封装.js"></script>
    <script>
        window.onload = function(ev)
        {
            var oBtn = document.querySelector("button");
            oBtn.onclick = function(ev1)
            {
                ajax("GET封装.php",
                {
                    "userName":"gaoju",
                    "userPwd":"123456"
                },3000,  //设置超时时间。
                function(xhr){
                     alert(xhr.responseText);
                },
                function(xhr){
                    alert("open faild!");
                }

                )
            }
        }
    </script>
</head>
<body>
    <button>发送请求</button>
</body>
</html>
```

##### JavaScript文件
```javascript
function objtostr(obj)
{

    /*
        {
            "userName":"goaju",
            "userPwd":"123456",
            "t":"32423435435" 一串随机的数字
        }
    */

    var res=[];
    obj.t = new Date().getTime();
    for(var key in obj)
    {
        //在URL中时不能出现中文的，所以用下面的方法转换成Unicode码
        //encodeURIComponent()方法转码
        //URL中只能出现：数字/字母/下划线/ASCII码
        res.push(encodeURIComponent(key)+"="+encodeURIComponent(obj[key]));  //[userName=gaoju,suerPwd=123456，t=213123123];
    }
    return res.join("&");//[userName=gaoju&suerPwd=123456&t=123123123];
}

function ajax(url,obj,timeout,success,error)
{

        var str = objtostr(obj);
            var xhr,timer;
            if (window.XMLHttpRequest)
            {// code for IE7+, Firefox, Chrome, Opera, Safari ,用于高版本的浏览器。
                xhr=new XMLHttpRequest(); 
            }
            else
            {// code for IE6, IE5  ,   用于支持低版本的IE
                xhr=new ActiveXObject("Microsoft.XMLHTTP");
            }
            
            //从开始请求到结束，有5个步骤

            //请求php文件
            // xhr.open("get","GET封装.php",true);

            //请求文本文件
            //给URL传递一个参数，保证每次URL不一样，兼容IE
            //1.设置请求方式
            xhr.open("get",url+"?"+str,true);

            //2.发送请求
            xhr.send(null);

            //3.监听请求状态事件，每次变化都会触发这个事件
            xhr.onreadystatechange = function(ev2) //这是一个回调函数
            {
                //4.判断请求状态码，4表示请求完成，
                if(xhr.readyState==4)
                {
                    clearInterval(timer);// 删除定时器。
                    //5.判断HTTP状态码
                    if(xhr.status>=200 && xhr.status<300||xhr.status==304)
                    {
                        // alert(xhr.responseText);
                        success(xhr);
                    }
                    else
                    {
                        // alert("请求成功");
                        error(xhr);
                    }
                }
            }
        


        //判断外界是否传入了超时时间。  
        if(timeout){
            timer = setInterval(function(){
                console.log("中断请求");
                xhr.abort();
                clearInterval(timer);
            },timeout)  //一到超时时间，就会执行这个回调函数。
        }


    
}
```


##### php文件
```php
   <?php
    //这里面的内容就是要返回给前端的异步对象的responsText属性。
    sleep(5);//暂停5s
    echo $_GET["userName"];
    echo "<br>";  
    echo $_GET["userPwd"];
?> 
```



### POST封装
如果需要像 HTML 表单那样 POST 数据，请使用 setRequestHeader() 来添加 HTTP 头。然后在 send() 方法中规定您希望发送的数据：
```javascript
xmlhttp.open("POST","ajax_test.asp",true);
xmlhttp.setRequestHeader("Content-type","application/x-www-form-urlencoded");
xmlhttp.send("fname=Bill&lname=Gates");
```


##### HTML文件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="POST封装.js"></script>
    <script>
        window.onload =function()
        {
            var oBtn = document.querySelector("button");
            oBtn.onclick =function()
            {
                ajax("post","POST封装.php",
                {
                    "userName":"gaoju",
                    "userPwd":"654321"
                },3000,  //设置超时时间。
                function(xhr){
                     alert(xhr.responseText);
                },
                function(xhr){
                    alert("open faild!");
                }

                )
            }
        }
    </script>
</head>
<body>
    <button>发送请求</button>
</body>
</html>
```

##### JavaScript文件
```javascript
function objtostr(obj)
{

    /*
        {
            "userName":"goaju",
            "userPwd":"123456",
            "t":"32423435435" 一串随机的数字
        }
    */

    var res=[];
    obj.t = new Date().getTime();
    for(var key in obj)
    {
        //在URL中时不能出现中文的，所以用下面的方法转换成Unicode码
        //encodeURIComponent()方法转码
        //URL中只能出现：数字/字母/下划线/ASCII码
        res.push(encodeURIComponent(key)+"="+encodeURIComponent(obj[key]));  //[userName=gaoju,suerPwd=123456，t=213123123];
    }
    return res.join("&");//[userName=gaoju&suerPwd=123456&t=123123123];
}

function ajax(type,url,obj,timeout,success,error)
{

        var str = objtostr(obj);
            var xhr,timer;
            if (window.XMLHttpRequest)
            {// code for IE7+, Firefox, Chrome, Opera, Safari ,用于高版本的浏览器。
                xhr=new XMLHttpRequest(); 
            }
            else
            {// code for IE6, IE5  ,   用于支持低版本的IE
                xhr=new ActiveXObject("Microsoft.XMLHTTP");
            }
            
            //请求php文件
            // xhr.open("get","GET封装.php",true);




            if(type==="get")
            {
                xhr.open(type,url+"?"+str,true);
                xhr.send(null);
            }
            else
            {
                xhr.open(type,url+"?"+str,true);
                xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
                xhr.send(str);
            }




            //请求文本文件
            //给URL传递一个参数，保证每次URL不一样，兼容IE
            // xhr.open("post",url+"?"+str,true);

            // //将这段话放在open和send中间，才是正确的用法。
            // xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");

            // xhr.send("userName=gaoju");

            xhr.onreadystatechange = function(ev2) //这是一个回调函数
            {
                if(xhr.readyState==4)
                {
                    clearInterval(timer);// 删除定时器。
                    if(xhr.status>=200 && xhr.status<300||xhr.status==304)
                    {
                        // alert(xhr.responseText);
                        success(xhr);
                    }
                    else
                    {
                        // alert("请求成功");
                        error(xhr);
                    }
                }
            }
        


        //判断外界是否传入了超时时间。  
        if(timeout){
            timer = setInterval(function(){
                console.log("中断请求");
                xhr.abort();
                clearInterval(timer);
            },timeout)  //一到超时时间，就会执行这个回调函数。
        }


    
}
```

##### php文件
```php
<?php

    // echo("succeed!");
    echo $_POST["userName"];
    echo $_POST["userPwd"];
?>
```





### 获取xml文件内容

##### html文件
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script src="xml.js"></script>
    <script>
        window.onload = function(ev)
        {
            var oBtn = document.querySelector("button");
            oBtn.onclick = function(ev1)
            {
                ajax(
                    "get",
                    "xml.php",
                    function(xhr){
                    // alert("666")
                        // console.log(xhr.responseXML);
                        // console.log(document);
                        var res = xhr.responseXML;
                        console.log(res.querySelector("name").innerHTML);
                        console.log(res.querySelector("age").innerHTML);
                    },
                    function(xhr){
                        console.log(xhr.status);
                    }
                )
            }
        }
    </script>
</head>
<body>
    <button>发送请求</button>
</body>
</html>
```

##### js文件
```javascript

    function ajax(type,url,success,error)
    {
                var xhr;
                if (window.XMLHttpRequest)
                {// code for IE7+, Firefox, Chrome, Opera, Safari ,用于高版本的浏览器。
                    xhr=new XMLHttpRequest(); 
                }
                else
                {// code for IE6, IE5  ,   用于支持低版本的IE
                    xhr=new ActiveXObject("Microsoft.XMLHTTP");
                }
                
                if(type==="get")
                {
                    
                    xhr.open(type,url,true);
                    xhr.send(null);
                }
                else
                {
                    xhr.open(type,url,true);
                    // xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
                    xhr.send();
                }
                xhr.onreadystatechange = function(ev2) //这是一个回调函数
                {
                    if(xhr.readyState==4)
                    {
                       
                        if(xhr.status>=200 && xhr.status<300||xhr.status==304)
                        {
                            // alert(xhr.responseText);
                            success(xhr);
                        }
                        else
                        {
                            // alert("请求成功");
                            error(xhr);
                        }
                    }
                }
    }
```

##### php文件
```php
<?php
//php中有中文必须添加的一行代码
//如果php中要返回XML数据，也要在php头部设置该行代码 
header("content-type:text/xml; charset=utf-8");  
    //用下面这个方法获取xml文件的内容

echo file_get_contents("info.xml");

?>
```

##### xml文件
```xml
<?xml version="1.0" encoding="UTF-8"?>        <!--这行是必须的-->
<person>
    <name>高巨</name>
    <age>19</age>
</person>
```

### JSON
```javascript
        <script src="ajax.js"></script>
        
        window.onload =function()
        {
            var oBtn = document.querySelector("button");
            oBtn.onclick = function()
            {
                //用的js文件的连接服务器的方法
                ajax(
                "get",
                "json.php",
                function(xhr){
                    var str=xhr.responseText;
                    // var obj = JSON.stringify(str);
                    //低版本ie不支持下面这个方法，可以使用json2.js框架的方法
                    var obj = JSON.parse(str);
                    console.log(obj.name);
                    console.log(obj.age);
                },
                function(xhr){
                    console.log(xhr.status);
                }
                
                )
                
            }
        }
```


### cookie
F12 在Application查看cookie

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <script>
        window.onload = function()
        {
            document.cookie = "name=gaoju;";
            // addCookie("liuxu","19");
            // addCookie("xxx","999","","/","127.0.0.1")  //添加cookie
            // console.log(getCookie("name"));            //获得cookie
            delCookie("xxx","/")                          //删除cookie
            function addCookie(key,value,day,path,domain)
            {
                //1.处理默认的保存路径
                var index = window.location.pathname.lastIndexOf("/") //取得最后一个'/'的索引位。
                var currentPath = window.location.pathname.slice(0,index);//从0截取至index的索引位，是一个字符串。
                path = path || currentPath; //逻辑或短路，太天才了这一个简化操作。
                //2.处理默认保存的domain
                domain = domain || document.domain;
                //3.处理过期时间
                if(!day)  //没有传过期时间的情况
                {
                    document.cookie = key+"="+value+";"+"path="+path+";domain="+domain+";";
                }
                else  //传入了过期时间的情况。
                {
                    var date = new Date();
                    date.setDate(date.getDate()+day);
                    document.cookie = key+"="+value+";expires="+date.toGMTString+";path="+path+";domain="+domain+";";
                }   
            }
            
            function getCookie(key)
            {
                var res = document.cookie.split(";");
                // console.log(res);

                for(var i=0;i<res.length;i++)
                {
                    var temp = res[i].split("=");
                    if(key ==temp[0])
                    {
                        return temp[1];
                    }
                }
            }
       

            function delCookie(key)            //这种方式只能删除在默认路径下的cookie,
            function delCookie(key,path)       //这样就可以删除指定路径的cookie 
            {
                addCookie(key,getCookie(key),-1,path);  //过期时间设置为-1就直接消失。
            }
        }
    </script>
</head>
<body>
    
</body>
</html>
```

### hash
显示在URL的#3（数字） `http://127.0.0.1/owner2/hash.html#5` 就是这个#5
```html
    <script>
            window.location.hash=5;
            console.log( window.location.hash.substring(1));
    </script>
```

