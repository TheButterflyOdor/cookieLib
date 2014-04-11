cookieLib
=========

cookieLib是对cookie操作做一些简单的封装，包括获取cookie值，设置cookie值都可以很容易的操作，另外屏蔽了一些常规错误


文档说明：
----------

该库会提供一个全局的Cookies对象，这个对象包含了所有的功能


接口说明
----------

###Cookies
Cookies(key,val,options)
这个构造函数可以传递3个参数key，[val,options]，
如果只有一个key的会获取当前key对应的val，如果大于一个参数的话表示设置这个cookie

例如获取`bduss`的值:

``` Cookies("bduss") ```

如果你传多个参数，就是设置cookie  例如设置`bdusss`:

``` Cookies("bduss","zhangsan") ```

###Cookies.get(key)
获取这个key对应的cookie值，跟Cookies方法传递一个参数一样

例如获取`bduss`的值

``` Cookies.get('bduss') ```

> 工作流程说明：

> 首先先取出`document.cookie` 与 `Cookies._cachedDocumentCookie` 比较如果相同的话证明已经缓存过cookie了可以直接从cache的cookie对象中拿值，否则重新获取cookie，然后缓存，最后返回相应的值.

>流程示意图：

>![获取cookie流程示意图](https://farm8.staticflickr.com/7011/13772915335_97ebbbf79c.jpg)

###Cookies.set(key,val,[opts])

**key**:    
cookie的键名

**val**    
cookie的值

**options**:      
path：路径       
domain：域名     
expires：过期时间        
secure： 它表示创建的 cookie 只能在 HTTPS 连接中被浏览器传递到服务器端进行会话验证，如果是 HTTP 连接则不会传递该信息



