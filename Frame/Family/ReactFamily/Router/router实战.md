# router

## 文件结构

```
└── router/
		└── index.jsx
```

index.jsx

```jsx
import react from 'react';
import { Router, Route, IndexRoute, hashHistory, IndexRedirect } from 'react-router';

import Home from '../home';

export default (
  <Provider store={store} >
    <Router history={hashHistory}>
      <Route path="/" component={Layout} onEnter={onLogin} >
        <IndexRedirect to="" />	// 默认进入的路由路径
        <Route path="home" component={Home} />
        ...
        <Route />
        <Route path="*" component={Basis} /> // 如果没有找到路径，跳转到该路由
      </Route>
    </Router>
  </Provider>
)
```

### 路由跳转 -- 返回

history.go(-1)返回后，原界面数据会丢失

history.back(-1)返回后，会保存原界面上的数据

window.history.go(-1);

this.props.router.goBack();

hashHistory.goBack(-1);



```js
history.go(1);
history.goForward();

history.go(-1); // 返回后，原界面数据会丢失
history.back(-1); // 返回后，会保存原界面上的数据
history.goBack();
```