select label value用法

```jsx
<FormItem
  {...formItemLayout1}
  label="分组:"
  >
  {getFieldDecorator('pati_group_id', {
    initialValue: data.pati_group_id ? { label: data.pati_group_name, value: data.pati_group_id } : undefined,
  })(
    <Select
      labelInValue
      showSearch
      allowClear
      filterOption={e => true}
      placeholder="请选择"
      >
      {
        groupData.map((item, i) => {
          return <Option key={item.label_id}>{item.label_name}</Option>;
        })
      }
    </Select>
  )}
</FormItem>
```

TreeSelect树选择器

```jsx
import { TreeNode } = antd;
const TreeNode = TreeSelect.TreeNode;

const generateTreeNodes = (tree, bool = true) => {
  return tree.map((item) => {
    if (item.children) {
      return (
        <TreeNode
          value={item.id}
          name={item.name}
          title={item.name}
          key={item.id}
          disabled={bool && item.id === '0'}
        >
          {generateTreeNodes(item.children)}
        </TreeNode>
      );
    }
    return <TreeNode value={item.id} name={item.name} title={item.name} key={item.id} />;
  });
};
```



tabel 功能渲染

```jsx
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

form 表单使用时需要注意点的点：

- 数据输入不进去

  查看数据是否双向绑定了，是否在前面定义了字段名

- 校验时只在第一个输入框下有校验提示

  每个输入的框都应该使用一个FormItem包裹住，

```jsx
<FormItem
  {...formItemLayout1}
  label="分组:"
  >
  {getFieldDecorator('pati_group_id', {
    initialValue: data.pati_group_id ? { label: data.pati_group_name, key: data.pati_group_id } : undefined,
  })(
    <Select
      labelInValue
      showSearch
      allowClear
      filterOption={e => true}
      // onSearch={value => this.handleSelect(value, 'group')}
      placeholder="请选择"
      >
      {
        groupData.map((item, i) => {
          return <Option key={item.label_id}>{item.label_name}</Option>;
        })
      }
    </Select>
  )}
</FormItem>
```

校验

```jsx
const reg1 = /^([0-9]+(\.\d+)?|0\.\d+)$/; // 正数
const match = (value) => {
  return reg.test(value);
};

<FormItem>
  {getFieldDecorator(`item_no_${key}`, {
    initialValue: item.item_no || '',
    rules: [{
      required: true,
      message: '必填',
    }, {
      validator: (rules, val, callback) => {
      if (val && !match(val)) {
      callback('请输入数字');
      }
    	callback();
    	}
    	}],
    })(
    <Input placeholder="问题编号" />
  )}
</FormItem>
```

```js
export default connect((state) => {
  return {
    data: state.RefractiveCenterList,
    cache: state.cache,
  };
})(Form.create()(RefractiveCenter));
```



ref   wrappedComponentRef