### RegExp 构造函数

```js
const pattern = new RegExp('\\[bc\\]at', 'gi');// 接受两个字符串，正则表达式主体和修饰符（匹配模式）
```

| 长属性名     | 短属性名 | description                              |
| ------------ | -------- | ---------------------------------------- |
| input        | $_       | 最近一次要匹配的字符串                   |
| lastMatch    | $&       | 最近一次的匹配项                         |
| lastParen    | $+       | 最近一次匹配的捕获组                     |
| rightContext | $'       | input字符串中lastMatch之后的文本         |
| lastContext  | $`       | input字符串中lastMatch之前的文本         |
| multiline    | $*       | 布尔值，表示是否所有表达式都是用多行模式 |



### function

#### search()

> 用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串，并返回子串的起始位置。

#### replace()

> 用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。

