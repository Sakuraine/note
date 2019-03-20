# ES2015

## Babel转码

函数拓展

let const数据结构

map数据结构

set数据结构

## 严格模式

### 作用

1. 消除Javascript语法的一些不合理、不严谨之处，减少一些怪异行为；
2. 消除代码运行的一些不安全之处，保证代码运行的安全；
3. 提高编译器效率，增加运行速度；
4. 为未来新版本的Javascript做好铺垫；

### 进入严格模式

1. "use strict";
   1. 将"use strict"放在脚本文件的第一行，则整个脚本都将以"严格模式"运行；
   2. 将"use strict"放在函数体的第一行，则整个函数以"严格模式"运行；

2. 使用Class时自动转换为全局严格模式；

### 要求

1. 不允许使用未声明的变量；（对象也是一个变量）
2. 不允许删除变量或对象；
3. 不允许删除函数；
4. 不允许变量重名；
5. 不允许使用八进制；
6. 不允许使用转义字符；
7. 不允许对只读属性赋值；
8. 不允许对一个使用getter方法读取的属性进行赋值；
9. 不允许删除一个不允许删除的属性；
10. 禁止使用with语句；
11. 变量名不能使用 "eval" 字符串；
12. 变量名不能使用 "arguments" 字符串；
13. 由于一些安全原因，在作用域 eval() 创建的变量不能被调用；
14. 禁止this关键字指向全局对象；
15. 使用构造函数时，如果忘了加new，this不再指向全局对象，而是报错；
16. 新增了一些保留字；



## 变量

### let

1. 隶属于块级作用域，块级作用域外不可见；
2. 不存在“变量提升”与死区；
3. 同一作用域内不得存在名称相同的变量；
4. 当声明为全局变量时不会作为全局对象的属性；
5. 不允许重复声明；

### const

1. 声明常量；（块级作用域，在一个作用域里只能有一个且不可重新声明）
2. 在声明时必须赋值；
3. 不能改变值，否则会报错；
4. 不同作用域声明的常量互不影响；
5. 可以定义成对象，且同样不可重写；但对象的属性不受影响；
6. 可以用来定义数组，切可以向数组内填充数据，但是，将一个新数组赋给变量会引发错误

### 块级作用域

1. 内层变量不会覆盖外层变量；
2. 用来计数的循环变量不会泄露为全局变量；
3. ES6 允许块级作用域的任意嵌套，且外层作用域无法读取内层作用域的变量；
4. 内层作用域可以定义外层作用域的同名变量

#### 块级作用域与函数声明

1. ES5 规定，函数只能在顶层作用域和函数作用域之中声明，不能在块级作用域声明。（但是浏览器为了兼容旧代码，依然支持）
2. ES6 引入了块级作用域，明确允许在块级作用域之中声明函数。ES6 规定，块级作用域之中，函数声明语句的行为类似于`let`，在块级作用域之外不可引用。



## 变量的解构赋值

> 只要等号两边的模式相同，左边的变量就会被赋予对应的值

> 如果解构不成功，变量的值就等于`undefined`

### 默认值

解构赋值允许指定默认值。

ES6 内部使用严格相等运算符（`===`），判断一个位置是否有值。所以，只有当一个数组成员严格等于`undefined`，默认值才会生效。

```js
var {x = 3} = {};
x // 3
```

如果默认值是一个表达式，那么这个表达式是惰性求值的，即只有在用到的时候，才会求值

```js
function f() { 
  console.log('aaa');
}
let [x = f()] = [1];
```

因为x能取到值，所以函数f根本不会执行

解构赋值允许等号左边的模式之中，不放置任何变量名。

### 字符串的解构赋值

字符串被转换成了一个类似数组的对象

```js
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"

const [a, ...b] = 'hello';
a // 'h'
b // ["e", "l", "l", "o"]
```

类似数组的对象都有一个`length`属性，因此还可以对这个属性解构赋值。

```js
let {length : len} = 'hello';
len // 5
```

### 数值和布尔值的解构赋值

解构赋值的规则是，只要等号右边的值不是对象或数组，就先将其转为对象。由于`undefined`和`null`无法转为对象，所以对它们进行解构赋值，都会报错。

```js
let {toString: s} = 123;
s === Number.prototype.toString // true

let {toString: s} = true;
s === Boolean.prototype.toString // true
```

### 函数参数的解构赋值

```js
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3

[[1, 2], [3, 4]].map(([a, b]) => a + b);
// [ 3, 7 ]
// 等同于
[[1, 2], [3, 4]].map(([a, b] = []) => a + b);

[{a: 1, b: 2}, {a: 3, b: 4}].map(({a, b} = {}) => a + b)
// [ 3, 7 ]
// 等同于
[{a: 1, b: 2}, {a: 3, b: 4}].map(item) => {
  const {a, b} = item;
  return a + b;
})
```

上面代码中，函数`add`的参数表面上是一个数组，但在传入参数的那一刻，数组参数就被解构成变量`x`和`y`。对于函数内部的代码来说，它们能感受到的参数就是`x`和`y`。

### 解构赋值的用途

#### 交换变量的值

```js
let x = 1;
let y = 2;

[x, y] = [y, x];
```

#### 从函数返回多个值

函数只能返回一个值，如果要返回多个值，只能将它们放在数组或对象里返回。有了解构赋值，取出这些值就非常方便。

```js
// 返回一个数组

function example() {
  return [1, 2, 3];
}
let [a, b, c] = example();

// 返回一个对象

function example() {
  return {
    foo: 1,
    bar: 2
  };
}
let { foo, bar } = example();
```

#### 函数参数的定义

解构赋值可以方便地将一组参数与变量名对应起来。

```js
// 参数是一组有次序的值
function f([x, y, z]) { ... }
f([1, 2, 3]);

// 参数是一组无次序的值
function f({x, y, z}) { ... }
f({z: 3, y: 2, x: 1});
```

#### 提取JSON数据

解构赋值对提取 JSON 对象中的数据，尤其有用。

```javascript
let jsonData = {
  id: 42,
  status: "OK",
  data: [867, 5309]
};

let { id, status, data: number } = jsonData;

console.log(id, status, number);
// 42, "OK", [867, 5309]
```

#### 函数参数的默认值

```js
function foo({ a } = {}) {
  //...
}
```

#### 遍历 Map 结构

任何部署了 Iterator 接口的对象，都可以用`for...of`循环遍历。Map 结构原生支持 Iterator 接口，配合变量的解构赋值，获取键名和键值就非常方便。

```js
const map = new Map();
map.set('first', 'hello');
map.set('second', 'world');

for (let [key, value] of map) {
  console.log(key + " is " + value);
}
// first is hello
// second is world
```

如果只想获取键名，或者只想获取键值，可以写成下面这样。

```js
// 获取键名
for (let [key] of map) {
  // ...
}

// 获取键值
for (let [,value] of map) {
  // ...
}
```

#### 输入模块的指定方法

加载模块时，往往需要指定输入哪些方法。解构赋值使得输入语句非常清晰。

```javascript
const { SourceMapConsumer, SourceNode } = require("source-map");
```



## 字符串的扩展

### 字符的unicode表示法

JavaScript 允许采用`\uxxxx`形式表示一个字符，其中`xxxx`表示字符的 Unicode 码点。

```js
"\u0061"
// "a"
```

但是，这种表示法只限于码点在`\u0000`~`\uFFFF`之间的字符。超出这个范围的字符，必须用两个双字节的形式表示。

上面代码表示，如果直接在`\u`后面跟上超过`0xFFFF`的数值（比如`\u20BB7`），JavaScript 会理解成`\u20BB+7`。由于`\u20BB`是一个不可打印字符，所以只会显示一个空格，后面跟着一个`7`。

ES6 对这一点做出了改进，只要将码点放入大括号，就能正确解读该字符。

```js
"\u{20BB7}"
// "𠮷"

"\u{41}\u{42}\u{43}"
// "ABC"

let hello = 123;
hell\u{6F} // 123

'\u{1F680}' === '\uD83D\uDE80'
// true
```

```javascript
'\z' === 'z'  // true
'\172' === 'z' // true
'\x7A' === 'z' // true
'\u007A' === 'z' // true
'\u{7A}' === 'z' // true
```

### 新扩展的方法

##### `str.includes(string, index)`

> 用法

​	用来确定一个字符串是否包含在另一个字符串中

> 参数

​	string | String

​	需要检测是否存在的字符串

​	index | Number

​	索引

> 返回值

​	返回布尔值，表示是否找到了参数字符串。



##### `str.startsWith(string, index)`

> 用法

​	用来确定一个字符串是否在另一个字符串的头部

> 参数

​	string | String

​	需要检测是否存在的字符串

​	index | Number

​	索引

> 返回值

​	返回布尔值，表示参数字符串是否在原字符串的头部；



##### `str.endsWith(string, index)`

> 用法

​	用来确定一个字符串是否在另一个字符串的尾部

> 参数

​	string | String

​	需要检测是否存在的字符串

​	index | Number

​	索引

> 返回值

​	返回布尔值，表示参数字符串是否在原字符串的尾部；如果传入第二个参数，是从索引为index的位置往前查找



##### `str.repeat(count)`

> 用法

​	构造并返回一个新字符串，该字符串包含被连接在一起的指定数量的字符串的副本。

> 参数

​	conunt | Number

​	介于0和正无穷大之间的整数 : [0, +∞) 。表示在新构造的字符串中重复了多少遍原字符串。

> 返回值

​	 包含指定字符串的指定数量副本的新字符串。

> 注意

​	count不能为负数和 Infinity ，如果是小数，则去尾去整

​	count如果为NaN，则等同于0

##### `normalize()`

```js
'\u01D1'.normalize() === '\u004F\u030C'.normalize()
```



##### `str.padStart(targetLength, str1, str2...)`

> 用法

​	用另一个字符串填充当前字符串(重复，如果需要的话)，以便产生的字符串达到给定的长度。填充从当前字符串的开始(左侧)应用的。

> 参数

​	targetLength | Number

​	当前字符串需要填充到的目标长度。如果这个数值小于当前字符串的长度，则返回当前字符串本身。

​	str1、str2… | String

​	填充字符串。如果字符串太长，使填充后的字符串长度超过了目标长度，则只保留最左侧的部分，其他部分会被截断。此参数的缺省值为 " "。



##### `Str.matchAll(regexp)`

> 用法



### 模版字符串

> 语法

```js
${变量名}
```

> Example

模板字符串中嵌入变量，需要将变量名写在`${}`之中。

```js
const a = 'yy';
console.log(`my name is ${a}`); // my name is yy
```

大括号内部可以放入任意的 JavaScript 表达式，可以进行运算，以及引用对象属性。

```js
let x = 1;
let y = 2;

`${x} + ${y} = ${x + y}`
// "1 + 2 = 3"
```

模板字符串之中还能调用函数。

```js
function fn() {
  return "Hello World";
}

`foo ${fn()} bar`
// foo Hello World bar
```

如果大括号中的值不是字符串，将按照一般的规则转为字符串。比如，大括号中是一个对象，将默认调用对象的`toString`方法。

```js
var obj = {};
`${obj}` // "[object Object]"
```

如果需要引用模板字符串本身，在需要时执行，可以像下面这样写。

```js
// 写法一
let str = 'return ' + '`Hello ${name}!`';
let func = new Function('name', str);
func('Jack') // "Hello Jack!"

// 写法二
let str = '(name) => `Hello ${name}!`';
let func = eval.call(null, str);
func('Jack') // "Hello Jack!"
```

如果在模板字符串中需要使用反引号，则前面要用反斜杠转义。

如果使用模板字符串表示多行字符串，所有的空格和缩进都会被保留在输出之中。

模板字符串甚至还能嵌套。



#### 标签模板

它可以紧跟在一个函数名后面，该函数将被调用来处理这个模板字符串。这被称为“标签模板”功能（tagged template）。

标签模板其实不是模板，而是函数调用的一种特殊形式。“标签”指的就是函数，紧跟在后面的模板字符串就是它的参数。

```js
alert`123`
// 等同于
alert(123)
```

如果模板字符里面有变量，会将模板字符串先处理成多个参数，再调用函数。

```js
let a = 5;
let b = 10;

tag`Hello ${ a + b } world ${ a * b }`;
// 等同于
tag(['Hello ', ' world ', ''], 15, 50);
```

将各个参数按照原来的位置拼合回去

```js
let total = 30;
let msg = passthru`The total is ${total} (${total*1.05} with tax)`;

function passthru(literals) {
  let result = '';
  let i = 0;

  while (i < literals.length) {
    result += literals[i++];
    if (i < arguments.length) {
      result += arguments[i];
    }
  }

  return result;
}

msg // "The total is 30 (31.5 with tax)"
```

`passthru`函数采用 rest 参数的写法如下。

```javascript
function passthru(literals, ...values) {
  let output = "";
  let index;
  for (index = 0; index < values.length; index++) {
    output += literals[index] + values[index];
  }

  output += literals[index]
  return output;
}
```



### 函数的扩展

#### 箭头函数

1. 如果只有一个参数，`()` 可以省略；
2. 如果只有一条return,`{}` 可以省略；

> 语法

```js
var f = () => 5;
// 等同于
var f = function () { return 5 };

var sum = (num1, num2) => num1 + num2;
// 等同于
var sum = function(num1, num2) {
  return num1 + num2;
};
```


### class

1. 可以看作构造函数的另一种写法；
2. 构造函数的`prototype`属性，在 ES6 的“类”上面继续存在；

# ES2016

指数操作符