

# 修饰器

```javascript
@testable
class MyTestableClass {
  // ...
}

function testable(target) {
  target.isTestable = true;
}

MyTestableClass.isTestable // true
```

```js
@decorator
class A {}

// 等同于

class A {}
A = decorator(A) || A;
```

修饰器也可以传入参数

```js
function decorator(param = { bool: true }) {
  return function(target) {
    if (bool) {
      target.prototype.onChange = function (){
        console.log(bool);
			}
		}
	}
}

@decorator(false)
class Class {}
```



实现

文件结构

```
└── src
    ├── decorator.js  // 修饰器
    └── class.js			// 类
```

// decorator.js

```js
/**
 * 通用属性修饰
 * @param  {[type]} target [类]
 * @return {[type]}        [description]
 */
function decorator(target){
  target.prototype.onChange = function (value) {
    console.log(value);
  }
}

function noop()

export {
	decorator,
  noop,
}
```

// class.js

```js
import { decorator } from './decorator';

@decorator
class Class {
  
}
```

