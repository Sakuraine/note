# Hooks

Hooks*是React v16.7.0-alpha中加入的新特性。它可以让你在class以外使用state和其他React特性。

## useState

## useEffect



```jsx
import { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;
  });

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```



**完全可选**

**100% 向后兼容**

**立即可用**

**classes不会被移除**

**Hooks不会影响你对React的理解**

