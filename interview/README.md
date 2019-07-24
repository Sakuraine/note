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

只对比同级

# `HTTPS` 安全性



# `HTTP` 状态码



# `rem`



# `getComputedStyle`



# 面向对象和面向过程

面向对象只关注结果，面向过程关注如何做

## 面向对象的三大特性

1. 封装
   1. 隐藏对象的属性和实现细节，仅对外提供公共访问方式，将变化隔离，便于使用，提高复用性和安全性。
2. 继承
   1. 提高代码复用性；继承是多态的前提。
3. 多态
   1. 父类或接口定义的引用变量可以指向子类或具体实现类的实例对象。提高了程序的拓展性。

## 五大基本原则（单开里依接）

1. 单一职责原则
   1. 类的功能要单一
2. 开放封闭原则
   1. 一个模块对于拓展是开放的，对于修改是封闭的
3. 里式替换原则
   1. 子类可以替换父类出现在父类能够出现的任何地方
4. 依赖倒置原则
   1. 高层次的模块不应该依赖于低层次的模块，他们都应该依赖于抽象。抽象不应该依赖于具体实现，具体实现应该依赖于抽象。
5. 接口分离原则
   1. 设计时采用多个与特定客户类有关的接口比采用一个通用的接口要好。



# 前端性能优化

- 减少http重复请求，合理设置 HTTP缓存
- 资源合并压缩（webpack打包工具）
- CSS Sprites
- 将外部脚本置底（将脚本内容在页面信息内容加载后再加载）
-  异步执行 inline脚本
- css选择器
- 试用CDN



- 减少不必要的 HTTP跳转
- 减少dom操作，（重绘和回流）
- 减少作用域链查找和闭包

## 浏览器的缓存机制

- Cookie

  - IE6或更低版本最多20个cookie
  - IE7和之后的版本最后可以有50个cookie。
  - Firefox最多50个cookie
  - chrome和Safari没有做硬性限制

  > 优点

  > 缺点

  - 数量和长度有限制，20条，4kb，超过的会被裁掉
  - 安全性问题。如果cookie被人拦截了，那人就可以取得所有的session信息。即使加密也与事无补，因为拦截者并不需要知道cookie的意义，他只要原样转发cookie就可以达到目的了。
  - 自己域名的Cookie 父级域名以及其他域名是不可访问

- 浏览器本地缓存（HTML5）

  -  localStorage 
    - 没有时间限制的数据存储
    - 不会过期
    - 数据可跨越多个窗口，无视当前会话，被共同访问、使用
  - sessionStorage
    - 浏览器关闭则丢失
    - 每个窗口的数据都是独立的
    - 在同一窗口的同一网站的任何界面都可以访问

  > localStorage和sessionStorage有共同的api

  ```js
  localStorage.length //获得storage中的个数
  localStorage .key(n) //获得storage中第n个键值对的键
  localStorage.key = //value
  localStorage.setItem(key, value) //添加
  localStorage.getItem(key) //获取
  localStorage.removeItem(key) //移除
  localStorage.clear() //清除
  ```

  - globalStorage
    - 浏览器关闭后仍有
    - 域中任何一个页面存储的信息都能被所有的页面共享
    - 目前只有FF支持
    - 只支持当前域下的globalStorage存储
  - Web Sql Database（目前只谷歌浏览器支持）
    - openDatabase：这个方法使用现有数据库或创建新数据库创建数据库对象。
    - ransaction：这个方法允许我们根据情况控制事务提交或回滚。
    - executeSql：这个方法用于执行真实的SQL查询。



### React

- 使用时候使用状态管理器？
- render函数中return如果没有使用()会有什么问题？
- componentWillUpdate可以直接修改state的值吗？
- 说说你对React的渲染原理的理解
- 什么渲染劫持？
- React Intl是什么原理？
- 你有使用过React Intl吗？
- 怎么实例React组件的国际化呢？
- 说说Context有哪些属性？
- 怎么使用Context开发组件？
- 为什么React并不推荐我们优先考虑使用Context？
- 除了实例的属性可以获取Context外哪些地方还能直接获取Context呢？
- childContextTypes是什么？它有什么用？
- contextType是什么？它有什么用？
- Consumer向上找不到Provider的时候怎么办？
- 有使用过Consumer吗？
- 在React怎么使用Context？
- React15和16别支持IE几以上？
- 说说你对windowing的了解
- 举例说明React的插槽有哪些运用场景？
- 你有用过React的插槽(Portals)吗？怎么用？
- React的严格模式有什么用处？
- React如何进行代码拆分？拆分的原则是什么？
- React组件的构造函数有什么作用？
- React组件的构造函数是必须的吗？
- React中在哪捕获错误？
- React怎样引入svg的文件？
- 说说你对Relay的理解
- 在React中你有经常使用常量吗？
- 为什么说React中的props是只读的？
- 你有使用过formik库吗？说说它的优缺点
- 你有用过哪些React的表单库吗？说说它们的优缺点
- 如果组件的属性没有传值，那么它的默认值是什么？
- 可以使用TypeScript写React应用吗？怎么操作？
- `super()`和`super(props)`有什么区别？
- 你有使用过loadable组件吗？它帮我们解决了什么问题？
- 你有使用过suspense组件吗？它帮我们解决了什么问题？
- 怎样动态导入组件？
- 如何给非控组件设置默认的值？
- 怎么在React中引入其它的UI库，例如Bootstrap
- 怎样将事件传递给子组件？
- 怎样使用Hooks获取服务端数据？
- 使用Hooks要遵守哪些原则？
- render方法的原理你有了解吗？它返回的数据类型是什么？
- useEffect和useLayoutEffect有什么区别？
- 在React项目中你用过哪些动画的包？
- React必须使用JSX吗？
- 自定义组件时render是可选的吗？为什么？
- 需要把keys设置为全局唯一吗？
- 怎么定时更新一个组件？
- React根据不同的环境打包不同的域名？
- 使用webpack打包React项目，怎么减小生成的js大小？
- 在React中怎么使用async/await？
- 你阅读了几遍React的源码？都有哪些收获？你是怎么阅读的？
- 什么是React.forwardRef？它有什么作用？
- 写个例子说明什么是JSX的内联条件渲染
- 在React中怎么将参数传递给事件？
- React的事件和普通的HTML事件有什么不同？
- 在React中怎么阻止事件的默认行为？
- 你最喜欢React的哪一个特性（说一个就好）？
- 在React中什么时候使用箭头函数更方便呢？
- 你最不喜欢React的哪一个特性（说一个就好）？
- 说说你对React的reconciliation（一致化算法）的理解
- 使用PropTypes和Flow有什么区别？
- 怎样有条件地渲染组件？
- 在JSX中如何写注释？
- constructor和getInitialState有不同？
- 写例子说明React如何在JSX中实现for循环
- 为什么建议Fragment包裹元素？它的简写是什么？
- 你有用过React.Fragment吗？说说它有什么用途？
- 在React中你有遇到过安全问题吗？怎么解决？
- React中如何监听state的变化？
- React什么是有状态组件？
- React v15中怎么处理错误边界？
- React Fiber它的目的是解决什么问题？
- React为什么不要直接修改state？如果想修改怎么做？
- create-react-app有什么好处？
- 装饰器(Decorator)在React中有什么应用？
- 使用高阶组件(HOC)实现一个loading组件
- 如何用React实现滚动动画？
- 说出几点你认为的React最佳实践
- 你是如何划分React组件的？
- 举例说明如何在React创建一个事件
- 如何更新组件的状态？
- 怎样将多个组件嵌入到一个组件中？
- React的render中可以写{if else}这样的判断吗？
- React为什么要搞一个Hooks？
- React Hooks帮我们解决了哪些问题？
- 使用React的memo和forwardRef包装的组件为什么提示children类型不对？
- 有在项目中使用过Antd吗？说说它的好处
- 在React中如果去除生产环境上的sourcemap？
- 在React中怎么引用sass或less？
- 组件卸载前，加在DOM元素的监听事件和定时器要不要手动清除？为什么？
- 为什么标签里的for要写成htmlFor呢？
- 状态管理器解决了什么问题？什么时候用状态管理器？
- 状态管理器它精髓是什么？
- 函数式组件有没有生命周期？为什么？
- 在React中怎么引用第三方插件？比如说jQuery等
- React的触摸事件有哪几种？
- 路由切换时同一组件无法重新渲染的有什么方法可以解决？
- React16新特性有哪些？
- 你有用过哪些React的UI库？它们的优缺点分别是什么？
- `<div onClick={handlerClick}>单击</div>`和`<div onClick={handlerClick(1)}>单击</div>`有什么区别？
- 在React中如何引入图片？哪种方式更好？
- 在React中怎么使用字体图标？
- React的应用如何打包发布？它的步骤是什么？
- ES6的语法'...'在React中有哪些应用？
- 如何封装一个React的全局公共组件？
- 在React中组件的props改变时更新组件的有哪些方法？
- immutable的原理是什么？
- 你对immutable有了解吗？它有什么作用？
- 如何提高组件的渲染效率呢？
- 在React中如何避免不必要的render？
- render在什么时候会被触发？
- 写出React动态改变class切换组件样式
- React中怎么操作虚拟DOM的Class属性？
- 为什么属性使用className而不是class呢？
- 请说下react组件更新的机制是什么？
- 怎么在JSX里属性可以被覆盖吗？覆盖的原则是什么？
- 怎么在JSX里使用自定义属性？
- 怎么防止HTML被转义？
- 经常用React，你知道React的核心思想是什么吗？
- 在React中我们怎么做静态类型检测？都有哪些方法可以做到？
- 在React中组件的state和setState有什么区别？
- React怎样跳过重新渲染？
- React怎么判断什么时候重新渲染组件呢？
- 什么是React的实例？函数式组件有没有实例？
- 在React中如何判断点击元素属于哪一个组件？
- 在React中组件和元素有什么区别？
- 在React中声明组件时组件名的第一个字母必须是大写吗？为什么？
- 举例说明什么是高阶组件(HOC)的反向继承？
- 有用过React Devtools吗？说说它的优缺点分别是什么？
- 举例说明什么是高阶组件(HOC)的属性代理？
- React的isMounted有什么作用？
- React组件命名推荐的方式是哪个？为什么不推荐使用displayName？
- React的displayName有什么作用？
- 说说你对React的组件命名规范的理解
- 说说你对React的项目结构的理解
- React16废弃了哪些生命周期？为什么？
- 怎样在React中开启生产模式？
- React中getInitialState方法的作用是什么？
- React中你知道creatClass的原理吗？
- React中验证props的目的是什么？
- React中你有使用过getDefaultProps吗？它有什么作用？
- React中你有使用过propType吗？它有什么作用？
- React中怎么检验props？
- React.createClass和extends Component的区别有哪些？
- 高阶组件(HOC)有哪些优点和缺点？
- 给组件设置很多属性时不想一个个去设置有什么办法可以解决这问题呢？
- React16跟之前的版本生命周期有哪些变化？
- 怎样实现React组件的记忆？原理是什么？
- 创建React动画有哪些方式？
- 为什么建议不要过渡使用Refs？
- 在React使用高阶组件(HOC)有遇到过哪些问题？如何解决？
- 在使用React过程中什么时候用高阶组件(HOC)？
- 说说React diff的原理是什么？
- React怎么提高列表渲染的性能？
- 使用ES6的class定义的组件不支持mixins了，那用什么可以替代呢？
- 为何说虚拟DOM会提高性能？
- React的性能优化在哪个生命周期？它优化的原理是什么？
- 你知道的React性能优化有哪些方法？
- 举例说明在React中怎么使用样式？
- React有哪几种方法来处理表单输入？
- 什么是浅层渲染？
- 你有做过React的单元测试吗？如果有用的是些工具？怎么做的？
- 在React中什么是合成事件？有什么用？
- 使用React写一个todo应用，说说你的思路
- React16的reconciliation和commit分别是什么？
- React的函数式组件有没有生命周期？
- useState和this.state的区别是什么？
- 请说说什么是useImperativeHandle？
- 请说说什么是useReducer？
- 请说说什么是useRef？
- 请说说什么是useEffect？
- 举例说明useState
- 请说说什么是useState？为什么要使用useState？
- 请描述下你对React的新特性Hooks的理解？它有哪些应用场景？
- 说说你对Error Boundaries的理解
- 说说你对Fiber架构的理解
- 说说你是怎么理解React的业务组件和技术组件的？
- 为什么建议setState的第一个参数是callback而不是一个对象呢？
- 展示组件和容器组件有什么区别？
- Mern和Yeoman脚手架有什么区别？
- 你有在项目中使用过Yeoman脚手架吗？
- 你有在项目中使用过Mern脚手架吗？
- shouldComponentUpdate方法是做什么的？
- 怎样在React中使用innerHTML？
- 你有写过React的中间件插件吗？
- React的中间件机制是怎么样的？这种机制有什么作用？
- React中你用过哪些第三方的中间件？
- 不用脚手架，你会手动搭建React项目吗？
- 请说说React中Portal是什么？
- React中修改prop引发的生命周期有哪几个？
- React多个setState调用的原理是什么？
- React中调用setState会更新的生命周期有哪几个？
- React中setState的第二个参数作用是什么呢？
- React中的setState是同步还是异步的呢？为什么state并不一定会同步更新？
- React中的setState批量更新的过程是什么？
- React中的setState执行机制是什么呢？
- 在React中遍历的方法有哪些？它们有什么区别呢？
- 请说说你对React的render方法的理解
- props.children.map和js的map有什么区别？为什么优先选择React的？
- 有用过React的严格模式吗？
- React中的setState和replaceState的区别是什么？
- React中的setState缺点是什么呢？
- 有用过React的Fragment吗？它的运用场景是什么？
- React组件间共享数据方法有哪些？
- React的状态提升是什么？使用场景有哪些？
- 简单描述下你有做过哪些React项目？
- 在构造函数中调用super(props)的目的是什么？
- 你是如何学习React的？
- 从旧版本的React升级到新版本的React有做过吗？有遇到过什么坑？
- 你用过React版本有哪些？
- 有用过React的服务端渲染吗？怎么做的？
- React的mixins有什么作用？适用于什么场景？
- React怎么拿到组件对应的DOM元素？
- 请描述下事件在React中的处理方式是什么？
- JSX和HTML有什么区别？
- React的书写规范有哪些？
- create-react-app创建新运用怎么解决卡的问题？
- 使用React的方式有哪几种？
- 说说你对reader的context的理解
- 同时引用这三个库React.js、React-dom.js和babel.js它们都有什么作用？
- 你知道Virtual DOM的工作原理吗？
- 你阅读过React的源码吗？简要说下它的执行流程
- React中怎样阻止组件渲染？
- React非兄弟组件如何通信？
- React兄弟组件如何通信？
- React非父子组件如何通信？
- React父子组件如何通信？
- React组件间的通信有哪些？
- 类组件和函数式组件有什么区别？
- React自定义组件你写过吗？说说看都写过哪些？
- React组件的state和props两者有什么区别？
- React有几种构建组件的方式？可以写出来吗？
- React中遍历时为什么不用索引作为唯一的key值？
- React中的key有什么作用？
- React中除了在构造函数中绑定this,还有别的方式吗？
- 在React中页面重新加载时怎样保留数据？
- 请描述下React的事件机制
- 怎样在React中创建一个事件？
- 在React中无状态组件有什么运用场景？
- 描述下在React中无状态组件和有状态组件的区别是什么？
- 写一个React的高阶组件(HOC)并说明你对它的理解
- React中可以在render访问refs吗？为什么？
- React中refs的作用是什么？有哪些应用场景？
- 请描述你对纯函数的理解？
- 受控组件和非受控组件有什么区别？
- React中什么是非控组件？
- React中什么是受控组件？
- React中发起网络请求应该在哪个生命周期中进行？为什么？
- 说说React的生命周期有哪些？
- 说说你对“在React中，一切都是组件”的理解
- 写React你是用es6还是es5的语法？有什么区别？
- 浏览器为什么无法直接JSX？怎么解决呢？
- 在使用React过程中你都踩过哪些坑？你是怎么填坑的？
- 说说你喜欢React的原因是什么？它有什么优缺点？
- 如何解决引用类型在pureComponent下修改值的时候，页面不渲染的问题？
- createElement与cloneElement两者有什么区别？
- 解释下React中Element 和Component两者的区别是什么？
- 解释下React中component和pureComponent两者的区别是什么？
- React的虚拟DOM和vue的虚拟DOM有什么区别？
- 你觉得React上手快不快？它有哪些限制？
- 说说你对声明式编程的理解？
- React与angular、vue有什么区别？
- React是哪个公司开发的？
- React是什么？它的主要特点是什么？
- 简要描述下你知道的React工作原理是什么？
- 在React中怎样改变组件状态，以及状态改变的过程是什么？
- 在React中你是怎么进行状态管理的？
- React声明组件有哪几种方法，各有什么不同？

### ReactNative

- 如何在React Native中设置环境变量？
- 请描述下Code Push的原理是什么？
- React Native怎样查看日记？
- React Native怎样测试？
- React Native怎样调试？
- React Native和React有什么区别？
- 有做过React Native项目吗？

### React-Router

- React-Router怎么获取历史对象？
- React-Router怎么获取URL的参数？
- 在history模式中push和replace有什么区别？
- React-Router怎么设置重定向？
- React-Router 4中`<Router>`组件有几种类型？
- React-Router 3和React-Router 4有什么变化？添加了什么好的特性？
- React-Router的实现原理是什么？
- React-Router 4的switch有什么用？
- React-Router的路由有几种模式？
- React-Router 4怎样在路由变化时重新渲染同一个组件？
- React-Router的`<Link>`标签和`<a>`标签有什么区别？
- React的路由和普通路由有什么区别？
- 请你说说React的路由的优缺点？
- 请你说说React的路由是什么？

### Redux/Mobox

- 你有了解Rxjs是什么吗？它是做什么的？
- 在Redux中怎么发起网络请求？
- Redux怎样重置状态？
- Redux怎样设置初始状态？
- Context api可以取代Redux吗？为什么？
- 推荐在reducer中触发Action吗？为什么？
- Redux怎么添加新的中间件？
- redux-saga和redux-thunk有什么本质的区别？
- 在React中你是怎么对异步方案进行选型的？
- 你知道redux-saga的原理吗？
- 你有使用过redux-saga中间件吗？它是干什么的？
- Redux中异步action和同步action最大的区别是什么？
- Redux和vuex有什么区别？
- Redux的中间件是什么？你有用过哪些Redux的中间件？
- 说说Redux的实现流程
- Mobx的设计思想是什么？
- Redux由哪些组件构成？
- Mobx和Redux有什么区别？
- 在React项目中你是如何选择Redux和Mobx的？说说你的理解
- 你有在React中使用过Mobx吗？它的运用场景有哪些？
- Redux的thunk作用是什么？
- Redux的数据存储和本地储存有什么区别？
- 在Redux中，什么是reducer？它有什么作用？
- 举例说明怎么在Redux中定义action？
- 在Redux中，什么是action？
- 在Redux中，什么是store？
- 为什么Redux能做到局部渲染呢？
- 说说Redux的优缺点分别是什么？
- Redux和Flux的区别是什么？
- Redux它的三个原则是什么？
- 什么是单一数据源？
- 什么是Redux？说说你对Redux的理解？有哪些运用场景？

### Flux

- 请说说点击按钮触发到状态更改，数据的流向？
- 请描述下Flux的思想
- 什么是Flux？说说你对Flux的理解？有哪些运用场景？



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