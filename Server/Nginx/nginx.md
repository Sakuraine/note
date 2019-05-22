# Nginx

> nginx是一个高性能的HTTP和反向代理服务器，也是一个通用的TCP/UDP代理服务器，最初由俄罗斯人Igor Sysoev编写。

**nginx的作用**

- 解决跨域
- 请求过滤
- 配置gzip
- 负载均衡
- 静态资源服务器

## 基本配置

### 配置结构

```nginx
events { 
}

http 
{
    server
    { 
        location path
        {
            ...
        }
        location path
        {
            ...
        }
     }

    server
    {
        ...
    }

}
```

- `main`:nginx的全局配置，对全局生效。

- `events`:配置影响nginx服务器或与用户的网络连接。

- `http`：可以嵌套多个server，配置代理，缓存，日志定义等绝大多数功能和第三方模块的配置。

- `server`：配置虚拟主机的相关参数，一个http中可以有多个server。

- `location`：配置请求的路由，以及各种页面的处理情况。

- `upstream`：配置后端服务器具体地址，负载均衡配置不可或缺的部分。

