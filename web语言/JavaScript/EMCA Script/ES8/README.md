# EMCAScript 2017 新增

### Object.values()

> 语法

```js
Object.values(obj)
```

> 参数

`obj`

被返回可枚举属性的对象。（如果参数是一个 `String` 则会把这个字符串遍历出来）

> 返回值

一个包含对象自身的所有可枚举属性值的数组。

不会返回从原型链上继承的属性

### Object.entries()

> 语法

```
Object.entries(obj)
```

> 参数

`obj`

可以返回其可枚举属性的键值对的对象。

> 返回值

给定对象滋生可枚举属性的键值对数组。

### Object.getOwnPropertyDescriptors()





### String.prototype.padStart()

> 语法

```js
str.padStart(targetLength [, padString])
```

> 参数

`targetLength`

当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。

`padString` （可选）

填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）。

> 返回值

在原字符串开头填充指定的填充字符串直到目标长度所形成的新字符串。

### String.prototype.padEnd()

> 语法

```js
str.padEnd(targetLength [, padString])
```

> 参数

`targetLenth`

当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。

`padString` （可选）

填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "（U+0020）。

> 返回值

在原字符串末尾填充指定的填充字符串直到目标长度所形成的新字符串。

### Async Functions

异步函数

