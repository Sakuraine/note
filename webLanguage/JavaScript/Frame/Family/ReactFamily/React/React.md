# React

### 组件生命周期

#### 装配

这些方法会在组件实例被创建和插入DOM中时被调用：

- [`constructor()`](https://react.docschina.org/docs/react-component.html#constructor)
- [`static getDerivedStateFromProps()`](https://react.docschina.org/docs/react-component.html#static-getderivedstatefromprops)
- [`componentWillMount()` / `UNSAFE_componentWillMount()`](https://react.docschina.org/docs/react-component.html#unsafe_componentwillmount)
- [`render()`](https://react.docschina.org/docs/react-component.html#render)
- [`componentDidMount()`](https://react.docschina.org/docs/react-component.html#componentdidmount)

#### 更新

属性或状态的改变会触发一次更新。当一个组件在被重渲时，这些方法将会被调用：

- [`componentWillReceiveProps()` / `UNSAFE_componentWillReceiveProps()`](https://react.docschina.org/docs/react-component.html#unsafe_componentwillreceiveprops)
- [`static getDerivedStateFromProps()`](https://react.docschina.org/docs/react-component.html#static-getderivedstatefromprops)
- [`shouldComponentUpdate()`](https://react.docschina.org/docs/react-component.html#shouldcomponentupdate)
- [`componentWillUpdate()` / `UNSAFE_componentWillUpdate()`](https://react.docschina.org/docs/react-component.html#unsafe_componentwillupdate)
- [`render()`](https://react.docschina.org/docs/react-component.html#render)
- [`getSnapshotBeforeUpdate()`](https://react.docschina.org/docs/react-component.html#getsnapshotbeforeupdate)
- [`componentDidUpdate()`](https://react.docschina.org/docs/react-component.html#componentdidupdate)

#### 卸载

当一个组件被从DOM中移除时，该方法被调用：

- [`componentWillUnmount()`](https://react.docschina.org/docs/react-component.html#componentwillunmount)

#### 错误处理

在渲染过程中发生错误时会被调用：

- [`componentDidCatch()`](https://react.docschina.org/docs/react-component.html#componentdidcatch)

### 其他API

每一个组件还提供了其他的API：

- [`setState()`](https://react.docschina.org/docs/react-component.html#setstate)
- [`forceUpdate()`](https://react.docschina.org/docs/react-component.html#forceupdate)

### 类属性

- [`defaultProps`](https://react.docschina.org/docs/react-component.html#defaultprops)
- [`displayName`](https://react.docschina.org/docs/react-component.html#displayname)

### 实例属性

- [`props`](https://react.docschina.org/docs/react-component.html#props)
- [`state`](https://react.docschina.org/docs/react-component.html#state)


##### dangerouslySetInnerHTML

`直接转译html标签`

`dangerouslySetInnerHTML`React是`innerHTML`在浏览器DOM中使用的替代品。通常，从代码设置HTML是有风险的，因为很容易无意中将您的用户暴露给[跨站点脚本（XSS）](https://en.wikipedia.org/wiki/Cross-site_scripting)攻击。因此，您可以直接从React设置HTML，但是您必须键入`dangerouslySetInnerHTML`并使用`__html`键传递对象，以提醒自己这很危险。例如：

```jsx
function createMarkup() {
  return {__html: 'First &middot; Second'};
}

function MyComponent() {
  return <div dangerouslySetInnerHTML={createMarkup()} />;
}
```



### 组件通信

1. 父组件向子组件传递

   父组件通过Props传递到子组件

2. 子组件向父组件传递

   1. 通过回调函数

      子组件调用父组件方法将状态传进去

   2. 利用自定义事件机制

3. 跨级组件通信

   1. 层层传递props

   2. 使用context

      context是一个全局变量
      
      ```jsx
      
      class List extends Component {
        static childContextTypes = {
          color: PropTypes.string,
        };
      
        getChildContext() {
          return {
            color: 'red',
          };
        }
      
        render() {
        	const { list } = this.props;
          return (
            <div>
              <ListTitle title={title} />
              <ul>
                {list.map((entry, index) => (
                  <ListItem key={`list-${index}`} value={entry.text} />
                ))}
              </ul>
            </div>
          );
        }
      }
      
      class ListItem extends Component {
        static contextTypes = {
          color: PropTypes.string,
        };
      
        render() {
          const { value } = this.props;
      
          return (
            <li style={{background: this.context.color}}>
            	<span>{value}</span>
      			</li>
          ); 
      	}
      }
      
      ```
      
      

### Context

一个组件树顶层的 Props

> 用法

```js
// Context 可以让我们无须明确地传遍每一个组件，就能将值深入传递进组件树。
// 为当前的 theme 创建一个 context（“light”为默认值）。
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    // 使用一个 Provider 来将当前的 theme 传递给以下的组件树。
    // 无论多深，任何组件都能读取这个值。
    // 在这个例子中，我们将 “dark” 作为当前的值传递下去。
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

// 中间的组件再也不必指明往下传递 theme 了。
function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

class ThemedButton extends React.Component {
  // 指定 contextType 读取当前的 theme context。
  // React 会往上找到最近的 theme Provider，然后使用它的值。
  // 在这个例子中，当前的 theme 值为 “dark”。
  static contextType = ThemeContext;
  render() {
    return <Button theme={this.context} />;
  }
}
```

> 注意

- 使用 `context` 会使组件的复用性降低
- ...

#### API

##### `React.createContext`

```js
const MyContext = React.createContext(defaultValue);
```

创建一个 Context 对象。当 React 渲染一个订阅了这个 Context 对象的组件，这个组件会从组件树中离自身最近的那个匹配的 `Provider` 中读取到当前的 context 值。

只有当组件所处的树中没有匹配到 Provider 时，其 `defaultValue` 参数**才**会生效。这有助于在不使用 Provider 包装组件的情况下对组件进行测试。注意：将 `undefined` 传递给 Provider 时，消费组件的 `defaultValue` 不会生效。

##### `Context.Provider`

```js
<MyContext.Provider value={/* 某个值 */}>
```

每个 Context 对象都会返回一个 Provider React 组件，它允许消费组件订阅 context 的变化。

Provider 接收一个 `value` 属性，传递给消费组件。一个 Provider 可以和多个消费组件有对应关系。多个 Provider 也可以嵌套使用，里层的会覆盖外层的数据。

当 Provider 的 `value` 值发生变化时，它内部的所有消费组件都会重新渲染。Provider 及其内部 consumer 组件都不受制于 `shouldComponentUpdate` 函数，因此当 consumer 组件在其祖先组件退出更新的情况下也能更新。

通过新旧值检测来确定变化，使用了与 [`Object.is`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/is#Description) 相同的算法。

> 注意
>
> 当传递对象给 `value` 时，检测变化的方式会导致一些问题：详见[注意事项](https://react.docschina.org/docs/context.html#caveats)。

##### `Class.contextType`

```js
class MyClass extends React.Component {
  componentDidMount() {
    let value = this.context;
    /* 在组件挂载完成后，使用 MyContext 组件的值来执行一些有副作用的操作 */
  }
  componentDidUpdate() {
    let value = this.context;
    /* ... */
  }
  componentWillUnmount() {
    let value = this.context;
    /* ... */
  }
  render() {
    let value = this.context;
    /* 基于 MyContext 组件的值进行渲染 */
  }
}
MyClass.contextType = MyContext;
```

挂载在 class 上的 `contextType` 属性会被重赋值为一个由 [`React.createContext()`](https://react.docschina.org/docs/context.html#reactcreatecontext) 创建的 Context 对象。这能让你使用 `this.context` 来消费最近 Context 上的那个值。你可以在任何生命周期中访问到它，包括 render 函数中。

> 注意：
>
> 你只通过该 API 订阅单一 context。如果你想订阅多个，阅读[使用多个 Context](https://react.docschina.org/docs/context.html#consuming-multiple-contexts) 章节
>
> 如果你正在使用实验性的 [public class fields 语法](https://babeljs.io/docs/plugins/transform-class-properties/)，你可以使用 `static` 这个类属性来初始化你的 `contextType`。

```js
class MyClass extends React.Component {
  static contextType = MyContext;
  render() {
    let value = this.context;
    /* 基于这个值进行渲染工作 */
  }
}
```

##### `Context.Consumer`

```js
<MyContext.Consumer>
  {value => /* 基于 context 值进行渲染*/}
</MyContext.Consumer>
```

这里，React 组件也可以订阅到 context 变更。这能让你在[函数式组件](https://react.docschina.org/docs/components-and-props.html#function-and-class-components)中完成订阅 context。

这需要[函数作为子元素（function as a child）](https://react.docschina.org/docs/render-props.html#using-props-other-than-render)这种做法。这个函数接收当前的 context 值，返回一个 React 节点。传递给函数的 `value` 值等同于往上组件树离这个 context 最近的 Provider 提供的 `value` 值。如果没有对应的 Provider，`value` 参数等同于传递给 `createContext()` 的 `defaultValue`。

> 注意
>
> 想要了解更多关于“函数作为子元素（function as a child）”模式，详见 [render props](https://react.docschina.org/docs/render-props.html)。



### 组件间抽象

#### mixin

> 广义的 mixin 方法，就是用赋值的方式将 mixin 对象里的方法都挂载到原对象上，来实现对对象的混入

##### mixin 的问题

- 破坏原有组件的封装
  - 可能带来新的 `state` 和 `props`，会带来不可见的状态
  - mixin也可能依赖其他mixin，mixin 是平面结构，无法维护依赖链
- 命名冲突
- 增加复杂性

#### ES6 Classes 与 decorator

> decorator实现

```js
import { getOwnPropertyDescriptors } from './private/utils';
const { defineProperty } = Object;

function handleClass(target, mixins) {
  if (!mixins.length) {
    throw new SyntaxError(`@mixin() class ${target.name} requires at least one mixin as an argument`);
  }

	for (let i = 0, l = mixins.length; i < l; i++) {
    // 获取 mixins 的 attributes 对象
    const descs = getOwnPropertyDescriptors(mixins[i]);
		// 批量定义 mixins 的 attributes 对象
    for (const key in descs) {
			if (!(key in target.prototype)) {
        defineProperty(target.prototype, key, descs[key]);
      }
    }
  }
}

export default function mixin(...mixins) {
  if (typeof mixins[0] === 'function') {
    return handleClass(mixins[0], []);
  } else {
    return target => {
      return handleClass(target, mixins); };
  }
}
```

它将每一个 mixin 对象的方法都叠加到 target 对象的原型上以达到 mixin 的目的

```js
import React, { Component } from 'React';
import { mixin } from 'core-decorators';

const PureRender = {
  shouldComponentUpdate() {}
};

const Theme = {
  setTheme() {}
};

@mixin(PureRender, Theme)
class MyComponent extends Component {
  render() {}
}
```



#### 高阶组件（higher-order-component）

> 一种接受组件返回一个增强组件的方法

##### 功能

1. 代码复用，代码模块化
2. 渲染劫持, 操作state
3. Props 增删改

##### 实现方式

1. 属性代理（Props Proxy）
   1. 高阶组件通过被包裹的 React 组件来操作 props。
2. 反向继承（Inheritance Inversion）
   1. 高阶组件继承于被包裹的 React 组件

##### 生命周期

didmount→HOC didmount→(HOCs didmount)→(HOCs will unmount)→HOC will unmount→unmount

##### 控制props

​	我们可以读取、增加、编辑或是移除从 WrappedComponent 传进来的 props，但需要小心删 

​	除与编辑重要的 props。我们应该尽可能对高阶组件的 props 作新的命名以防止混淆。 例如，我们需要增加一个新的 prop: 

```jsx
import React, { Component } from 'React'; 

const MyContainer = (WrappedComponent) => class extends Component { 

render() {
  const newProps = { 
    text: newText,
  }; 

  return <WrappedComponent {...this.props} {...newProps} />; } 
}

```

 	当调用高阶组件时，可以用 `text` 这个新的 `props` 了。对于原组件来说，只要套用这个高阶组 件，我们的新组件中就会多一个 `text` 的 `prop`。 

##### 通过 `refs` 使用引用

```jsx
import React, { Component } from 'react';

const MyContainer = (WrappedComponent) => class extends Component {
	proc(wrappedComponentInstance) {
    wrappedComponentInstance.method();
  }

  render() {
    const props = Object.assign({}, this.props, {
      ref: this.proc.bind(this),
    });
    return <WrappedComponent {...props} />;
  }
}
```

​	当 WrappedComponent 被渲染时，refs 回调函数就会被执行，这样就会拿到一份WrappedComponent 实例的引用。这就可以方便地用于读取或增加实例的 props，并调用实例的方法。 

##### 抽象 state

​	通过 WrappedComponent 提供的 `props` 和回调函数抽象 `state`，高阶组件可以将原组件抽象为展示型组件，分离内部状态

> Example

​	抽象一个 input 组件：

```jsx
import React, { Component } from 'React';

const MyContainer = (WrappedComponent) => class extends Component {
  constructor(props) {
    super(props);
    this.state = {
      name: '',
    };

		this.onNameChange = this.onNameChange.bind(this);
  }

	onNameChange(event) {
    this.setState({
			name: event.target.value,
    })
	}

	render() {
    const newProps = {
      name: {
        value: this.state.name, onChange: this.onNameChange,
      },
    }
    return <WrappedComponent {...this.props} {...newProps} />;
  }
}
```



##### 问题

1. 静态方法丢失

   1. 解决方法：使用[hoist-non-react-statics](https://github.com/mridgway/hoist-non-react-statics)来帮你自动处理，它会自动拷贝所有非React的静态方法；（react-router 里withRouter就使用了这个包）

2. Refs属性不能传递

   1. 解决方法：新组建传递一个 `ref` 回调函数属性给原始组件

      ```jsx
      <Enhancer  getRef={ref => this.wrappedC = ref} />
      ```

3. 不要再 `render()` 里使用高阶函数：

   ```js
   render() {
     // 每一次render函数调用都会创建一个新的EnhancedComponent实例 
     // EnhancedComponent1 !== EnhancedComponent2
     const EnhancedComponent = enhance(MyComponent);
     // 每一次都会使子对象树完全被卸载或移除
     return <EnhancedComponent />;
   }
   ```

   性能问题、重新加载一个组件会引起原有组件的所有状态和子组件丢失

   1. 解决方法：

      在组件定义外使用高阶组件



