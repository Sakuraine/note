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

