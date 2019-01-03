# react
## 页面结构

### 单页结构

```
└── FlieName/                            	文件名称
 		├── action.js													数据处理层
 		├── controller.jsx										逻辑层
 		|── index.js													入口
 		|── reducer.js												数据层
		└── view.jsx                   				视图层
```

> action.js

```js
import { fetchutil } from 'util';
/**
* 调用接口
* @param {[type]} param [description]
*/
export function fetchTestData(param) {
  return (dispatch) => {
    return fetchutil.get('/sys_service/customer/source/list', { param }).then(
      (res) => {
        const data = res.data;
        if (data) {
          dispatch({ type: 'FETCH_CUSTOMER_LIST', data });
        }
      }
    );
  };
}
//最少需要有两个方法，如果没有，添加一个空的function
export function noop() {}

```

> controller.jsx

```

```

> index.js

```js
import Module from './controller.jsx';

export default Module;

```



### list&detail结构

    ├── FlieName/                            	名称
    │   ├── List/          	                  列表界面
    |		|		├──index.js												
    |		|		├──view.js												
    |		|		├──action.js											
    |		|		└──reducer.js											
    │   └── Detail/                           详情界面
    |		|		├──index.js												
    |		|		├──action.js											
    |		|		└──reducer.js											
    ├── index.js                          		外层index
    └── reducer.js                    				外层reducer

```

```

