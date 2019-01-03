# [Ant Design](https://ant.design/index-cn)

## component

### 通用

### 布局

#### Grid 栅格

##### 工作原理

- 通过`row`在水平方向建立一组`column`（简写col）

- 你的内容应当放置于`col`内，并且，只有`col`可以作为`row`的直接元素

- 栅格系统中的列是指1到24的值来表示其跨越的范围。例如，三个等宽的列可以使用`.col-8`来创建

- 如果一个`row`中的`col`总和超过 24，那么多余的`col`会作为一个整体另起一行排列

##### Flex 布局

##### API

###### ROW

| method  | description               | type           | default |
| ------- | ------------------------- | -------------- | ------- |
| align   | flex 布局下的垂直对齐方式 | string         | top     |
| gutter  | 栅格间隔                  | number\|Object | 0       |
| justify | flex 布局下的水平排列方式 | string         | start   |
| type    | 布局模式                  | string         |         |

###### Col

| method | description                                           | type           | default |
| ------ | ----------------------------------------------------- | -------------- | ------- |
| offset | 栅格左侧的间隔格数，间隔内不可以有栅格                | number         | 0       |
| order  | 栅格顺序，flex布局模式下有效                          | number         | 0       |
| pull   | 栅格向左移动格数                                      | number         | 0       |
| push   | 栅格向右移动格数                                      | number         | 0       |
| span   | 栅格占位格数，为 0 时相当于display: none              | number         |         |
| xs     | <576px响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object |         |
| sm     | ≥576px响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object |         |
| md     | ≥768px响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object |         |
| lg     | ≥992px响应式栅格，可为栅格数或一个包含其他属性的对象  | number\|object |         |
| xl     | ≥1200px响应式栅格，可为栅格数或一个包含其他属性的对象 | number\|object |         |
| xxl    | ≥1600px响应式栅格，可为栅格数或一个包含其他属性的对象 | number\|object |         |

#### Layout布局

协助进行页面级整体布局

### 导航

### 数据录入

#### From

##### From

| method            | description           | type                        |
| ----------------- | ---------------------- | :-------------------------- |
| getFieldDecorator | 用于和表单进行双向绑定 |                             |
| getFieldValue     | 获取一个输入控件的值   | Function(fieldName: string) |
|  validateFields   | 校验并获取一组输入域的值与 Error，若 fieldNames 参数为空，则校验全部组件 |  |
| setFieldsValue |  | |

##### From.Item

| method | description | type |
| ------ | ----------- | ---- |
|        |             |      |

### 数据展示

#### Tabel 表格

##### Table

| method   | Description        | type                        | default  |
| -------- | ------------------ | --------------------------- | -------- |
| position | 指定分页显示的位置 | 'top' \| 'bootom' \| 'both' | 'bootom' |

#### Tree 树形控件

##### Tree props

| method           | description        | type    | default |
| ---------------- | ------------------ | ------- | ------- |
| defaultExpandAll | 是否展开所有树节点 | boolean | false   |

##### TreeNode props

| method | description | type   | default |
| ------ | ----------- | ------ | ------- |
| title  | 标题        | string | ---     |

### 反馈

### 其他

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
    initialValue: data.pati_group_id ? { label: data.pati_group_name, value: data.pati_group_id } : undefined,
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

