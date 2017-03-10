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

    axios 是常用的发 http 请求的工具（现在一般不提发 ajax 请求这个说法了）。

    首先前端来进行装包：

    npm install --save axios

    装包之后，就可以到 src/index.js 中去使用了，代码如下：

    import axios from 'axios';

    我们当前的请求不希望是通过按钮来触发，而是希望，页面加载的时候，自动发出 http 请求，向服务要数据，
    所以，代码非常适合写到生命周期函数中：
```js
    componentWillMount() {
      axios.get('http://localhost:3000/username').then(function(response){
          return console.log(response);
        }
      )
    }
```
###  跨域请求 Access-Control-Allow-Origin

    代码进行到上面，浏览器中用前台请求后台，会在 chrome console 中看到，如下 错误：

    XMLHttpRequest cannot load http://localhost:3000/. No 'Access-Control-Allow-Origin' header is present on the requested resource. Origin 'null' is therefore not allowed access.

    XMLHttpRequest 是发 HTTP 请求的底层机制，是浏览器自带功能。上面的报错翻译如下：

    无法加载后台 http://localhost:3000 . 被请求的资源中没有设置 Access-Control-Allow-Origin 头部。源头设置为 Null ，所以不允许 访问。

    Access-Control-Allow-Origin 字面意思：访问控制允许来源。服务器上的默认是不允许其他网址（或者网址相同，但是端口号不同）的网站请求资源的（也就是默认不允许跨域请求），如果需要开通权限，就需要设置这个选项。

    那么，如何开通服务器上的这个资源访问权限呢？就是要在服务器上做下面的设置

    Access-Control-Allow-Origin: *
    有了这个设置，所有的第三方网站都可以访问服务器上的资源了。

###  跨域请求的解决方案

    解决方案采用： https://github.com/expressjs/cors
    cors 是 Cross Origin Resource Share ，安装了这个包就可以完成

    保证后台启动状态，现在我们看看当前后台资源的 header 设置，可以用下面的 curl 命令

    $ curl -I http://localhost:3000/
    HTTP/1.1 200 OK
    X-Powered-By: Express
    Content-Type: text/html; charset=utf-8
    Content-Length: 11
    ETag: W/"b-sQqNsWTgdUEFt6mb5y4/5Q"
    Date: Thu, 08 Dec 2016 01:51:44 GMT
    Connection: keep-alive

    curl 的 -I 选项用来专门拿到服务器返回的 header 。命令返回的信息，就是服务器端被请求资源的的 header 。上面很明显是没有 Access-Control-Allow-Origin 这一项的。下面我们安装 cors 这个包，就可以解决这个问题。

    具体步骤如下：

    到 https://www.npmjs.com/package/cors 可以看到装包命令如下：

    npm install --save cors
    再次提醒：这个包要安装到后台代码中。

    然后按照文档，添加下面两行代码，再重启服务器代码：

    const cors = require('cors')
    app.use(cors());
    接下来再用 curl -I 看看输出如下：

    HTTP/1.1 200 OK
    X-Powered-By: Express
    Access-Control-Allow-Origin: *
    Content-Type: text/html; charset=utf-8
    Content-Length: 11
    ETag: W/"b-sQqNsWTgdUEFt6mb5y4/5Q"
    Date: Thu, 08 Dec 2016 02:17:23 GMT
    Connection: keep-alive
    这样，我们就看到了 Access-Control-Allow-Origin: * 。

    浏览器中，刷新一下，可以看到后台返回的 response 数据了。错误没有了。

    调整接口数据格式

    后台代码中，添加下面两个 API

    app.get('/username', function(req, res){
      res.json({"username": "happypeter"});
    })
    对应，到前台代码中，调整 componentWillMount ，如下：

    componentWillMount() {
      axios.get('http://localhost:3000/username').then(function(response){
          return console.log(response.data.username);
      })
    }
    这样，前台的 console 中，就可以看到返回数据

    happypeter
    下面进一步调整 componentWillMount 如下：

    componentWillMount() {
      axios.get('http://localhost:3000/username').then((response) => {
          this.setState({username: response.data.username});
      })
    }
