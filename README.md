cookieLib
=========

cookieLib是对cookie操作做一些简单的封装，包括获取cookie值，设置cookie值都可以很容易的操作，另外屏蔽了一些常规错误


##文档说明：

该库会提供一个全局的Cookies对象，这个对象包含了所有的功能

##接口说明

###Cookies
Cookies(key,val,options)
这个构造函数可以传递3个参数key，[val,options]，
如果只有一个key的会获取当前key对应的val，如果大于一个参数的话表示设置这个cookie

例如获取username的值:

``` Cookies("username") ```

如果你传多个参数，就是设置cookie:

``` Cookies("username","zhangsan") ```

