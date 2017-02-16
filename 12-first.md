---
layout: default
title: Blogging Like a Hacker
---


### 　初始化项目

　　　 .gitignore 隐藏文件　（和ｇｉｔ类似）

      创建一个项目

      $ mkdir webpack-demos && cd webpack-demos
      $ git init
      $ touch README.md .gitignore
      $ npm init　　

      编辑.gitignore

      node_modules
      *.log*
      .idea

      # 安装并保存在项目的依赖中
      $ npm install --save-dev webpack webpack-dev-server
      # 如果想直接在命令行使用webpack或webpack-dev-server命令，请全局安装
      $ npm install -g webpack webpack-dev-server

      创建webpack的配置文件

      $ touch webpack.config.js

      进行基本配置

      var path = require('path');

      module.exports = {
          entry: path.resolve(__dirname, 'src/index.js'),
          output: {
              path: path.resolve(__dirname, 'build'),
              filename: 'bundle.js'
          },
      };

      执行webpack命令,这里我们用的是项目内安装的webpack

      $ ./node_modules/.bin/webpack

      webpack -p 产品编译及压缩
      webpack --watch 开发环境下持续的监听文件变动来进行编译(非常快!)
      webpack -d 引入 source maps　　　　　　
　　　　
      devtool: 'cheap-module-source-map'
