# 安装

```
# 全局安装 // 本机上的所有工程下都可以直接使用
$ npm install <Module Name>

# 本地安装 // 只安装在此工程下
$ npm install <Module Name> -g

# 本地安装的同时，将信息写入package.json中
npm install <Module Name> --save
```



# 卸载

```
# 卸载全局安装
$ npm uninstall <Module Name> -g
```



# 查看

```
npm list -g

npm list grunt

npm list --depth=0 -global
```



# 控制版本

```

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

