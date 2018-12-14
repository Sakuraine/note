# JS基础

## 迭代方法

### every()

### filter()

### forEach()

### map()

### some()

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

**String.parseInt(String, Number)**

>返回值`Number`

将`String`转换成10进制的`Number`

```js
const newStr = parseInt(str, 10);
```

**toFixed()**

> 返回值``

**String.match(String, Reg)**

>

## RegExp对象

### [正则](https://baike.baidu.com/item/正则表达式/1700215?fr=aladdin)

## 时间戳用法

对比时间和当前时间

hash

## canvs画布

drawImage方法

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

## 树状结构

```jsx
const Tree = (tree, bool = true) => {
  return tree.map((item) => {
		if (item.children) {
      return (
        <div style={{ paddingLeft: '20px' }}>
          <span value={item.id} title={item.name} key={item.id} disabled={bool && item.id === '0'} />
    			{Tree(item.children)}
      	</div>
      );
    }
    return <span value={item.id} title={item.name} key={item.id} />;
  });
};
```

**Object.assign()**

用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。它将返回目标对象。

```js
const newObj = Object.assign({}, { a: 1, b: 2}, { c: 3 }); //        
```

