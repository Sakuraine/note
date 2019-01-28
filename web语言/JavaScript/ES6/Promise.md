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

