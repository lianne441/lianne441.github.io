---
layout: default
title: Blogging Like a Hacker
---

###  前台向后台传递参数

    本节要做的事情就是，前台在发 axios 的 http 请求的时候，我们要携带 一个参数到服务器端。这里，参数的本质就是字符串。所以这一集的本质就是 把一个任意我们想用的字符串，从前台传到后台。

    比如，我们现在向把一个 “123456” 这个字符串，传递一下。

###＃  前台发出请求

    后台代码：

```js
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
```

    前台代码：

```js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import axios from 'axios';

    class App extends React.Component{
    constructor(){
    super();
    this.state={
      user:{},
      users:[]
    }
    }
    handleClick(e){
      e.preventDefault();
      axios.get('http://localhost:3000/users/58c24c1858d83402647e3887').then((response) => {
        console.log(response);
        this.setState({
          user: response.data
        });
      })
    }
    componentWillMount() {
      axios.get('http://localhost:3000/users').then((response) => {
        console.log(response.data.users);
        this.setState({users: response.data.users});
      })
    }
    render(){
      const userList = this.state.users.map((user, i) => {
        return (
          <div key={i}>
             username: <br />
            {user.username} <br />
            {user.email}
          </div>
        )
      });

      return(
        <div>
          { userList }
          <div onClick={this.handleClick.bind(this)}>
             clickme
          </div>
          <div>
            username:
            { this.state.user.username }
          </div>
      </div>
      )
    }
    }
    export default App;

```

    在express-backend中，用curl测试一下(123456可以换成任意字符串)

    $ curl -X GET localhost:3000/users/123456

    在启动窗口显示：(npm start)

    123456

    注意，前台的请求是：

    GET /users/123456

    后台如果 API 写成这样：

    app.get('/users'...)

    是匹配不上的。可以写成

    app.get('/users/123456'...)
    但是这样前台能传递的字符串就限制死了。所以最好就是使用 express 的 params 机制来进行处理，也就是写成如上的

    app.get('/users/:id')
    注：上面的 id 写成其他的单词也可以，关键点就是前面的冒号。这样写之后 前台请求中的字符串，就可以在后台通过 req.params.id 这个变量来拿到了。
