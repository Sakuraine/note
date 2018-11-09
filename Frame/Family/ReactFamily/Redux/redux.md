# redux

## 基础

### Action 

> 把数据从应用传到 store 的有效载荷

> 是 store 数据的**唯一**来源

> action 内必须使用一个字符串类型的`type`字段来表示将要执行的动作

> action 只是描述有事情发生，没有描述应用如何更新

> 尽量减少在 action 中传递的数据

**action.js**

```js
/*
 * action 类型
 */

export const ADD_TODO = 'ADD_TODO';
export const TOGGLE_TODO = 'TOGGLE_TODO'
export const SET_VISIBILITY_FILTER = 'SET_VISIBILITY_FILTER'

/*
 * 其它的常量
 */

export const VisibilityFilters = {
  SHOW_ALL: 'SHOW_ALL',
  SHOW_COMPLETED: 'SHOW_COMPLETED',
  SHOW_ACTIVE: 'SHOW_ACTIVE'
}

/*
 * action 创建函数
 */

export function addTodo(text) {
  return { type: ADD_TODO, text }
}

export function toggleTodo(index) {
  return { type: TOGGLE_TODO, index }
}

export function setVisibilityFilter(filter) {
  return { type: SET_VISIBILITY_FILTER, filter }
}
```

### Reducer

>**Reducers** 指定了应用状态的变化如何响应 [actions](https://www.redux.org.cn/docs/basics/Actions.html) 并发送到 store

#### Action 处理

> reducer 是一个纯函数，接收旧 state 和 action，返回新的 state

```js
(previousState, action) => newState
```

> 保持 reducer 纯净非常重要，**永远不要**在 reducer 里做这些操作：

- 修改传入参数；
- 执行有副作用的操作，如 API 请求和路由跳转；
- 调用非纯函数，如 `Date.now()` 或 `Math.random()`;

> 不要修改 `state`

> 在 `default`情况下返回旧的`state`

**reducers.js**

```js
import { combineReducers } from 'redux'
import {
  ADD_TODO,
  TOGGLE_TODO,
  SET_VISIBILITY_FILTER,
  VisibilityFilters
} from './actions'
const { SHOW_ALL } = VisibilityFilters

function visibilityFilter(state = SHOW_ALL, action) {
  switch (action.type) {
    case SET_VISIBILITY_FILTER:
      return action.filter
    default:
      return state
  }
}

function todos(state = [], action) {
  switch (action.type) {
    case ADD_TODO:
      return [
        ...state,
        {
          text: action.text,
          completed: false
        }
      ]
    case TOGGLE_TODO:
      return state.map((todo, index) => {
        if (index === action.index) {
          return Object.assign({}, todo, {
            completed: !todo.completed
          })
        }
        return todo
      })
    default:
      return state
  }
}

const todoApp = combineReducers({
  visibilityFilter,
  todos
});

export default todoApp;
```

### Store

> 维持应用的state；

> 提供 [`getState()`](https://www.redux.org.cn/docs/api/Store.html#getState) 方法获取 state；

> 提供 [`dispatch(action)`](https://www.redux.org.cn/docs/api/Store.html#dispatch) 方法更新 state；

> 通过 [`subscribe(listener)`](https://www.redux.org.cn/docs/api/Store.html#subscribe) 注册监听器；

> 通过 [`subscribe(listener)`](https://www.redux.org.cn/docs/api/Store.html#subscribe) 返回的函数注销监听器;

> **Redux 应用只有一个单一的 store**

**index.js**

```js
import { createStore } from 'redux';
import todoApp from './reducers';

let store = createStore(todoApp);
```




### 代码结构

> **index.jsx** `view层`

```jsx
import React from 'react';
// 引入action.js里定义的方法
import {
  fetchTestData,
  updataTestData
} from './action';

class View extends React.Component {
// 组件即将更新前
  componentWillMount() {
  	const { dispatch } = this.props;
    // 能且只能通过dispatch()方法获取/更新数据，触发action
    dispatch(fetchTestData());
  }
}

// 遍历传入的数据
export default connect((state) => {
  return {
    //reducer.js里定义的常量
    data: state.testData,
  };
})(Form.create({
  onFieldsChange(props, values) {
  },
  mapPropsToFields(props) {
  }
})(View));
```

> **action.js** `动作层`

用于纯粹的数据处理，尽量不带任何逻辑

action会获取新的数据，但是会将数据交给redecer如何去改变

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

> **reducer.js** `数据层`

处理数据，所有数据的改变都需要通过reducer.js
```js
// 引用combineReducers()方法来处理state树上的分支
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

// 导出，返回处理后的数据
export default combineReducers({
  testData,
});
```

### 数据流向

> 单向数据流

1. **调用 [`store.dispatch(action)`](https://www.redux.org.cn/docs/api/Store.html#dispatch)**

2. **Redux store 接收了dispatch()发送的action，传入 reducer 函数**

   `Store` 会把两个参数传入 `reducer`：当前的state树和action

3. **根 reducer 应该把多个子 reducer 输出合并成一个单一的 state 树**

   使用[`combineReducers()`](https://www.redux.org.cn/docs/api/combineReducers.html)处理state树的分支；

4. 

#### index.jsx

> 通过`import`引入 action.js 内改变数据的方法

```jsx
import {
  fetchTestData,
  updataTestData
} from './action';
```

> 通过`export defaultconnect()`接收 reducer.js 内处理过后的数据

```jsx
export default connect((state) => {
  return {
    //reducer.js里定义的常量
    data: state.testData,
  };
})
```

#### action.js

> 只做对数据的更新处理

```js
export function fetchTestData(param) {
  
}
```

#### reducer.js

>