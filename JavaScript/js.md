# JavaScript原理

## 编译原理

### 引擎

`负责所有JavaScript编译及执行`

### 编译器

`负责语法分析及代码生成`

### 作用域

`负责收集并维护由所有声明的标识符（变量）组成的一系列查询`

`实施一套非常严格的规则，确定当前执行的代码对这些标识符的访问权限`

- 查询

  - LHS查询
    - 查找的目的是对变量进行赋值

  - RHS查询
    - 查找的目的是获取变量的值

不成功的 RHS 引用会导致抛出 `ReferenceError` 异常。

不成功的 LHS 引用会导致自动隐式地创建一个全局变量（非严格模式下）。

该变量使用 LHS 引用的目标作为标识符，或者抛出 `ReferenceError` 异常（严格模式下）。

#### 工作模型

##### 词法作用域



##### 动态作用域



## 编译过程

- 分词/词法分析（Tokenizing/Lexing）
  - 词法单元（token）
  - 分词（tokenizing）和词法分析（Lexing）
- 解析/语法分析（Parsing）

> 抽象语法树 `Abstract Syntax Tree,AST`

```js
var a = 2;
/**
 * 上面程序的抽象语法树：
 * VariableDeclaration: {
 *   Identifier: a,
 *   AssignmentExpression: {
 *     NumericLiteral: 2,
 *   }
 * }
**/
```

将AST 转换为可执行代码的过程称被称为代码生成。