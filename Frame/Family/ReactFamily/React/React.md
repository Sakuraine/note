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

table功能项渲染

```js
const columns = [{
  title: '序号',
  dataIndex: 'index',
  key: 'index',
  width: 100,
}, {
  title: '操作',
  dataIndex: 'action',
  key: 'action',
  width: 100,
}]
class List extends React.Component {
	componentWillMount() {
    const { dispatch } = this.props;
    util.tableAddRender(columns, 'index', (text, record, i) => {
      const key = `${i + 1}`;
      return (
        <div>{key}</div>
      );
    });
    util.tableAddRender(columns, 'action', (text, record, i) => {
      return (
        <div>
          <a onClick={e => this.handleDetail(record.package_id)}>详情</a>;
          <a onClick={e => this.handleDelete(record.package_id)}>删除</a>;
        </div>
      );
    });
  }
  
  /**
   * 表格渲染--状态
   * @return {[type]}        [description]
   */
  _renderPatiState = (text, record) => {
    let showText;
    if (record.package_enable === 0) {
      showText = '停用';
    } else if (record.package_enable === 1) {
      showText = '有效';
    }
    return showText;
  }
}
```

