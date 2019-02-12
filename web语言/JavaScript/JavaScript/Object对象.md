# Object对象

## 创建对象的模式

### 1.工厂模式

> 工厂模式虽然解决了创建多个相似对象的问题，但却没有解决对象识别的问题(即怎样知道一个对象的类型)

- 在方法内显式的创建一个对象，将属性和方法赋值给新创建的对象
- 创建后需要使用 `return` 语句返回该对象

#### 缺点

- 无法识别对象

#### Example

```js
function createPerson(name, age, job) {
  var person = new Object;
  person.name = name;
  person.age = age;
  person.job = job;
  person.sayName = function () {
    console.log(this.name);
  }
  return person;
}

var yy = createPerson('yy', 21, 'coder');
console.log(yy); // { name: 'yy', age: 21, job: 'coder', sayName: [Function] }
```



### 2.构造函数模式

> 创建特定类型的对象

- 没有显示的创建对象
- 直接将属性和方法赋值给 `this` 对象
- 没有 `return` 语句
- 构造函数的函数名首字母应该使用大写
- 创建实例时使用 `new` 操作符

#### 缺点

- 不同实例上的同名函数是不相等的，导致不同的作用域链和标识符解析

#### Example

```js
function Person (name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;
  this.sayName = function () {
    console.log(this.name);
  }
}

var yy = new Person('yy', 21, 'coder');
console.log(yy); // { name: 'yy', age: 21, job: 'coder', sayName: [Function] }
```



### 3.原型模式

> 通过将属性和方法添加到原型对象上，使所有实例共享方法属性

- 所有对象实例都共享它包含的属性和方法

#### 缺点

- 创建的实例都会有相同的属性值
- 当改变一个实例的属性值时，其他的实例所对应的属性值也会改变

#### Example

```js
function Person() {
}

Person.prototype = {
  constructor: Person,
  name: 'yy',
  age: '21',
  sayName: function () {
    console.log(this.name);
  }
}

var person = new Person();
```



### 4.组合使用构造函数模式和原型模式

> 使用构造函数模式定义实例属性，使用原型模式定义方法和共享的属性

**这种构造函数模和原型混成的模式，是目前在ECMAScript中使用最广泛、认同度最高的的一种创建自定义类型的方法，可以说，这是用来定义引用类型的一种默认模式**

- 每个实例都会有自己的一份实例属性的副本
- 共享对方法的引用，最大限度地节省内存

#### 缺点

- 代码量太多，ES6增加了class类代替

#### Example

```js
function Person(name, age, job) {
  this.name = name;
  this.age = age;
  this.job = job;
  this.friends = ['Bob'];
}

Person.prototype = {
  constructor: Person,
  sayName = function () {
    console.log(this.name);
  }
}

var person1 = new Person('yy', 18, 'Doctor');
var person2 = new Person('zz', 29, 'Coder');

person1.friends.push('Van');
console.log(person1.friends); // 'Bob, Van'
console.log(person2.friends); // 'Bob'
console.log(person1.sayName === person2.sayName); // ture
```



### 5.动态原型模式

> 



### 6.寄生构造函数模式



### 7.稳妥构造函数模式



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

修改属性默认的特性。

> 参数

`obj`

要在其上定义属性的对象。

`prop`

要定义或修改的属性的名称。

`descriptor`

将被定义或修改的属性描述符。

> 返回值

被传递给函数的对象。



##### Object.defineProperties(obj, 'name', {})

> 定义和用法

修改属性默认的特性。

> 参数

`obj`

要在其上定义属性的对象。

`prop`

要定义或修改的属性的名称。

`descriptor`

将被定义或修改的属性描述符。

> 返回值

被传递给函数的对象。



##### Object.getOwnPropertyDescriptor(obj, prop)

> 定义和用法

读取属性默认的特性。

> 参数

`obj`

需要查找的目标对象。

`prop`

目标对象内属性名称（String类型）

> 返回值

如果指定的属性存在于对象上，则返回其属性描述符对象（property descriptor），否则返回 [`undefined`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/undefined)。



##### Object.keys(obj)

> 定义和用法

返回一个由一个给定对象的自身可枚举属性组成的数组，数组中属性名的排列顺序和使用 [`for...in`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in) 循环遍历该对象时返回的顺序一致。

> 参数

`obj`

要返回其枚举自身属性的对象。

> 返回值

一个表示给定对象的所有可枚举属性的字符串数组。



##### Object.getOwnPropertyNames(obj)

> 定义和用法

返回一个由指定对象的所有自身属性的属性名（包括不可枚举属性但不包括Symbol值作为名称的属性）组成的数组。

> 参数

`obj`

一个对象，其自身的可枚举和不可枚举属性的名称被返回。

> 返回值

在给定对象上找到的自身属性对应的字符串数组。



## 原型

Object.prototype

> 是一个指针，指向该实例的原型对象。

> es5 规定这个指针叫做 `[[Prototype]]` ,在浏览器中使用 `__Proto_` 属性访问，一个实例的`__proto__`

Object.prototype.constructor

> 是原型对象上的一个属性，原型上最初只包含constructor属性

**isPrototypeOf**

> 如果[[Prototype]]指向调用 isPrototypeOf() 方法的对象（Object.prototype）,那么这个方法就会返回true