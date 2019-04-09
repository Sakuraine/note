# Yarn

> 包管理工具

## 安装

### MacOS

##### 通过 Homebrew 安装

```shell
# 安装
$ brew install yarn

# 升级
$ brew upgrade yarn
```

##### 通过 MacPorts 安装

```shell
$ sudo port install yarn
```

查看yarn版本

```shell
$ yarn --version
```

### Windows

##### 通过 Chocolatey 安装

```shell
$ choco install yarn
```



## 使用

```shell
# 初始化
$ yarn init

# 添加依赖包
$ yarn add [package]
$ yarn add [package]@[version]
$ yarn add [package]@[tag]

# 将依赖项添加到不同依赖项类别中
  分别添加到 devDependencies、peerDependencies 和 optionalDependencies 类别中：
$ yarn add [package] --dev
$ yarn add [package] --peer
$ yarn add [package] --optional

# 升级依赖包
$ yarn upgrade [package]
$ yarn upgrade [package]@[version]
$ yarn upgrade [package]@[tag]

# 移除依赖包
$ yarn remove [package]

# 安装项目的全部依赖
$ yarn
or
$ yarn install

# 安装全局依赖
$ yarn global add [package]
```

