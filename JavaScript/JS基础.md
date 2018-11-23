# JS基础

## 遍历

> map遍历

返回一个新的数组

```jsx
{['one', 'two'].map((type) => {
	const title = `hellow${type}`;
	return (
		<div>{title}</div>
	)
})}
```

> for...in

```js
for (value in Object) {
  
}
```

> for...of

```js
for (const item of Object) {
  
}
```

> forEach()

```
stringLIst.forEach()
```



## 字符串

**String.indexOf(String)**

> 返回值`Number`

‘ - ’ 在 str 字符串里第一次出现的索引

```js
const strindex = str.indexOf('-');
```

**String.lastIndexOf(String)**

> 返回值`Number`

‘ - ’ 在 str 字符串里最后一次出现的索引

```js
const strindex = str.lastIndexOf('-');
```

**String.substring(String, String)**

> 返回值`String`

str 字符串里索引 a 到 b 的字符

```js
const newStr = str.substring(a, b);
```

**parseInt(String, Number)**

>返回值`Number`

将`String`转换成10进制的`Number`

```js
const newStr = parseInt(str, 10);
```

**toFixed()**

> 返回值``



## 时间戳用法

对比时间和当前时间

hash

## console对象

```js
console.log()
```

弹出输入的对象

```js
console.table()
```

已表格形式弹出对象

trim()