```shell
# 创建项目文件夹
$ mkdir demo && cd demo

# 初始化项目
$ npm init -y

# webpack 4.x 需要安装 webpck-cli,webpack命令行工具
$ npm i webpack webpack-cli -D

# 安装插件
# clean-webpack-plugin：打包时自动清除输出文件夹中未用到的文件;
# html-webpack-plugin：打包时会自动生成index.html并替换已有的index.html，bundle.js也会自行添加到 html 中。
$ npm i clean-webpack-plugin html-webpack-plugin -D

# 用以合并通用配置文件与开发环境配置文件
$ npm i webpack-merge -D

# 安装开发服务器devServer,作用是修改代码后实时重新加载（刷新浏览器）
$ npm i webpack-dev-server -D
```

创建项目目录结构为

```
webpack-demo
  |- package.json
+ |- /src
+   |- index.js
```

