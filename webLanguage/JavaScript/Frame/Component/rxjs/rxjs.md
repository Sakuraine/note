# Rxjs

https://github.com/mocheng/dissecting-rxjs

# 函数响应式编程

> 解决的问题

- 如何控制大量代码的复杂度
- 如何保持代码可读
- 如何处理异步操作

代表流的变量标识符，用`$`结尾（芬兰式命名法）

> 实现差异

- jQuery的实现，代码看起来就是一串指令的组合
- RxJS的实现，代码是一个个函数，每个函数只是对输入的参数做了相应，然后返回结果

> 思想

- 函数式
- 响应式

## 函数式编程

### 什么是函数式编程

#### 函数式编程对函数使用的要求

- 声明式
- 纯函数
  - 函数的执行过程完全由输入参数决定，不会受除参数之外的任何数据影响
  - 函数不会修改任何外部状态，比如修改全局变量或传入的参数对象
- 数据不可变性

##### 声明式

想要做什么

> 命令式

怎么去做

##### 纯函数

> 不纯函数的部分表现（纯函数的相反）

- 改变全局变量的值
- 改变输入参数引用的对象
- 读取用户输入，比如调用了alert或者confirm函数
- 抛出一个异常
- 网络输入/输入操作，比如通过AJAX调用一个服务器的API
- 操作浏览器的DOM

> 如何判断函数纯不纯

假设将一个函数调用替换为一个预期返回的常数，程序运行结果是否一样（如果运行结果不一样说明函数修改了函数外的值）

> 满足纯函数的特性也叫做引用透明度
>
> 所谓的纯函数，做的事情就是输入参数到返回结果的一个映射，不要产生副作用

##### 数据不可变

> 通过产生新数据，来实现”变化“，当我们需要数据状态发生改变时，保持原有数据不变，产生一个新的数据来体现这种变化

### 函数式编程和面向对象编程的比较

面向对象的方法把状态的改变封装起来，以此达到让代码清晰的目的

函数式编程则是尽量减少变化的部分，以此让代码逻辑更加清晰

> 面向对象的缺点

数据的修改历史完全被隐藏了

## 响应式编程

>在计算中，响应式编程或反应式编程（英語：Reactive programming）是一种面向数据串流和变化传播的声明式编程范式。 这意味着可以在编程语言中很方便地表达静态或动态的数据流，而相关的计算模型会自动将变化的值通过数据流进行传播。

## Reactive Extension

> Reactive Extension，简称Rx，值的是实践响应式编程的一套工具
>
> Rx是一套通过可监听流来做异步编程的API
>
> Rx诞生的主要目的虽然是解决异步处理的问题，依然适合同步的数据处理，不关注是同步还是异步
>
> Reactive Extension扩展了那些不支持响应式编程的语言的功能
>
> RxJS就是用JavaScript语言实现的Reactive Extension

## RxJS是否是函数响应式编程

> 函数响应式编程 Functional Reactive Programming 简称FRP
>
> RxJS属于FRP，但不是FRP

FRP包含两个元素：

- 指称性
- 临时的连续性

> 正统FRP认为，一个系统如果能被称为FRP，除了要有Functional和Reactive的特点，还必须要能够支持两个时间可以同时发生，这就是指称性的要求

## 函数响应式编程的优势

> 特点

- 数据流抽象了很多现实问题
- 擅长处理异步操作
- 把复杂问题分解成简单问题的组合

网页应用的前端领域中的数据流：

- 网页DOM的事件
- 通过WebSocket获得的服务器端推送消息
- 通过AJAX获得服务器端的数据资源
- 网页的动画显示

RxJS擅长处理异步操作，因为它对数据采取“推”的处理方式，当一个数据产生的时候，被推送到对应的处理函数，这个处理函数不用关心数据是同步产生的还是异步产生的

# RxJS入门

## RxJS的版本和运行环境

> 目前被广泛使用的RxJS版本有两个：v4和v5，这两个版本的API很相似，但是也有巨大的差别

1. npm安装

   V5

   ```shell
   npm install rxjs
   ```

   v4

   ```shell
   npm install rx
   ```

   1. 导入

      ```jsx
      // ES6的import语法
      import Rx from 'rxjs';
      // 或者
      import Rx from 'rxjs/Rx';
      
      // CommonJS风格的require函数
      const Rx = require('rxjs');
      
      // 导入需要的功能
      import { Observable } from 'rejs/Observable';
      const Observable = reqrire('rejs.Observable').Obserbable;
      
      ```

   2. 

2. 引入RxJS URL

   1. 引入指定版本

      ```js
      <script src="https://unpkg.com/rxjs@5.5.2/bundles/Rx.min.js"></script>
      ```

   2. 跳转到最新版本的RxJS内容

      ```js
      <script src="https://unpkg.com/rxjs/bundles/Rx.min.js"></script>
      ```

   > 使用公共CDN还有一个好处，可以充分利用浏览器的缓存机制，如果用户在访问你的网页应用之前访问过其他网站，而且那些网站也使用了一样的CDN静态资源，那么浏览器可以直接从本地缓存中获取这些资源，省去了下载时间。
   >
   > 不过，从CDN获取RxJS也有缺点，那就是RxJS要下载就要全部下载，没办法根据应用的需要定制。

## Observable和Observer

> Observable 被观察者
>
> Observer 观察者

RxJS中的数据流就是Observable对象，Observable实现了下面两种设计模式：

- 观察者模式（Observer Pattern）
- 迭代器模式（Iterator Pattern）

### 观察者模式

- 发布者 Publisher

  > 负责生产事件，通知所有注册挂上号的观察者，不关心观察者如何处理事件

- 观察者 Observer

  > 可以被注册上某个发布者，只管接收到事件之后就处理，不关心数据如何产生

观察者模式只需要关注三个小问题：

1. 如何产生事件，这是发布者的责任，在RxJS中是Observable


