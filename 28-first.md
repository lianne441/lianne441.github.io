---
layout: default
title:故事的起点： 发起HTTP请求
---


本节来聊聊发起 HTTP 请求之后，表面那些事（用浏览器发起请求），和底层那些事（用 curl 工具发起请求）。
这些我们观察到的现象就会是后续我们进行深入的 HTTP 知识讨论的起点。

###  资源和 URL

HTTP 故事的开始是浏览器发出请求。但是请求的是什么呢？是服务器上的资源，英文叫 Resource 。

对应的每一个资源，都有一个 URL ，也就是统一资源定位地址，指向这个资源。不过资源分两种：

- 一种是静态资源，也就是各种文件了，最常见的就是静态 HTML ，但是也可以是 PDF ，json 文件等等。
- 另外一种，就是动态资源，也就是 URL 指向的地方不是一个文件，而是一段代码的入口，
服务器经过运算后，才返回运算结果给客户端。
所以， 我们有 http://haoqicat.com/peter.txt ，这个 URL 就是指向一个静态资源的。
如果是 http://haoqicat.com/username 这个可能就是指向动态资源的，后台对应的可能就是一个 API 。

###  浏览器的 HTTP 请求

发起一个 HTTP 请求很容易。比如你说你想用浏览器访问 haoqicat.com 。你所需要做的仅仅是启动浏览器
然后在地址栏输入 http://haoqicat.com ，然后你就可以在页面中看到好奇猫网站的首页了。

那么底层发生了什么呢？首先，我们的浏览器作为 HTTP Client ，发出了一个请求给服务器

```
$ GET http://haoqicat.com/
```

上面的 GET 是 HTTP 方法（或者叫 HTTP 动词），这个后面我们会详细介绍的。

haoqicat.com 的服务器收到请求后，给出响应。响应中带有各种数据，html/css/图片 等等，返回到浏览器。
 浏览器是理解这些文件格式的，所以可以最终展示一个美观的网页给用户。

###  使用 curl 发起请求

因为浏览器给我们展示的是处理过的服务器响应，我们看不到服务器发给我们的响应的本来面目。
怎么样才能看到原始的 HTTP 响应数据呢？

为此，我们可以使用一个 HTTP 工具，就像用浏览器的时候我们输入网址一样，我们可以用 HTTP 工具发送一
个请求到 haoqicat.com。我们的 HTTP 工具，curl ，不会处理响应数据，这样能让我们看到原始的请求
和响应数据，大概长这样：

$ curl -X GET "http://haoqicat.com" -v
* Rebuilt URL to: http://haoqicat.com/
*   Trying 182.92.203.18...
* Connected to haoqicat.com (182.92.203.18) port 80 (#0)
> GET / HTTP/1.1
> Host: haoqicat.com
> User-Agent: curl/7.43.0
> Accept: */*
>
< HTTP/1.1 200 OK
< Server: nginx/1.4.6 (Ubuntu)
< Date: Fri, 09 Dec 2016 09:23:59 GMT
< Content-Type: text/html; charset=utf-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< Vary: Accept-Encoding
<
<!DOCTYPE html>
<html>
<head>
  <title>haoqicat</title>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  ...
</head>
<body>
...

</body>
</html>
* Connection #0 to host haoqicat.com left intact

稍微解释一下上面都发生了什么。首先我们输入了一个命令

$ curl  https://haoqicat.com -v
使用 curl 工具，向 haoqicat.com 发起了一个 HTTP 请求。请求方法为 GET 。如果看一下 man curl
也就是查看 curl 的手册，可以看到 -X 选项后面是专门用来指定 HTTP 方法的。最后的 -v 用来显示详情。
所以我们才能看到比较详尽的后续输出内容。

###  总结

下面我们要来详细介绍一下，请求的头部的每个头（ header ）的意思。

[header 名]：[header 值]
上节中我们请求中有三个 header

> Host: haoqicat.com
> User-Agent: curl/7.43.0
> Accept: */*
都是以冒号隔开的键值对。上面三项：

- 第一个，Host 代表被请求的主机，也就是 haoqicat.com
- 第二个，User-Agent 代表用户使用的客户端，我们这里用的是 curl
- 第三个，Accept 后面指明客户端可以接受的返回资源的类型，* 代表所有类型都接受
其他的 header 还有很多，可以参考 Wikepedia 上的列表 。

###  请求主体

其实请求主体，英文的说法严格来说叫负载数据 payload 。

请求头部之下，一个 request 中还可能包含负载数据（ payload ）。这一项，请求中不一定会包含，
就像咱们上一节的 request 中就没有这一项。GET 请求都是不带负载数据的，POST 请求一般会带负载数据。
这个挺好理解，POST 方法的请求都是要改动服务器数据的，当然要在请求中携带数据过去。

比如，我们页面上有一个表单 form ，我们填写几项数据，然后一点提交，这个就会发出一个 POST 请求，
而我们填写的数据，就会作为 payload 成为请求的一部分。

###  总结一下

一个 HTTP 请求，第一会有一个请求行，然后会有几项 header ，最后，可能会有 payload 。
这个就是任何一个 HTTP 请求的基本格式了。
