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



### 高阶组件

table功能项渲染

```js
class BinocularDiy extends React.Component {
  // 当组件的state需要this.props传进来的数据传进来
  constructor(props) {
    super(props);
    this.state = {};
  }
}
```
