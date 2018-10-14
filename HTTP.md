## osi 参考模型

<img src='https://images2015.cnblogs.com/blog/705728/201604/705728-20160424234824085-667046040.png' />

<img src='https://images2015.cnblogs.com/blog/705728/201604/705728-20160424234825491-384470376.png' />

tcp/ip协议在传输层

http协议在应用层

http请求建立在tcp链接之上，一个tcp链接可以进行多次http请求

## 三次握手


<img src='https://pic2.zhimg.com/v2-c368d5cd8b80e9121621231d4bc19335_b.jpg' />

<img src='https://pic1.zhimg.com/v2-ea262ece5e3a5da46ea72bcf272ce6ec_r.jpg' />

<img src='https://pic2.zhimg.com/v2-2271eb84ef4f8da6b948668f2448c405_r.jpg' />

## udp和tcp对比

TCP的优点： 可靠，稳定 TCP的可靠体现在TCP在传递数据之前，会有三次握手来建立连接，而且在数据传递时，有确认、窗口、重传、拥塞控制机制，

在数据传完后，还会断开连接用来节约系统资源。 

TCP的缺点： 慢，效率低，占用系统资源高，易被攻击 

UDP的优点： 快，比TCP稍安全 

UDP没有TCP的握手、确认、窗口、重传、拥塞控制等机制，UDP是一个无状态的传输协议，所以它在传递数据时非常快。

没有TCP的这些机制，UDP较TCP被攻击者利用的漏洞就要少一些

UDP的缺点： 不可靠，不稳定 因为UDP没有TCP那些可靠的机制，在数据传递时，如果网络质量不好，就会很容易丢包

## URI URL URN

uri 统一资源标识符，用来唯一标识互联网上的信息资源，包括url和urn

url 统一资源定位器

urn 永久统一资源定位符

## HTTP请求的方法：

HTTP/1.1协议中共定义了八种方法（有时也叫“动作”），来表明Request-URL指定的资源不同的操作方式

```
1、OPTIONS
返回服务器针对特定资源所支持的HTTP请求方法，

也可以利用向web服务器发送‘*’的请求来测试服务器的功能性
2、HEAD
向服务器索与GET请求相一致的响应，只不过响应体将不会被返回。

这一方法可以再不必传输整个响应内容的情况下，就可以获取包含在响应小消息头中的元信息。
3、GET
向特定的资源发出请求。它本质就是发送一个请求来取得服务器上的某一资源。
资源通过一组HTTP头和呈现数据（如HTML文本，或者图片或者视频等）返回给客户端。GET请求中，永远不会包含呈现数据。
4、POST
向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。
数据被包含在请求体中。POST请求可能会导致新的资源的建立和/或已有资源的修改。
Loadrunner中对应POST请求函数：web_submit_data,web_submit_form
5、PUT
向指定资源位置上传其最新内容
6、DELETE
请求服务器删除Request-URL所标识的资源
7、TRACE
回显服务器收到的请求，主要用于测试或诊断
8、CONNECT
HTTP/1.1协议中预留给能够将连接改为管道方式的代理服务器。
```
## 状态码

1xx:服务器收到请求，需要请求者继续执行操作

2xx:	成功，操作被成功接收并处理

3xx:重定向，需要进一步的操作以完成请求

4xx:	客户端错误，请求包含语法错误或无法完成请求

5xx:	服务器错误，服务器在处理请求的过程中发生了错误


401	Unauthorized	请求要求用户的身份认证

403	Forbidden	服务器理解请求客户端的请求，但是拒绝执行此请求

404	Not Found	服务器无法根据客户端的请求找到资源

500	Internal Server Error	服务器内部错误

502	Bad Gateway	充当网关或代理的服务器，从远端服务器接收到了一个无效的请求

## 跨域

cors 跨域请求技术

```
1. 后端返回头信息带上 'Access-Control-Allow-Origin':'*'  指定对应的域名

2.jsonp

3.websoctet

4.postMessage

5.hash

```
## cors 预请求

```

cors 允许的方法： get post head 这仨不需要预请求

coes 允许的 Content-Type   text/plain  multipart/form-data  application/x-www-form-urlencoded 这仨不需要预请求

请求头限制

被限制的请求方式或者Content-Type要先发一个预请求验证

被限制的类型要想跨域就要改请求头

'Access-Control-Allow-Origin':'*'  指定对应的域名

'Access-Control-Allow-Headers':'X-Test-Cors'

'Access-Control-Allow-Methods':'PUT,Delete'

'Access-Control-Max-Age':'1000'   // 1000秒内无需再次发送预请求验证
```

## Cache-Control

Cache-Control缓存控制

可以设置下面的值

public 所有代理服务器可缓存

private 只有发起请求的浏览器可缓存

no-cache 不可缓存(需要去服务端验证缓存是否可用)

no-store 不可缓存(不需要去服务端验证)

max-age = <seconds>  浏览器缓存时间
  
s-maxage = <seconds> 代理服务器缓存时间
  
max-stale = <seconds> 

must-revalidate  重新验证

no-transform  禁止代理服务器修改资源

设置缓存时间后之后，前端可以在构建时为文件名添加哈希值来表示缓存有无更新，从而更新缓存

## cookie

可以在头信息里面通过 'Set-Cookie' 为用户写入cookie

```
// max-age 缓存时间 
// HttpOnly 设置了HttpOnly属性，那么通过js脚本将无法读取到cookie信息
// Domain 设置域名下所有的二级域名都可以访问本条cookie
'Set-Cookie':['id=123;max-age=10','abc=456;HttpOnly','def=12121;Domain=test.com']
```
js可以通过下面来读取和设置cookie

```

var ck = document.cookie

document.cookie='key=value'


```

## session

cookie 和session 的区别：

1、cookie数据存放在客户的浏览器上，session数据放在服务器上。

2、cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗
   考虑到安全应当使用session。

3、session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能
   考虑到减轻服务器性能方面，应当使用COOKIE。

4、单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。


## http 长连接

Connection: Keep-Alive  保持tcp连接长连接，请求资源数量大的时候提高资源下载速度，因为不用重复的三次握手四次挥手，默认开启

## 数据协商

客户端期望服务器返回的数据格式


请求
```
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36


Accept  数据类型编码格式

Accept-Encoding   数据压缩算法

Accept-Language   语言

User-Agent  浏览器信息

```
返回

```
Content-Type: text/html;charset=utf-8
Content-Encoding: gzip
Content-Language: zh-CN
```

## Redirect 重定向

```js
const http = require('http')
http.createServer(function(req,res){
    if(req.url ==='/'){
        res.writeHead(302,{
            'Location':'/new'
        })
        res.end('')
    }
    if(req.url ==='/new'){
        res.writeHead(200,{
            'content-type': 'text/html;charset=utf-8'
        })
        res.end('<h1>重定向</h1>')
    }

}).listen(8080)

```

## htttps

公钥加密 

传输

私钥解密







