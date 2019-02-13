# webpack

## 安装

> 安装前请先安装node

##### 本地安装

```shell
$ npm install webpack webpack-cli --save-dev
# webpack-cli用于在命令行运行webpack，webpack v4+需要
```

##### 全局安装

```shell
$ npm install webpack -g
```

##### 安装最新版本

```shell
$ npm install webpack@beta
```



> webpack.base.config.js文件配置

```js
const webpack = require('webpack');
const fs = require('fs');
const path = require('path');
const HtmlWebpackPlugin = require('html-webpack-plugin');
const ExtractTextPlugin = require('extract-text-webpack-plugin');
const CopyWebpackPlugin = require('copy-webpack-plugin');
const WepackGenerateScript = require('./webpack-generate-script');

// 配置上下文路径
const context = path.resolve(__dirname, '../src');
// 获取入口文件
const config = (function () {
  // 获取多页入口路径
  const pagepath = `${context}/pages`;
  // 读取多页文件名
  // const dirs = fs.readdirSync(pagepath);
  // 只读取制定文件名
  const dirs = ['outpatient', 'doctorstation', 'login'];
})

```

