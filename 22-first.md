---
layout: default
title: Blogging Like a Hacker
---


###    前端安装 http-server

    npm install -g http-server

    这样，我们就有了一个简单的系统工具叫 http-server

    cd react-frontend/
    http-server .
    就能把我们的前端项目启动到一个 http 服务器上了。

    打开 express-backend 中的 index.js 代码，添加下面这个 API

    app.get('/username', function(req, res){
      res.send({username: 'happypeter'});
    })

    用 curl 来测试 API

    curl -X GET 'http://localhost:3000/username'

    输出：
    {username: 'happypeter'}

    后端 API 测试通过。

    express-backend git:(master) ✗ curl -X GET localhost:3000/username
    curl: (7) Failed to connect to localhost port 3000: Connection refused
    翻译：连接 localhost:3000 失败，连接被拒绝。
    错误的原因：后端没有启动。nodemon index.js

    
