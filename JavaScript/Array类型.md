### Array类型

#### 监测数组

##### instanceof 操作符

>

```js
if (value instanceof Array){
	// 对数组执行某些操作
}
```

##### Array.isArray()

>

```js
if (Array.isArray(value)){
  // 对数组执行某些操作
}
```

支持 Array.isArray()方法的浏览器有 IE9+、Firefox 4+、Safari 5+、Opera 10.5+和 Chrome

#### 转换方法

...

#### 栈方法

...

#### 队列方法

...

#### 重排序方法

...

#### 操作方法

...

#### 位置方法

...

#### 迭代方法

##### every()

> 对数组中的每一项运行给定函数，如果该函数对每一项都返回 true，则返回 true

##### filter()

> 对数组中的每一项运行给定函数，返回该函数会返回 true 的项组成的数组

##### forEach()

> 对数组中的每一项运行给定函数。这个方法没有返回值

##### map()

> 对数组中的每一项运行给定函数，返回每次函数调用的结果组成的数组

##### some()

> 对数组中的每一项运行给定函数，如果该函数对任一项返回 true，则返回 true

#### 归并方法

##### reduce()

##### reduceRight()