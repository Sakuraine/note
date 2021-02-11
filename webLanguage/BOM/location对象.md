location对象既是window下的属性也是document下的属性

```js
window.location === document.location; // true
```

location对象下的属性

| attribute | example             | description                                                  |
| --------- | ------------------- | ------------------------------------------------------------ |
| hash      | "#contents"         | 返回URL中的hash(#号后跟零或多个字符)，如果URL中不包含散列，则返回空字符串 |
| host      | "www.wrox.com:80"   | 返回服务器名称和端口号(如果有)                               |
| hostname  | "www.wrox.com"      | 返回不带端口号的服务器名称                                   |
| href      | "http:www.wrox.com" | 返回当前加载页面的完整URL。location对象的饿 toString()方法也返回这个值 |
| pathname  | "/WileyCDA/"        | 返回URL中的目录和(或)文件名                                  |
| port      | "8080"              | 返回URL中指定的端口号。如果不包含端口号，则返回空字符串      |
| protocol  | "http:"             | 返回页面试用的协议。通常是http:或者https:                    |
| search    | "?q=javascript"     | 返回URL的查询字符串。这个字符串以问号开头                    |

​	