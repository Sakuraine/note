##### call

**`call()`** 方法调用一个函数, 其具有一个指定的`this`值和分别地提供的参数(**参数的列表**)

> 语法

```js
fun.call(thisArg, arg1, arg2, ...)
```

> 参数

`thisArg`

调用绑定函数时作为`this`参数传递给目标函数的值

`arg1, arg2, ...`

指定的参数列表



##### apply

```js
func.apply(thisArg, [argsArray])
```



##### bind

**`bind()`**方法创建一个新的函数，在调用时设置`this`关键字为提供的值。并在调用新函数时，将给定参数列表作为原函数的参数序列的前若干项。

```js
func.bind(thisArg[, arg1[, arg2[, ...]]])
```

