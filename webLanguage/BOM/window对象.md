# window对象

既是通过 JavaScript 访问浏览器窗口的接口，又是 ECMAScript 规定的 Global 对象。

## 全局作用域

所有在全局作用域中声明的变量、函数都会变成 window 对象的属性和方法。 

全局变量不能通过 delete 操作符删除，而直接在 window 对象上的定义的属性可以。

## 窗口关系及框架

如果页面中包含框架，则每个框架都拥有自己的 window 对象，并且保存在 frames 集合中

## 间歇调用

setTimeout()

clearTimeout()

## 间隔调用

setInterval()

clearInterval()