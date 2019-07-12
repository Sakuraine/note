# this

## 绑定方式

- 默认绑定

  ```js
  var name = 'a';
  
  function show() {
    var name = 'name';
    console.log(this.name);
  }
  
  show(); // a
  ```

  > `this` 绑定在全局对象上

- 隐式绑定

  ```js
  function show() {
    var name = 'a';
    console.log(this.name);
  }
  
  var name = 'b';
  
  var obj = {
    name: 'c',
    showName: show,
  }
  
  obj.showName(); // c
  ```

  > `this` 指向调用的 `obj` 对象上

- 显示绑定

  ```js
  var obj = {
    name: 'a',
  }
  
  var name = 'b';
  
  function show() {
    var name = 'c';
    console.log(this.name);
  }
  
  show.call(obj); // a
  ```

  > 通过 `call`、`apply`、`bind`显示地改变调用的this对象

- `new` 绑定/构造函数调用

  ```js
  function createObj(name) {
  	this.name = name;
  }
  
  var obj = new createObj('a');
  
  console.log(obj.name); // a
  ```

  > 通过构造函数或者 `new` 操作符创建的对象，`this` 会绑定到创建的实例上

## 改变 `this`

```js
var name = 'a';
var obj = {
  name: 'b',
};

function showName(arg1, arg2) {
  var name = 'c';
  console.log(name, arg1, arg2);
}

showName('name1', 'name2'); // a name1 name2
showName.call(obj, 'name1', 'name2'); // b name1 name2
showName.apply(obj, ['name1', 'name2']); // b name1 name2
showNmme.bind(obj, 'name1', 'name2')(); // b name1 name2
```



**绑定的优先级为 `new` > 显示绑定  > 隐式绑定 > 默认绑定**

> 普通函数的 `this` 谁调用指向谁，它是运行期间绑定的，和它声明的环境无关，只和调用它的对象有关

> 箭头函数没有 `this` 绑定，谁创建方法指向谁

# 箭头函数

1. 箭头函数不能用于构造函数

2. 箭头函数没有 `prototype` 属性

3. 箭头函数不能绑定 `arguments`

4. 箭头函数不能绑定 `this`，其内部的this绑定到它的外围作用域，所以也不能使用 `call` 或 `apply` 来改变其运行的作用域

   ```js
   window.name = "window";
   
   let name = "name";
   let obj = {
       name: "obj",
       getName: () => {
           return this.name;//this指向window
       }
   };
   
   obj.getName(); // window
   ```

# 变量提升



# 原型链 && 闭包

> 利用原型让一个引用类型继承另一个引用类型的属性和方法

## 原型

### 继承方式

> OO语言支持两种继承方式：接口继承和实现继承

#### 接口继承

只继承方法签名

#### 实现继承

继承实际的方法，**`ECMAScript` 只支持实现继承，而且其实现集成主要是依靠原型链来实现的**

```js
function SuperType() {
  this.property = true;
}

SuperType.prototype.getSuperValue = function() {
  return this.property;
};

function SubType() {
  this.subproperty = false;
}

// 继承了SuperType
SubType.prototype = new SuperType();

SubType.prototype.getSubValue = function() {
  return this.subproperty;
};

var instance = new Subtype();
alert(instance.getSuperValue()); // true;
```

**`prototype` 和 `__proto__` 的区别**

`prototype` 是每个**函数**才有的属性

`__proto__` 是每个**对象**都有的属性

# 同步异步



# 事件机制



# `DOM` 事件



# 防抖和节流

防抖是延迟执行，如果再触发则重新延迟

节流是一个时间内只执行一次



# 中间件



# `Redux` 原理

## 为什么要用 `Redux`

`react` 中数据是单向数据流，为了解决两个非父子组件之间的通信

## `Redux` 设计理念

`Redux` 是将整个应用状态存储到一个地方上称为 `store` ,里面保存着一个状态树 `store tree` ,组件可以派发 `dispatch` 行为 `action` 给 `store`,而不是直接通知其他组件，组件内部通过订阅 `store` 中的状态 `state` 来刷新自己的视图。

> `Redux`工作流

```mermaid
graph LR

c[Action Creators] --> |转发 action| a
a[Store] --> |state 变化重新渲染| b[React Components]  
a --> |传入 state 和 action| d[Reducers]
d --> |get newState| a
```

## `Redux` 三大原则

1. 唯一数据源

   ​	整个应用的 `state` 都被存储到一个状态树里面，并且这个状态树，只存在于唯一的 `store` 中

2. 保持只读状态

   ​	`state` 是只读的，唯一改变 `state` 的方法就是触发 ·action，`action` 是一个用于描述以发生时间的普通对象

3. 数据改变只能通过纯函数来执行

   ​	使用纯函数来执行修改，为了描述 `action` 如何改变 `state` 的，你需要编写 `reducers`

## `Redux`概念解析

### `Store`

- `store` 就是保存数据的地方，你可以把它看成一个数据，整个应用智能有一个 `store`

- `Redux` 提供 `createStore` 这个函数，用来生成 `Store`

  ```js
  import { createStore } from 'redux';
  
  const store = createStore(fn);
  ```

### `State`



# `Vdom` 原理及`diff`算法



# `HTTPS` 安全性



# `HTTP` 状态码



# `rem`



# `getComputedStyle`



# ***规范***

大标题使用一级标题 `#`

细分往下使用标题 `# * n`

特殊情况使用斜体 `**`

注释使用 `>`

代码示例使用代码块，并在代码块注明代码语言类型

```language
…
```

文字内的变量、操作符等使用``