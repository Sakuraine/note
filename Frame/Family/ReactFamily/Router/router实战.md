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

