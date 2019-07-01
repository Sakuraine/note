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



# 同步异步



# 事件机制



# `DOM` 事件



# `Redux` 原理



# `Vdom` 原理及`diff`算法



# `HTTPS` 安全性



# `HTTP` 状态码



# rem



# getComputedStyle



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