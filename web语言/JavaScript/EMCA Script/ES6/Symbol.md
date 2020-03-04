Symbol 值不能与其他类型的值进行运算，会报错
Symbol 值可以显式转为字符串。
Symbol 值也可以转为布尔值，但是不能转为数值。



##### Symbol.prototype.description

ES2019 提供了一个实例属性description，直接返回 Symbol 的描述。

Symbol 值作为对象属性名时，不能用点运算符。（点运算符后面总是字符串）
let mySymbol = Symbol();
a[mySymbol] = ‘hellow’;