# 前言

## React 的开始

- 2004年 Gmail 的推出，大家发现单页应用的互动也可以如此流畅。
- 2010年，前端单页应用框架接踵而至，Backbone、Knockout、Angular
- 2013年，Facebook 发布 React：单向绑定、声明式UI，大大简化了大型应用的构建

## React流行的原因：

​	平衡了函数式编程的约束与工程师的实用主义

### React从函数式编程社区借鉴了许多约定：

	- 把 dom 当成纯函数
	- 不可变性
	- 单向数据流

> 加强了程序的可预测性

# React

## React 简介

### 专注视图层

​	React 并不是完整的 MVC/MVVM 框架，它专注于提供清晰、简洁的View（视图层）解决方案。

​	又于模板引擎不同，React 是一个包括 View 和 Controller 的库。

​	以 **Minimal API Interface** 为目标，只提供组件化相关的非常少量的 API。

### Virtual DOM

> 真实页面对应的JavaScript对象表达的DOM树

​	节省DOM开销

​	方便和其他平台集成（Web、Android、IOS）

### 函数式编程

> 函数式编程对应的是声明式编程，本质是 lambda演算

## JSX 语法

### JSX 的由来

​	JSX是一种JavaScript的语法扩展，JSX就是用来声明React当中的元素，React使用JSX来描述用户界面

- DOM元素

- 组件元素

​	JSX 将 HTML 语法 直接加入到 JavaScript 代码中，再通过翻译器转换到纯 JavaScript 后由浏览器执行

- 没有副作用

- 代码直观且易于维护

### JSX 基本语法

​	JSX的官方定义是类 XML 语法的 ECMAScript 扩展

1. XML 基本语法

   ​	使用类 XML 语法的好处是标签可以任意嵌套

   1. 定义标签时，只允许被一个标签包裹
   2. 标签一定要闭合

2. 元素类型

   1. HTML元素 首字母小写
   2. 组件元素 首字母大写

   - 注释

     ```JSX
     // HTML 注释
     <!-- content -->
     
     // JSX 注释
     {/* 节点注释 */}
     /* 多行
     	 注释 */
     ```

   - DOCTYPE

     ​	DOCTYPE 一般在使用 React 作为服务器渲染时用到。在 HTML 中，DOCTYPE 是没有闭合的，也就是说我们无法渲染它。

     ​	常见的做法是构造一个保存 HTML 的变量，将 DOCTYPE 与整个 HTML 标签渲染后的结果串联起来。

   3. 元素属性

      1. DOM 元素的属性是标准规范属性，但也有两个例外：

         1. class 属性改为 className
         2. for 属性改为 htmlFor

      2. 组件元素的属性是完全自定义的属性，也可以理解为实现组件所需要的参数

         - Boolean 属性

           省略 Boolean 属性值会导致 JSX 认为 bool 值设为了 true

           ```jsx
           <Component
           	disabled // 没有值则认为设为了 true
           	required={false} // 传 false 必须使用属性表达式
           />
           ```

         - 展开属性

           如果事先知道组件需要的全部属性，JSX 可以这样写

           ```jsx
           const data = { name: 'foo', value: 'bar' };
           const component = <Component {...data} />
           ```

         - 自定义 HTML 属性

           如果在 JSX 中往 DOM 元素中传入自定义属性，React 是不会渲染的：

           ```JSX
           <div d="xxx">content</div>
           ```

           如果需要使用 HTML 自定义属性，要使用 data- 前缀，这与 HTML 标准也是一致的：

           ```JSX
           <div data-attr="xxx">content</div>
           ```

           以 aria- 开头的网络无障碍属性同样可以正常使用：

           ```JSX
           <div aria-hidden />
           ```

   4. JavaScript 属性表达式

      属性值要使用表达式，只要用{}替换""即可

   5. HTML 转义

      ​	React 会将所有要显示到 DOM 的字符串转义，防止 XSS。如果 JSX 中含有转义后的实体字符，比如 `&copy;`，DOM 中不会正确显示，React 会把 `&copy; ` 中的特殊字符转义了。

      解决办法：

      - 直接使用 UTF-8 字符 &copy;
      - 使用对应字符的 Unicode 编码查询编码
      - 使用数组组装 `<div>{['cc', <span>&copy;</span>, '2015']}</div>`
      - 直接插入原始的 HTML
      - 使用 React 提供的 dangerouslySetInnerHTML 属性（避免 React 转义字符）`<div dangerouslySetInnerHTML={{  __html: 'cc &copy; 2015' }} />`

