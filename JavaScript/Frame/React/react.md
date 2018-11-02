# react全家桶的基本结构
> index.jsx `view层`

```js
import React from 'react’;
// 引入action.js里定义的方法
import {
    fetchTestData,
    updataTestData
} from './action';

class View extends React.Component {
    getDefaultProps() {
    //获取初始props
    }
    
    getInitialState() {
    //定义初始state
    }
    
    componentWillMount() {
    //装载前
    }
    
    componentDidMount() {
    //装载后
    }
    
    componentWillReceiveProps(nextProps) {
    //更新前,接收新的props对象
    }
    
    shouldComponentUpdate(nextProps, nextState) {
    //更新前,接收新的props对象
    //返回一个bool值，决定是否更新
    }
    
    compontWillUpdate(nextProps, nextState) {
    //更新前,接收新的props对象
    }
    
    compontWillUpdate(prevProps, prevState) {
    //更新后
    }
    
    componentWillUnmount(nextProps) {
    //卸载前
    }
}

// 遍历传入的数据
export default connect((state) => {
    return {
        //reducer.js里定义的常量
        data: state.testData,
    };
})(Form.create()(View));
```

> action.js `动作层`

用于纯粹的数据处理，尽量不带任何逻辑

```javascript
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
列表//最少需要有两个方法，如果没有，添加一个空的function
export function noop() {}
```

> reducer.js `数据层`

存放数据，所有数据的改变都需要通过reducer.js
```javascript
import { combineReducers } from 'redux';
/**
* data
* @param {Array}     state  [description]
* @param {[type]}    action [description]
* @return {[type]}          [description]
*/
const testData = (state = { list: [] }, action) => {
    switch (action.type) {
        case 'FETCH_CUSTOMER_LIST': {
            return action.data;
        }
        default:
            return state;
    }
};

// 导出
export default combineReducers({
    testData,
});
``` 
