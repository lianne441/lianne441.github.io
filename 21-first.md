---
layout: default
title: Blogging Like a Hacker
---


###  React 牵手 Express

    前端和后端是完全独立的两个项目，通过 API 来作为桥梁。其实，我们后端虽然是 Nodejs 写的，但是用 PHP/JAVA 也能写。

    react搭建环境(回顾)


    mkdir suiliyan441
    cd suiliyan441
    atom .

    生成package.json

    npm init

    安装四个包

    npm i --save weebpack babel-core babel-preset-env babel-loader react react-dom

    npm i --save babel-preset-react

    npm i --save axios


    1.index.js中：

    import React from 'react';
    import ReactDOM from 'react-dom';

    import App from './App';

    ReactDOM.render(
        <div>
          <App />
       </div>,
      document.getElementById("app")
    )

    2.index.html中：

    <!DOCTYPE html>
    <html lang="en">
    <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <meta http-equiv="X-UA-Compatible" content="ie=edge">
      <title>Document</title>
    </head>
    <body>

      <div id="app"></div>
      <script src="./build/bundle.js" charset="utf-8"></script>
    </body>
    </html>

    3..babelrc中：

    {
      "presets":["env","react"]
    }

    4.Ａpp.js中：

    import React, { Component } from 'react';
    import ReactDOM from 'react-dom';

    class App extends Component {
      constructor(){
        super();
        this.state = {
          username: ''
        };
      }
      componentWillMount() {
        this.setState({username: 'suiliyan'});
      }
      render(){
        return(
          <div>
            {this.state.username}
          </div>
        )
      }
    }
    export default App;

    5.package.json中：

    {
      "name": "suiliyan441",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "./node_modules/.bin/webpack -w",
        "dev": "./node_modules/.bin/webpack-dev-server --config webpack.dev.config.js"
      },
      "author": "",
      "license": "ISC",
      "dependencies": {
        "babel-core": "^6.23.1",
        "babel-loader": "^6.4.0",
        "babel-preset-env": "^1.2.1",
        "webpack": "^2.2.1"
      }
    }

    ６.webpack.config.js

    var path = require('path');

    module.exports = {
      entry: path.resolve(__dirname, 'src/index.js'),
      output: {
        path: path.resolve(__dirname, 'build'),
        filename: 'bundle.js'
      },
      module: {
        rules: [
          {
            test: /\.js$/,
            use: 'babel-loader'
          }
        ]
      }
    };
