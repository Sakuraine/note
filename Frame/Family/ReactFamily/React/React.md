# React

### dangerouslySetInnerHTML

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

