# npm

> node.js包管理工具  node package manager

# 起步

## 安装&更新

```shell
# 安装稳定版npm
$ npm install -g npm@latest

# 更新npm
$ npm install -g npm
```



## 创建

```shell
# 初始化 package.json 文件
$ npm init

# 以默认模版创建 package.json 文件
$ npm init -y
or
$ npm int --yes

# 在 npm 资源库中注册用户（使用邮箱注册）
$ npm adduser
```



## 安装模块

```shell
# 全局安装 // 本机上的所有工程下都可以直接使用
$ npm install -g <moduleName>

# 本地安装 // 只安装在此目录下
$ npm install <moduleName>

# 本地安装的同时，将信息写入 package.json 中
npm install <moduleName> --save

===========================================
# 使用淘宝 npm 镜像
# 安装淘宝镜像
$ npm install -g cnpm --registry=https://registry.npm.taobao.org

# 使用 cnpm 安装模块
$ cnpm isntall <moduleName>

```

### 安装权限 for Mac

```shell
# 修改npm包所安装目录的权限
$ sudo chown -R $USER /usr/local
```



## 更新

```shell
# 更新当前目录下 node_modules 子目录里对应模块到最新版本
$ npm update <moduleName>

# 更新全局安装的模块到最新版本
$ npm update <moduleName> -g

# 清空 npm 本地缓存，用于对付使用相同版本号发布新版本代码的人
$ npm cache clear
```



## 卸载

```shell
# 卸载全局安装
$ npm uninstall -g <moduleName>

# 卸载本地安装
$ npm uninstall <moduleName>

# 卸载本地安装，且从 package.json 文件中删除
$ npm uninstall --save <moduleName>
```



## 查看

```shell
# 查看全局包位置
$ npm root -g

# 查看所有命令
$ npm help

# 查看命令的详细说明
$ npm help <command>

# 查看全局安装的模块 // depth 显示依赖层级，不设置则默认全部展开
$ npm list -g --depth=0

# 查看
$ npm list grunt
```



## 版本

```shell
# 发布模块
$ npm publish

# 撤销发布过的某个版本代码
$ npm unpublish <moduleName>@<version>
```



> package.json 属性说明

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



## npm包管理工具

### [ndm](https://github.com/720kb/ndm)

> 查看和管理全局和本地包

## 其他

### 如果npm损坏了

#### for Mac

```shell
$ curl -L https://www.npmjs.org/install.sh | sh
```

#### for Windows

去官网重新下载



# 高级

## 创建node.js模块



## 发布npm包

### 语义版本控制

| 代码状态             | 阶段     | 规则                                         | 示例版本 |
| -------------------- | -------- | -------------------------------------------- | -------- |
| 首发                 | 新产品   | 从1.0.0开始                                  | 1.0.0    |
| 向后兼容的错误修复   | 补丁发布 | 增加第三位数                                 | 1.0.1    |
| 向后兼容的新功能     | 次要发布 | 增加中间数字并将最后一个数字重置为零         | 1.1.0    |
| 破坏向后兼容性的更改 | 主要发布 | 增加第一个数字并将中间和最后一个数字重置为零 | 2.0.0    |





