# Ant Design

## component

### From

#### From

| method            | Description                                                  | type                                                         |
| ----------------- | ------------------------------------------------------------ | :----------------------------------------------------------- |
| getFieldDecorator | 用于和表单进行双向绑定                                       |                                                              |
| getFieldValue     | 获取一个输入控件的值                                         | Function(fieldName: string)                                  |
| validateFields    | 校验并获取一组输入域的值与 Error，若 fieldNames 参数为空，则校验全部组件 | (<br/>  [fieldNames: string[]],
  [options: object],
  callback(errors, values)
) => void |
|                   |                                                              |                                                              |



#### From.Item

注意：一个 Form.Item 建议只放一个被 getFieldDecorator 装饰过的 child，当有多个被装饰过的 child 时，`help` `required` `validateStatus` 无法自动生成。

| method | Description | type |
| ------ | ----------- | ---- |
|        |             |      |

