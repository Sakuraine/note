promise 表示一个最终值，该值由一个操作完成时返回

- promise 有三种状态：**未完成** (unfulfilled)，**完成** (fulfilled) 和**失败** (failed)。
- promise 的状态只能由**未完成**转换成`完成`，或者**未完成**转换成**失败** 。
- promise 的状态转换只发生一次。

Promise对象

```javascript
const promise = nwe Promise((resolve, reject) => {
  // ... some code
  if (/* 异步操作 */) {
  	resolve(value);
  } else {
		reject(error);
	}
})
```

