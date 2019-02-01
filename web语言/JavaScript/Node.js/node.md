# Node.js

Node.js不是一个JavaScript应用，而是一个JavaScript的运行环境，由C++语言编写。

Node.js 是**单进程单线程应用程序**，但是因为 V8 引擎提供的异步执行回调接口，通过这些接口可以处理大量的并发，所以性能非常高。

Node.js 几乎每一个 API 都是支持回调函数的。

Node.js 基本上所有的事件机制都是用设计模式中观察者模式实现。

Node.js 单线程类似进入一个while(true)的事件循环，直到没有事件观察者退出，每个异步事件都生成一个事件观察者，如果有事件发生就调用该回调函数.

Node.js 使用事件驱动模型，当web server接收到请求，就把它关闭然后进行处理，然后去服务下一个web请求。

当这个请求完成，它被放回处理队列，当到达队列开头，这个结果被返回给用户。

这个模型非常高效可扩展性非常强，因为webserver一直接受请求而不等待任何读写操作。（这也被称之为非阻塞式IO或者事件驱动IO）

在事件驱动模型中，会生成一个主循环来监听事件，当检测到事件时触发回调函数。

## 安装

### Mac OS

终端输入

```
brew install node
```



## REPL （Read Eval Print Loop:交互式解释器）

### 命令

```
- 进入node交互模式
	node

- 退出当前终端
	control + c
	.exit

- 退出 Node REPL
	control + c 按下两次
	control + d

- 查看输入的历史命令
	向上/向下 键

- 列出当前命令
	tab 键

- 列出使用命令
	.hlep

- 退出多行表达式
	.break
	.clear

- 保存当前的 Node REPL 会话到指定文件
	.save <filename>

- 载入当前 Node REPL 会话的文件内容
	.load <filename>
```

## 模块

### require引入模块

```js
// 引入原生模块
const http = require('http');
// 变量名 = require('引入的模块名');

// 引入文件模块
const fileName = require('./fileName');
// 变量名 = require('引入的文件路径，可以省略后缀名');
```

### exports导出模块

```js
const util = {
	/**
	 * 方法名
	 * @param  {[type]} arr [description]
	 * @return {[type]}			[description]
	 */
	functionName: function(arr) {
		return arr;
	}
}

module.exports = util;
```

hellow-world.js

```js
const http = require('http'); // 引入HTTP模块
const events = require('events'); // 引入events模块

// 创建 eventEmitter 对象
var eventEmitter = new events.EventEmitter();

// 绑定事件及事件的处理程序
eventEmitter.on('eventName', eventHandler);

// 触发事件
eventEmitter.emit('eventName');

/**
 * 创建服务器
 */
const server = http.createServer((request, response) => {
  
})
```



- node的特点

事件驱动

异步、非阻塞I/O

单线程

- node的软肋

CPU密集型应用、模版渲染、压缩/解压缩、加/解密