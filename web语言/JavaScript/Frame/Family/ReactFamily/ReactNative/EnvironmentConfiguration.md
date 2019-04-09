# 开发平台

## macOS

### iOS

#### 安装依赖

- Node `基于 Chrome V8 引擎的 JavaScript 运行环境`
- Watchman `由 Facebook 提供的监视文件系统变更的工具`

##### NPM 安装

```shell
# 安装 Node // v8.3+
$ brew install node

# 安装 Watchman
$ brew install watchman

Error: An unexpected error occurred during the `brew link` step
The formula built, but is not symlinked into /usr/local
Permission denied @ dir_s_mkdir - /usr/local/Frameworks
Error: Permission denied @ dir_s_mkdir - /usr/local/Frameworks

# 设置 npm 淘宝镜像
$ npm config set registry https://registry.npm.taobao.org --global
$ npm config set disturl https://npm.taobao.org/dist --global

# 设置 Yarn 淘宝镜像
$ yarn config set registry https://registry.npm.taobao.org --global
$ yarn config set disturl https://npm.taobao.org/dist --global

# 安装 React Native 的命令行工具
## npm
$ npm install -g react-native-cli
# yarn
$ yarn -g react-native-cli

```

##### Yarn 安装

```shell
# 
```



## Windows

## Linux

