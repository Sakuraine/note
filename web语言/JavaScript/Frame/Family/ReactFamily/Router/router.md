# 路由

## 基础

### 路由匹配原理

#### 嵌套关系

React Router 使用路由嵌套的概念来让你定义 view 的嵌套集合，当一个给定的 URL 被调用时，整个集合中（命中的部分）都会被渲染。嵌套路由被描述成一种树形结构。React Router 会深度优先遍历整个[路由配置](http://react-guide.github.io/react-router-cn/docs/guides/basics/docs/Glossary.md#routeconfig)来寻找一个与给定的 URL 相匹配的路由。

#### 路径语法

##### 特殊情况

1. `:paramName`

   当做一个参数

2. `()`

   在它内部的内容被认为是可选的

3. `*`

   匹配任意字符（非贪婪的）直到命中下一个字符或者整个 URL 的末尾，并创建一个 `splat` 参数

#### 优先级

路由算法会根据定义的顺序自顶向下匹配路由

### Histories

- browserHistory
- hashHistory
- createMemoryHistory

