# nginx

## 安装

### for mac

**安装工具：**homebrew

**步骤：**

打开终端:

- 查询要安装的软件是否存在

  ```shell
  brew search nginx
  ```

- 查看信息

  ```shell
  brew info nginx
  ```

- 安装

  ```shell
  brew install nginx
  ```

- 查看nginx安装目录（是否如info所说）

  ```shell
  open /usr/local/etc/nginx/
  
  open /usr/local/Cellar/nginx  //其实这个才是nginx被安装到的目录
  ```

## 命令

**启动**

```shell
sudo nginx
```

**关闭**

```shell
sudo nginx -s stop
```

打开活动监视器；

关闭nginx；

**重新启动**

```shell
sudo sudo nginx -s reload
```





