                                 ---
layout: default
title: Blogging Like a Hacker
---



###   Installation

     npm install --save-dev babel-loader babel-core

###   Usage

    module: {
      loaders: [
        { test: /\.js$/, exclude: /node_modules/, loader: "babel-loader" }
      ]
    }

###  Create .babelrc configuration file

    npm install babel-preset-env --save-dev

    在babelrc文件夹中配置
    {
      "presets": ["env"]
    }


      index.js中写入要编译的语句，例如：let a=x=>x++;
    　在命令行中输入 npm run builds
      结果为var a=function a(x){return x++;};
