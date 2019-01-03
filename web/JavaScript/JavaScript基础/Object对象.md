# Object对象

<table>
  <tr>
    <th colspan="3">对象属性类型</th>
  </tr>
  <tr>
    <td>属性名</td>
    <td>说明</td>
    <td>默认值</td>
  </tr>
  <tr>
    <td colspan="3">数据属性</td>
  </tr>
  <tr>
    <td>[[Configurable]]</td>
    <td>该属性是否能通过`delete`删除</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Enumerable]]</td>
    <td>该属性是否可枚举</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Writable]]</td>
    <td>该属性是否可更改值</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Value]]</td>
    <td>属性的数据值</td>
    <td>undefined</td>
  </tr>
  <tr>
    <td colspan="3">访问器属性</td>
  </tr>
  <tr>
    <td>[[Configurable]]</td>
    <td>该属性是否能通过`delete`删除</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Enumerable]]</td>
    <td>该属性是否可枚举</td>
    <td>true</td>
  </tr>
  <tr>
    <td>[[Get]]</td>
    <td>在读取属性时调用的函数</td>
    <td>undefined</td>
  </tr>
  <tr>
    <td>[[Set]]</td>
    <td>在写入属性时调用的函数</td>
    <td>undefined</td>
  </tr>
</table>

Object.defineProperty(a, 'name', {})

> 修改属性默认的特性



Object.defineProperties(a, 'name', {})

> 修改属性默认的特性



Object.getOwnPropertyDescriptor(a, 'name')

> 读取属性默认的特性

## 原型

