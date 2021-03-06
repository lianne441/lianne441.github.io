---
layout: default
title: GET 链接中嵌入参数传递到服务器端 
---

###


GET 链接中嵌入参数传递到服务器端

浏览器一般发出两类请求：GET ，POST 。GET 用来获取数据，POST 用来修改服务器数据。 GET 请求主体数据（ payload ）通常为空，但是依然可以用一定的技巧，通过 GET 请求往服务器传递数据，例如，之前我们介绍的查询字符串的形式。但是那不是唯一形式，这一节我们看看如何在链接中嵌入参数传递给服务器。

案例：传递用户 id 到服务器

现在我想请求一个具体的用户，通常会发这样的请求

GET /users/12345
我们要解决的问题是：如何把 12345 传递给服务器。

先给出后台代码

index.js

const express =  require('express');
const app = express();
const cors = require('cors');
app.use(cors());


app.get('/users/:id', function(req, res){
  console.log(req.params.id)
})

app.listen(3000, function(){
  console.log('running on port 3000...');
});
后台运行

node index.js
启动服务器。

前台发出请求

使用 curl 来发出请求

curl -X GET localhost:3000/users/12345
这样，到后台终端 log 中，可以看到 12345 被打印出来了，表示后台以及收到了前台的参数。

结语

GET 请求因为不涉及到 HTTP 请求主体（ body ）部分，所以传参数都是通过 url 中嵌入 参数的方式实现的。

有任何问题请联系 happypeter
