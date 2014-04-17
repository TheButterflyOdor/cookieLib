cookieLib
=========

cookieLib是对cookie操作做一些简单的封装，包括获取cookie值，设置cookie值都可以很容易的操作，另外屏蔽了一些常规错误

当前用户
----------

[百度地图](http://map.baidu.com/)    
[百度团购](http://tuan.baidu.com/)   
[+You]()

文档说明
----------

该库会提供一个全局的Cookies对象，这个对象包含了所有的功能

属性说明
----------

###Cookie.enabled    
如果为true表示当前支持cookie，否则不支持cookie

公共接口说明
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

###Cookies.set(key,val[,opts])     
设置cookie的一个值和这个cookie的相关设置    
**key**:    
cookie的键名

**val**：    
cookie的值

**options**:      
path：路径       
domain：域名     
expires：过期时间        
secure： 它表示创建的 cookie 只能在 HTTPS 连接中被浏览器传递到服务器端进行会话验证，如果是 HTTP 连接则不会传递该信息


私有接口说明
-------------
>私有接口是让cookieLib调用的，如果你可以接受这些接口带来的副作用的话 是可以直接调用的 ps：不作死就不会死

###Cookies._getExtendedOptions(opts)      
设置cookie的选项值，如果为空的话则设置默认值     
**opts**：    
同Cookies.set中的opts     
###Cookies._isValidDate(date)
判断当前date日期对象是否是合法的日期对象       
**date**：    
日期对象
###Cookies._getExpiresDate(expires,now)
获取基于date的过期时间    
**expires**：    
如果是数字，会返回现在到那个时间的日期    
如果是字符串，则返回一个日期对象   

###Cookies._generateCookieString(key,val,opts)    
把对应的cookie名、值、选项转换成对应的字符串并返回结果      
**key**:    
要设置的cookie的名    
**val**:   
要设置的cookie对应的值    
**opts**:    
要设置的cookie的可选项 同Cookie函数中的opts 

###Cookies._getCookieObjectFromString(documentCookie)
把cookie字符串格式化成一个json对象，cookie的名与内容一一对应   
**documentCookie**:   
整个cookie字符串
###Cookies._getKeyValuePairFromCookieString(cookieString)   
把一个简单的cookie字符串转换成一个key、value对    
**cookieString**:    
一个等号分割的cookie字符串，单个cookie   
>在生成对象的时候会试着解析urlEncode编码后的数据，如果解析失败的就原样输出，如果解析成功了就返回解析成功后的内容。

###Cookies._renewCache()
重新设置Cookie转换后键值对的对象和整个cookie 字符串    

###Cookies._areEnabled()
设置当前cookie的状态，表示当前浏览器是否禁用了cookie
