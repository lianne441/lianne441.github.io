---
layout: default
title:HTTP 请求的格式
---

前面我们已经看到了一个请求和响应的流程。这集咱们拿起放大镜，专门聊聊 Request 的具体格式。

###  请求行

第一行的内容被叫做请求行 （ Request Line ） ，具体形式如下

GET/POST [url] HTTP/[version]   GET / HTTP/1.1
这一行就是以HTTP 方法（ HTTP Method ）打头，一般是 GET 或者 POST ，当然还有其他不太常用的方法。
 当我们用 GET 发请求的时候，一般我们就是想要从服务器上 GET （拿到）一些内容，而不是想去修改服务器数据。
 POST 正好就是用来修改服务器上的数据的。到底要 GET 或者要修改哪个资源，就是后面的 URL 这一项来指定了。
 上面例子中，请求的 URL 是 / 。最后就是跟 HTTP 字样，再跟上到底是使用的哪个版本的 HTTP 协议，
 目前一般都是 HTTP 1.1 了。

请求的头部 Headers

请求行下面的内容就是请求的头部了。英文叫做 Headers ，注意是复数。也就是这一项下面可以有多个 header 。

[header 名]：[header 值]
