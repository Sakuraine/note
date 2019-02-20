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

## 使用

### loader

> loader 用于对模块的源代码进行转换。

在你的应用程序中，有三种使用 loader 的方式：

- [配置](https://www.webpackjs.com/concepts/loaders/#configuration)（推荐）：在 **webpack.config.js** 文件中指定 loader。
- [内联](https://www.webpackjs.com/concepts/loaders/#inline)：在每个 `import` 语句中显式指定 loader。
- [CLI](https://www.webpackjs.com/concepts/loaders/#cli)：在 shell 命令中指定它们。

#### 配置

```js
module.exports = {
  module: {
    rule: [
      {
        test: /\.ts$/, // 需要匹配的文件类型
        use: ts-loader // 使用什么插件编译
      }
    ]
  }
}
```

#### 内联

可以在 `import` 语句或任何[等效于 "import" 的方式](https://www.webpackjs.com/api/module-methods)中指定 loader。使用 `!` 将资源中的 loader 分开。分开的每个部分都相对于当前目录解析。

```js
import Styles from 'style-loader!css-loader?modules!./styles.css';
```

通过前置所有规则及使用 `!`，可以对应覆盖到配置中的任意 loader。

选项可以传递查询参数，例如 `?key=value&foo=bar`，或者一个 JSON 对象，例如 `?{"key":"value","foo":"bar"}`。

> 尽可能使用 `module.rules`，因为这样可以减少源码中的代码量，并且可以在出错时，更快地调试和定位 loader 中的问题。 

#### CLI

你也可以通过 CLI 使用 loader：

```sh
webpack --module-bind jade-loader --module-bind 'css=style-loader!css-loader'
```

这会对 `.jade` 文件使用 `jade-loader`，对 `.css` 文件使用 [`style-loader`](https://www.webpackjs.com/loaders/style-loader) 和 [`css-loader`](https://www.webpackjs.com/loaders/css-loader)。









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
  // const dirs = fs.readdirSync(pagepath); // 返回文件数组列表
  // 只读取制定文件名
  const dirs = ['outpatient', 'doctorstation', 'login'];
})

```

