---
layout: default
title:  HTTP 简介
---


###  HTTP 简介

    HTTP 全称就是“超文本传输协议”，超文本就是 HTML 。 我们的浏览器和服务器进行通信，
    就是通过 HTTP 来进行的。

####  起步走

    如果你跟大多数人一样，那么到现在你应该已经使用了很长时间的互联网了。每次都在浏览器顶部输入那些
    讨厌的 URL 网址，先写个 HTTP 啊，然后冒号，斜杠斜杠，然后三个大不留 (w)，接着是一串所谓域
    名的东西，每次上网都重复，但是你从来不知道这些到底代表了什么。

    每天，网上都有大量的图片，视频，HTML 页面等等这些东西飞来飞去，从服务器上送到我们的浏览器里，
    这个过程都是用 HTTP 协议来传输数据的。所以理解 HTTP ，不管是对于做网站，还是做 Web App ，
    都是非常重要的基本功。



####  HTTP 的请求和响应

    HTTP 协议最重要的两个概念就是请求（ request ）和响应（ response )。

    请求是由浏览器发出的，响应是由服务器给出的。

    请求由请求头和 请求主体 组成。响应由响应头和响应主体来组成。

####  代码演示

    来写一个简单的 HTTP 服务器：

    index.js 如下

```js
    const express = require('express');
    const app = express();

    app.get('/', function(req, res){
      console.log('hello');
      res.send('hello world');
    })

    app.listen(3000, function(){
      console.log('running on port 3000...');
    });
```

然后，后台

    $ nodemon index.js

    启动后台服务器，跑在3000端口。

#### 请求响应

    前台如果用浏览器发请求，也能完成整个循环，但是看不到底层数据。所以我们用 curl 代替
    浏览器来发请求：(另起一个命令行窗口)

    $ curl -X GET localhost:3000 -v

    上面 -v 参数，表示”显示详情“ 。最终输出内容如下：

    * Rebuilt URL to: localhost:3000/
    * Hostname was NOT found in DNS cache
    *   Trying ::1...
    * Connected to localhost (::1) port 3000 (#0)
    > GET / HTTP/1.1
    > User-Agent: curl/7.37.1
    > Host: localhost:3000
    > Accept: */*
    >
    < HTTP/1.1 200 OK
    < X-Powered-By: Express
    < Content-Type: text/html; charset=utf-8
    < Content-Length: 11
    < ETag: W/"b-XrY7u+Ae7tCTyyK7j1rNww"
    < Date: Sat, 17 Dec 2016 01:40:49 GMT
    < Connection: keep-alive
    <
    * Connection #0 to host localhost left intact
    hello world%

####  输出的结构分析

    请求头：

    > GET / HTTP/1.1
    > User-Agent: curl/7.37.1
    > Host: localhost:3000
    > Accept: */*
    请求主体：没有。一般 GET 请求，是没有请求主体的。POST 一般是有主体的。

    响应头，如下

    < HTTP/1.1 200 OK
    < X-Powered-By: Express
    < Content-Type: text/html; charset=utf-8
    < Content-Length: 11
    < ETag: W/"b-XrY7u+Ae7tCTyyK7j1rNww"
    < Date: Sat, 17 Dec 2016 01:40:49 GMT
    < Connection: keep-alive
    响应主体：

    hello world%

    通常我们请求，就是请求一个 html 页面，那么响应主体就是：html 代码。
