# npm

> node.js包管理工具  node package manager

# 起步

## 创建

```
# 初始化 package.json 文件
$ npm init

# 在 npm 资源库中注册用户（使用邮箱注册）
$ npm adduser
```



## 安装模块

```
# 全局安装 // 本机上的所有工程下都可以直接使用
$ npm install <ModuleName>

# 本地安装 // 只安装在此目录下
$ npm install <ModuleName> -g

# 本地安装的同时，将信息写入 package.json 中
npm install <ModuleName> --save

===========================================
# 使用淘宝 npm 镜像
# 安装淘宝镜像
$ npm install -g cnpm --registry=https://registry.npm.taobao.org

# 使用 cnpm 安装模块
$ cnpm isntall <ModuleName>

```



## 更新

```
# 更新当前目录下 node_modules 子目录里对应模块到最新版本
$ npm update <ModuleName>

# 更新全局安装的模块到最新版本
$ npm update <ModuleName> -g

# 清空 npm 本地缓存，用于对付使用相同版本号发布新版本代码的人
$ npm cache clear
```



## 卸载

```
# 卸载全局安装
$ npm uninstall <ModuleName> -g
```



## 查看

```
# 查看所有命令
$ npm help

# 查看命令的详细说明
$ npm help <command>

# 查看全局安装的模块
$ npm list -g

# 查看
$ npm list grunt

$ npm list --depth=0 -global
```



## 版本

```
# 发布模块
$ npm publish

# 撤销发布过的某个版本代码
$ npm unpublish <ModuleName>@<version>
```



package.json 属性说明

```json
{
  "name": "express", // 包名
  "description": "Fast, unopinionated, minimalist web framework", // 描述
  "version": "4.13.3", // 版本号
  "author": { // 包作者信息
    "name": "TJ Holowaychuk", // 姓名
    "email": "tj@vision-media.ca", // 邮箱
  },
  "contributors": [ // 包的其他贡献者姓名
    {
      "name": "Aaron Heckmann",
      "email": "aaron.heckmann+github@gmail.com"
    },
  ],
  "license": "MIT",
  "homepage": "http://expressjs.com/", // 包的官网URL
  "keywords": [ // 关键字
    "express",
    "framework",
    "sinatra",
    "web",
    "rest",
    "restful",
    "router",
    "app",
    "api"
  ],
}


dependencies - 依赖包列表。如果依赖包没有安装，npm 会自动将依赖包安装在 node_module 目录下。
repository - 包代码存放的地方的类型，可以是 git 或 svn，git 可在 Github 上。
main - main 字段指定了程序的主入口文件，require('moduleName') 就会加载这个文件。这个字段的默认值是模块根目录下面的 index.js。

```







****



查看全局安装的依赖

```
npm list --depth=0 -global
```

卸载全局安装的依赖

```
npm uninstall -g 依赖包名称
```

更新全局安装的所有依赖

```
npm updata -g
```

