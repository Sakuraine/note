# Mackdown
## 标题

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

> 语法
```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```
#和标题之间用空格分隔开

## 字体

**加粗**
*斜体*
***斜体加粗***
～～删除线～～

> 语法
```
**加粗**
*斜体*
***斜体加粗***
～～删除线～～
```

## 引用
> 引用
>
> > 引用

> 语法
```
> 引用
>> 引用
```

## 分割线
***
*****

> 语法
```
***
*****
```

## 列表
### 无序列表
- 列表内容
    - 列表内容
        - 列表内容
+ 列表内容
    + 列表内容
        + 列表内容
* 列表内容
    * 列表内容
        * 列表内容

> 语法
```
- 列表内容
    - 列表内容
        - 列表内容
+ 列表内容
    + 列表内容
        + 列表内容
* 列表内容
    * 列表内容
        * 列表内容
```

### 有序列表
1. 列表内容
    1. 列表内容
    2. 列表内容
2. 列表内容

> 语法
```
1. 列表内容
    1. 列表内容
    2. 列表内容
2. 列表内容
```

### 列表嵌套
上一级和下一级之间敲三个空格即可

## 表格
表  头|表  头|表  头
:----|:---:|-----:
内容|内容|内容|

> 语法
```
表  头|表  头|表  头
:-----|:---:|-----:
内容|内容|内容|
```
第二行分割表头和内容。
-有一个就行，为了对齐，多加了几个
文字默认居左
-两边加:表示文字居中
-右边加:表示文字居右
注：原生的语法两边都要用 | 包起来


## 代码
### 单行代码
`function() {}`

> 语法
```
`function() {}`
```

### 代码块
```
function(){}
```

> 语法
```js
​```js
	function() {
		alert('hellow, world');
	}
(防止编译)```
```

## 其他
### 任务
* [ ] 任务
* [x] 已完成

> 语法
```
* [] 任务
* [x] 已完成
```

### 超链接
[百度一下](https://www.baidu.com)

> 语法
```
[百度一下](https://www.baidu.com)
```

### 设置目录
[TOC]

> 语法
```
[TOC]
```

设置之后可以自动根据设置的分级标题来自动生成目录

### 图片

![image](https://www.yinxiang.com/blog/wp-content/uploads/2018/07/%E5%94%AE%E7%A5%A8%E5%BE%AE%E4%BF%A1%E5%B0%81%E9%9D%A22.png)@w=300h=150


> 语法

```
![图片alt](图片地址 ''图片title'')@w=宽度h=高度
```

### 数学公式

```math
e^{i\pi} + 1 = 0
```



### 图表

#### 饼状图&折线图&柱状图&条形图

```chart
,预算,收入,花费,债务
June,5000,8000,4000,6000,
July,3000,1000,4000,3000,
Aug,5000,7000,6000,3000,
Sep,7000,2000,3000,1000,
Oct,6000,5000,4000,2000,
Nov,4000,3000,5000,

type: pie
title: 每月收益
x.title: Amount
y.title: Month
y.prefix: $
y.suffix: $
```

> 语法
```
(```)chart
,预算,收入,花费,债务
June,5000,8000,4000,6000
July,3000,1000,4000,3000
Aug,5000,7000,6000,3000
Sep,7000,2000,3000,1000
Oct,6000,5000,4000,2000
Nov,4000,3000,5000,

type: pie
title: 每月收益
x.title: Amount
y.title: Month
y.suffix: $
(```) //括号防止编译
```

##### type:
饼状图：pie
折线图：line
柱状图：column
条形图：bar

#### 流程图

```mermaid
graph TD

A[模块A] --> |A1| B(模块B)
B --> C{判断条件C}
C -->|条件C1| D[模块D]
C -- 条件C2 --> E[模块E]
C -->|条件C3| F[模块F]

a默认节点
b[文本节点]
c(圆角节点)
d((圆形节点))
e>非对称节点]
f{菱形节点}
```

**连线**

```mermaid
graph TB
A1-->B1
A2---B2
A3--text---B3
A4--text-->B4
A5-.-B5
A6-.->B6
A7-.text.-B7
A8-.text.->B8
A9===B9
A10==>B10
A11==text===B11
A12==text==>B12
```

> 语法
```
(```)mermaid
graph TB //（top bottom）表示从上到下
graph TD //（top bottom）表示从上到下
graph BT //（bottom top）表示从下到上
graph RL //（right left）表示从右到左
graph LR //（left right）表示从左到右

A[模块A] -->|A1| B(模块B)
B --> C{判断条件C}
C -->|条件C1| D[模块D]
C -->|条件C2| E[模块E]
C -->|条件C3| F[模块F]

a默认节点
b[文本节点]
c(圆角节点)
d((圆形节点))
e>非对称节点]
f{菱形节点}
(```) //括号防止编译
```

或者

```flow
st=>start: 开始
e=>end: 结束
op=>operation: 我的操作
cond=>condition: 确认？

st->op->cond
cond(yes)->e
cond(no)->op

```

#### 时序图

```mermaid
sequenceDiagram
    A->>B: 是否已收到消息？
    B-->>A: 已收到消息
```

> 语法
```
(```)mermaid
sequenceDiagram
A->>B: 是否已收到消息？
B-->>A: 已收到消息
(```) //括号防止编译
```
#### 甘特图

```mermaid
gantt
title 甘特图
section 项目A
任务1:a1, 2018-06-06, 30d
任务2     :after a1  , 20d
section 项目B
任务3      :2018-06-12  , 12d
任务4      : 24d
```

> 语法
```
(```)mermaid
gantt
title 甘特图
dateFormat  YYYY-MM-DD
section 项目A
任务1           :a1, 2018-06-06, 30d
任务2     :after a1  , 20d
section 项目B
任务3      :2018-06-12  , 12d
任务4      : 24d
(```) //括号防止编译
```

## 高级用法
> 当你看到这里的时候，说明你的md已经可以出山了

GitHub上设置微标：

- 在 `https://shields.io/#/` 生成svg图标；
  svg链接格式：
  https://img.shields.io/badge/{徽标标题}-{徽标内容}-{徽标颜色}.svg

- 在项目的README.md内引入

  `![image](svg链接)`
