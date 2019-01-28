# Object对象

<table>
  <tr>
    <th colspan="3">对象属性类型</th>
  </tr>
  <tr>
    <td>属性名</td>
    <td>说明</td>
    <td>默认值</td>
  </tr>
  <tr>
    <td colspan="3">数据属性</td>
  </tr>
  <tr>
    <td>[[Configurable]]</td>
    <td>该属性是否能通过`delete`删除</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Enumerable]]</td>
    <td>该属性是否可枚举</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Writable]]</td>
    <td>该属性是否可更改值</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Value]]</td>
    <td>属性的数据值</td>
    <td>undefined</td>
  </tr>
  <tr>
    <td colspan="3">访问器属性</td>
  </tr>
  <tr>
    <td>[[Configurable]]</td>
    <td>该属性是否能通过`delete`删除</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Enumerable]]</td>
    <td>该属性是否可枚举</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Get]]</td>
    <td>在读取属性时调用的函数</td>
    <td>undefined</td>
  </tr>
  <tr>
    <td>[[Set]]</td>
    <td>在写入属性时调用的函数</td>
    <td>undefined</td>
  </tr>
</table>
##### Object.defineProperty(obj, prop, descriptor)

> 定义和用法

修改属性默认的特性

> 参数

`obj`

要在其上定义属性的对象。

`prop`

要定义或修改的属性的名称。

`descriptor`

将被定义或修改的属性描述符。

> 返回值

被传递给函数的对象



##### Object.defineProperties(obj, 'name', {})

> 定义和用法

修改属性默认的特性

> 参数

`obj`

要在其上定义属性的对象。

`prop`

要定义或修改的属性的名称。

`descriptor`

将被定义或修改的属性描述符。

> 返回值

被传递给函数的对象



##### Object.getOwnPropertyDescriptor(obj, prop)

> 定义和用法

读取属性默认的特性

> 参数

`obj`

需要查找的目标对象

`prop`

目标对象内属性名称（String类型）

> 返回值

如果指定的属性存在于对象上，则返回其属性描述符对象（property descriptor），否则返回 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。



## 原型

Object.prototype

> 是一个指针，指向该实例的原型对象。

> es5 规定这个指针叫做 `[[Prototype]]` ,在浏览器中使用 `__Proto_` 属性访问

Object.prototype.constructor

> 是原型对象上的一个属性，原型上最初只包含constructor属性

**isPrototypeOf**

> 如果[[Prototype]]指向调用 isPrototypeOf() 方法的对象（Object.prototype）,那么这个方法就会返回true