# JavaScript Array 对象

## Array 对象

Array 对象用于在单个的变量中存储多个值。

### 创建

> 语法

```js
new Array();
new Array(size);
new Array(element0, element1, ..., elementn);
```

> 参数

参数 *size* 是期望的数组元素个数。返回的数组，length 字段将被设为 *size* 的值。

参数 *element* ..., *elementn* 是参数列表。当使用这些参数来调用构造函数 Array() 时，新创建的数组的元素就会被初始化为这些值。它的 length 字段也会被设置为参数的个数。

> 返回值

返回新创建并被初始化了的数组。

如果调用构造函数 Array() 时没有使用参数，那么返回的数组为空，length 字段为 0。

当调用构造函数时只传递给它一个数字参数，该构造函数将返回具有指定个数、元素为 undefined 的数组。

当其他参数调用 Array() 时，该构造函数将用参数指定的值初始化数组。

当把构造函数作为函数调用，不使用 new 运算符时，它的行为与使用 new 运算符调用它时的行为完全一样。

### Array 对象属性

| 属性                                                         | 描述                               |
| ------------------------------------------------------------ | ---------------------------------- |
| [constructor](http://www.w3school.com.cn/jsref/jsref_constructor_array.asp) | 返回对创建此对象的数组函数的引用。 |
| [length](http://www.w3school.com.cn/jsref/jsref_length_array.asp) | 设置或返回数组中元素的数目。       |
| [prototype](http://www.w3school.com.cn/jsref/jsref_prototype_array.asp) | 使您有能力向对象添加属性和方法。   |

### Array 对象方法

| 方法                                                         | 描述                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [concat()](http://www.w3school.com.cn/jsref/jsref_concat_array.asp) | 连接两个或更多的数组，并返回结果。                           |
| [join()](http://www.w3school.com.cn/jsref/jsref_join.asp)    | 把数组的所有元素放入一个字符串。元素通过指定的分隔符进行分隔。 |
| [pop()](http://www.w3school.com.cn/jsref/jsref_pop.asp)      | 删除并返回数组的最后一个元素                                 |
| [push()](http://www.w3school.com.cn/jsref/jsref_push.asp)    | 向数组的末尾添加一个或更多元素，并返回新的长度。             |
| [reverse()](http://www.w3school.com.cn/jsref/jsref_reverse.asp) | 颠倒数组中元素的顺序。                                       |
| [shift()](http://www.w3school.com.cn/jsref/jsref_shift.asp)  | 删除并返回数组的第一个元素                                   |
| [slice()](http://www.w3school.com.cn/jsref/jsref_slice_array.asp) | 从某个已有的数组返回选定的元素                               |
| [sort()](http://www.w3school.com.cn/jsref/jsref_sort.asp)    | 对数组的元素进行排序                                         |
| [splice()](http://www.w3school.com.cn/jsref/jsref_splice.asp) | 删除元素，并向数组添加新元素。                               |
| [toSource()](http://www.w3school.com.cn/jsref/jsref_tosource_array.asp) | 返回该对象的源代码。                                         |
| [toString()](http://www.w3school.com.cn/jsref/jsref_toString_array.asp) | 把数组转换为字符串，并返回结果。                             |
| [toLocaleString()](http://www.w3school.com.cn/jsref/jsref_toLocaleString_array.asp) | 把数组转换为本地数组，并返回结果。                           |
| [unshift()](http://www.w3school.com.cn/jsref/jsref_unshift.asp) | 向数组的开头添加一个或更多元素，并返回新的长度。             |
| [valueOf()](http://www.w3school.com.cn/jsref/jsref_valueof_array.asp) | 返回数组对象的原始值                                         |

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

LIFO（Last-In-First-Out，后进先出）

的数据结构，也就是最新添加的项最早被移除。而栈中项的插入(叫做推入)和移除(叫做
弹出)，只发生在一个位置——栈的顶部。

##### push()

> 定义和用法

push()方法可以像树的末尾添加一个或多个元素，并返回新的长度。

> 语法：

```js
arrayObject.push(newelement1,newelement2,....,newelementX)
```

> 参数：

| 参数        | 描述                             |
| ----------- | -------------------------------- |
| newelement1 | 必需。要添加到数组的第一个元素。 |
| newelement2 | 可选。要添加到数组的第二个元素。 |
| newelementX | 可选。可添加多个元素。           |

> 返回值

把指定的值添加到数组后的新长度。

> 说明

push() 方法可把它的参数顺序添加到 arrayObject 的尾部。

它直接修改 arrayObject，而不是创建一个新的数组。

push() 方法和 pop() 方法使用数组提供的先进后出栈的功能。

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