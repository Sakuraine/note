Node.js不是一个JavaScript应用，而是一个JavaScript的运行环境，由C++语言编写。

REPL 命令

```
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



hellow-world.js

```js
const http = require('http'); // 引入HTTP模块

/**
 * 创建服务器
 */
const server = http.createServer((request, response) => {
  
})
```



