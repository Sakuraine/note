http协议

> 无状态协议



**一个完整的http请求过程：**

1. 建立与服务器的TCP连接
2. 客户端浏览器向WEB服务器发送请求
3. 客户端浏览器向WEB服务器发送请求头信息
4. WEB服务器应答
5. WEB服务器发送应答头信息
6. WEB服务器向浏览器发送数据
7. WEB服务器断开TCP连接

## Ajax

异步的javascript 和 xml

XMLHttpRequest内置对象

### ajax网站中应用

1. 瀑布流
2. 检测用户是否被占用
3. 登录验证
4. 关键字提示

### 优势

1. 瀑布流降低服务器带宽
2. 用户体验好
3. 前后端分离

### 创建ajax兼容IE6和其他浏览器不同

```js
if(window.XMLHttpRequest){
  //IE7+
  var http=new XMLHttpRequest();
}else{
  //IE6
  var http=new ActiveXObject("Microsoft.XMLHTTP");
}
```



### ajax对象--属性和方法
难点:ajax对象的属性和方法必须互相配合使用，而且有严格步骤。

### 数据格式编码:
form-ulendcoded表单url编码

### 客户端提交
变量=值&变量=值&变量=值

### 服务器php

```
get-->_GET["变量名"]
post->_POST["变量名"]
```

7.ajax请求过程问题?
	程序怎么知道，数据什么时候回来，或者ajax和服务器交互到了哪一步了，请求状态如何

readyState属性可以监控ajax请求过程
	只读属性
	js解释器自动根据ajax状态自动赋值

当readyState值发生改变，触发onreadystatechange事件