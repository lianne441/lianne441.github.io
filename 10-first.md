---
layout: default
title: Blogging Like a Hacker
---



###   10. nodejs 安装

      nodejs 的模块分为 3 类，核心模块，第三方模块，以及自定义的模块

      // 通过 module.exports 导出模块，require 导入模块。

      // 导入核心模块
      var fs = require('fs')

      // 导入第三方模块
      var $ = require('jquery')

      // 导入自定义的模块
      var test = require('./test')

      // 导出模块
      module.exports.test = 'test';
      我们的前端开发会用到 es6 的模块，需要用 webpack 来打包我们的代码。

      // 创建项目文件夹
      mkdir webpack-demo && cd webpack-demo
      // 初始化项目
      npm init -y
      // 安装 webpack
      npm i -D webpack
      // 编写我们的 npm 脚本，使用项目内的 webpack
      "scripts": {
        "build": "./node_modules/.bin/webpack"
      }
      // 增加 webpack 的配置文件 webpack.config.js
      module.exports = {
        entry: './index.js',
        output: {
          filename: 'bundle.js'
        }
      }
      有任何问题请联系 happypeter ： happypeter1983@gmail.com
      所有内容基于 允许商用保留署名的 CC 协议 发布
