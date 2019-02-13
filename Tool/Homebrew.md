# 起步

## 安装Homebrew

command + space 打开聚焦搜索；

输入 terminal.app 打开终端；

在终端输入：

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```



## 安装

##### 安装指定的包

```shell
$ brew install <packageName>
```



## 更新

##### 更新 Homebrew

```shell
$ brew update
```

##### 更新所有可以更新的包

```shell
$ brew upgrade
```

##### 更新指定的包

```shell
$ brew upgrade <packageName>
```



## 卸载

##### 卸载指定的包

```shell
$ brew uninstall <packageName>
```

##### 卸载所有旧版本

```shell
$ brew cleanup
```

##### 卸载指定版本

```shell
$ brew cleanup <packageName>
```



## 查看

##### 查看已安装包列表

```shell
$ brew list
```

##### 查看包信息

```shell
$ brew info <packageName>
```

##### 查看可以更新的包的

```shell
$ brew outdated
```

##### 查看可以清理的旧版本

```shell
$ brew cleanup -n
```



## 搜索

##### 搜索指定的版本

```shell
$ brew search <packageName>
```

