# console对象

## 属性

### log

> 输出

```js
consoel.log('Hello World');
```

### info

> 输出

```js
console.info('Hello World');
```

### error

> 输出错误

```js
console.error('Hellow World');
```

### warn

> 输出警告

```js
console.warn('Hellow World');
```

### table

> 以表格的形式输出

```js
const list = [1, 2, 3];
console.table(list);
```

### dir

> 用来输出对象

```js
const obj = { name: 'yy' };
console.dir(obj);
```

### time和timeEnd

> 用于统计一段代码的执行时间

```js
console.time('time');

for (let i = 1; i < 10; i++) {
  console.log('Hello World');
}

console.timeEnd('time');
```

### group和groupEnd

> 用于分组输出的信息

```js
console.group('group');
console.groupEnd('group');
```

### count

> 用于计数

```js
for (let i = 0; i <= 10; i++) {
  console.count('count');
}
```

### trace

> 输出栈信息

## 格式化打印

### `%s`

> 字符串占位符

```js
const name = 'world';
console.log('Hellow %s', name);
```

### `%d`

> 整数占位符

```js
const number = 1;
console.log('I have %d dollar', number);
```

### `%f`

> 浮点数占位符

```js
const float = 1.01;
console.log('I have %f dollar', float);
```

### `%o`

> 对象占位符(注意是字母`o`，不是数字`0`)

```js
const obj = { name: 'World' };
console.log('Hellow %o', obj);
```

### `%c`

> CSS样式占位符

```js
console.log('%cHellow World', 'background: red');
```

