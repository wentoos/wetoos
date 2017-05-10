# AJAX  
#### 定义：不重新加载整个页面，实现页面的局部刷新。  
- 特点：AJAX = Asynchronous JavaScript and XML（异步的 JavaScript 和 XML）。简单地说就是不影响网页的加载。
***
### 原生AJAX碰撞xml  
- 首先构建实例对象，并发送请求命令  
```js
var xml = new XMLHttpRequest();
xml.open('GET','https://api.github.com/users/wentoos',true);//API 接口地址 是否异步
xml.send()//发送数据请求
    //GET 请求方式
```    

### 1. AJAX  请求方式  
####    a. GET 还是 POST？  
- GET   请求
1 . 与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用。   
2 . 然而，在以下情况中，请使用 POST 请求：
无法使用缓存文件（更新服务器上的文件或数据库）
向服务器发送大量数据（POST 没有数据量限制）
发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠   
```JS
xmlhttp.open("GET","/try/ajax/demo_get.php",true);
xmlhttp.send();
```  
- POST  请求
```JS
xmlhttp.open("POST","/try/ajax/demo_post.php",true);
xmlhttp.send();
```  
* 注意：所有使用post请求数据时必须指定发送send()请求数据类型，仅存在语法不同但意思相同   
```js
xml.setRequestHeader('Content-type','application/json');//使用json的数据类型
```

### 2. AJAX - onreadystatechange 事件  
```js
xml.onreadystatechange= function(){
    if (xml.readyState==4 && xml.status==200){
        console.log(xml.responseText);
    }
}
```
- readyState 监控 xml.responseText状态的方法，有0到4五种状态   
    - 0: 请求未初始化  
    - 1: 服务器连接已建立
    - 2: 请求已接收
    - 3: 请求处理中
    - 4: 请求已完成，且响应已就绪    
- status 返回浏览器的服务器状态码及其对应的含义如下
    - 200：服务器响应正常。
    - 304：该资源在上次请求之后没有任何修改（这通常用于浏览器的缓存机制，使用GET请求时尤其需要注意）。
    - 400：无法找到请求的资源。
    - 401：访问资源的权限不够。
    - 403：没有权限访问资源。
    - 404：需要访问的资源不存在。
    - 405：需要访问的资源被禁止。
    - 407：访问的资源需要代理身份验证。
    - 414：请求的URL太长。
    - 500：服务器内部错误。
***
#### 原生js ajax  
```js
<script>
    var xml = new XMLHttpRequest();//实例化AJAX对象
    xml.onreadystatechange= function(){
        if (xml.readyState==4 && xml.status==200){
            console.log(xml.responseText);
        }//判断请求是否完成和服务器状态
        console.log(xml.readyState);
    }
    xml.open('POST','https://cnodejs.org/api/v1/accesstoken',true);//指定请求类型post，服务器地址，和是否异步，true为异步
    xml.setRequestHeader('Content-type','application/json');//传给服务器的数据类型为json
    let data = {
        accesstoken :'3f77acb1-d753-4393-b784-44913190e6a8'
    }
    xml.send(JSON.stringify(data))//传出数据
</script>
```  
#### Jquery AJAX  
```JS
<script src="https://cdn.bootcss.com/jquery/3.2.1/jquery.js"></script>
<script>
//方法一
    $.ajax({
        //type:'GET',  JQ默认就是get请求
        url:'https://cnodejs.org/api/v1/topics',
        success:function (data){
            console.log(data);
        }//接收成功的数据
        error:function(data){
        }//接受失败的
    })// 与$.get一样
    //jq ajax 官方文档
//方法二 链式操作
    $.ajax({
        //type:'GET',  JQ默认就是get请求
        url:'https://cnodejs.org/api/v1/topics',
    }).done(
        function(data){
            console.log(data);
    }).fail(
        function(err){
            console.log(err);
    }).always(function(){
        console.log('q');
    })//错误正确都执行
//POST 请求
    $.ajax({
        type:'POST',//请求类型
        dataType:'json',//后台返回的类型
        contentType:'application/json',//发往后台的类型
        url:'https://cnodejs.org/api/v1/accesstoken',//后台地址
        data: JSON.stringify({accesstoken :'3f77acb1-d753-4393-b784-44913190e6a8'})//去后台的json数据
    }).done(
        function(data){
            console.log(data);
    }).fail(
        function(err){
            console.log(err);
    }).always(function(){
        conso le.log('q');
    })//错误正确都执行
</script>
```  
#### 跨域请求   
- 跨域的产生 当请求数据端口与前段端口不同时就产生了跨域问题
#### 用jq解决JSONP 解决跨域请求   
```js
<script>
$.ajax({
    type:'POST',
    // dataType:'json',
    dataType:'jsonp',//这就是主要的东西
    jsonp:'callback',//这就是主要的东西
    contentType:'application/json',
    url:'https://api.douban.com/v2/book/1220562',
}).done(
    function(data){
        console.log(data);
    }
)
</script>
```  

### fetch 请求(兼容不好)（es6）
