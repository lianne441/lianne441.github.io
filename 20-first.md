---
layout: default
title: Blogging Like a Hacker
---


###   EXPRESS 后台框架


    面向对象编程两个重要概念：对象和类
    对象是类实例化

    React 是一个 前端框架 ，前端框架是运行在浏览器 环境下的，负责 UI（ User Interface 用户界面）。
    Express 就是一个后台框架

    Express 就是 Nodejs 的 一个框架，而且是 Nodejs 各种后台框架中最为通用， Nodejs相当于在后台创建一个可以使用javascript的可能
    Express 的官网位置是 http://www.expressjs.com.cn/
    API 是应用开发接口，简称接口（Application Program Interface ），前后台沟通（方式）接口。

    补充知识：框架，库，工具
    工具：就是完成特定的一个小功能的软件，比如 Babel
    库： 英文叫 lib ，我们每天 import 的东西，都是库。库是把一系列相关工具，组织到一起。例如，lodash ，react 。库里面的东西虽然多，但是都是干一类工作的。
    框架：英文是 framework ，是把很多类功能的工具和库集合到一起，目的是完成整个项目。 例如，RubyOnRails

    第一步，要新建文件夹，并把它初始化为一个 Nodejs 项目：

    ```
    mkdir express-hello
    cd express-hello
    npm init -y

    ```
    这样文件夹内就会生成一个 package.json ，有了这个文件，我们这个文件夹就可以 叫做一个 Nodejs 项目 了

    下一步，进行装包

    ```

    npm install express --save

    ```

    报错：Refusing to install express as a dependency of itself
    原因：文件夹名与包名重复
    解决方法就是：修改项目文件夹名。

    Node.green 网站上，可以看到新版的 Nodejs (7.0 版本以上)对于 ES6 的支持已经到了99% 。所以， 不用 Babel 我们也可以直接用 ES6 语法
    我们的后台代码暂时需要用 require 来替代 import 。require 用的是 commonjs 模块语法， 这个是 Nodejs 原生支持的。ES6 可以用，别用 import 就好了。

    到项目中，创建一个 index.js 文件，内容如下：

    ```

    const express =  require('express');

    let app = express();

    app.listen(3000,function(){
      console.log('Running on port 3000...');
    });

    ```
    监听３０００端口（ＡＰＩ），始终监听客户端的请求
    3000 指的是 3000端口 ，端口的英文是 port ，之前端口有８０８０，８０８１，３０００等

    注：const 是 只读变量，let 是可以修改的变量

    这样，后台（命令行）执行的效果就是

    ```
    $ node index.js
    running on port 3000...

    ```

    上面添加的无名函数 function(){...} 在这里 的作用是回调函数( callback function ) 。
    一般回调函数的使用场合就是，之前的一个操作耗时比较长（或者是异步操作） 这样的情况下才使用回调函数。

    我们在上面的 index.js 中，app.listen 语句的上面，添加如下代码：

    ```

    app.get('/', function(){
      console.log('request come in...');
    })

    ```
    get 是一个 http 请求的动词 ，类似的还有 post/delete/put 。
    / 是一个路径 ，英文 path

    request = verb + path + data
    这里的不是发出请求 ，而是 接收请求 。

    小贴士：翻墙方式：

    免费的：https://laod.cn
    Peter 自己用：https://agentwho.rocks 小贴士结束。

    默认动词就是 GET ，同时 :3000 用来指定端口号。

    //get /title 3000
    app.get('/title',function(){
      console.log('my title')
    })

    前台网页：localhost:3000/title
    命令行（相当于后台）：my title
    注：刷新一次，请求一次，命令行输出一次console.log()中的内容

    app.get('/title',function(req,res){
      res.send('my title')
    })
    注：request,response简称req,res。分别为请求和响应。

    安装nodemon
    npm i -g nodemon
    nodemon index.js

    app.get('/', function(req, res){
      res.send('Hello World');
    })

    前台实时更新，内容变为'my title'
    内容变为'Hello World'

    前端，front-end，或者也可以叫前台。后端，back-end 也可叫后台。

    前端代码运行环境是浏览器，笔记本或ipad;
    后端代码运行环境是一个放在人家机房里的刀片机。

    给出两个 API 的例子：
    // GET /title(前台网址为：‘http://localhost:3000/title’)
    app.get('/title', function(req, res){
        res.send('my title');
      }
    )

    // GET /content(前台网址为：‘http://localhost:3000/content’)
    app.get('/content', function(req, res){
      res.send('my content');
    })

    全部代码:

    package.json 如下：

    {
      "name": "express-hello",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "keywords": [],
      "author": "",
      "license": "ISC",
      "dependencies": {
        "express": "^4.14.0"
      }
    }
    index.js 代码如下

    const express =  require('express');
    const app = express();


    // 下面三行就是我们实现的一个 API
    app.get('/', function(req, res){
      res.send('Hello World');
    })

    app.listen(3000, function(){
      console.log('running on port 3000...');
    });
    上面两个文件都放在一个 express-hello 文件夹中，然后

    cd express-hello
    npm install
    node index.js
    就可以把代码运行起来了。
