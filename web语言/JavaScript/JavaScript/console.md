# console对象

## 属性

##### log

> 输出

```js
consoel.log('%d%s'); // %d表示数字、%s表示字符串
```

##### info

> 输出

```js
console.info('Hello World!');
```

##### error

> 输出错误

##### warn

> 输出警告

##### table

> 以表格的形式输出

##### dir

> 用来输出对象

##### time和timeEnd

> 用于统计一段代码的执行时间

```js
console.time('time');

for (let i = 1; i < 10; i++) {
  console.log('Hello World!');
}

console.timeEnd('time');
```

##### trace

> 输出栈信息

