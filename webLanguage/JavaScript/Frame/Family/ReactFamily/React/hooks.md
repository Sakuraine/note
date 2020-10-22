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

# React Hooks

> 在React函数组件中使用状态和副作用的一种方式

- 所有副作用都直接存在于组件中，而没有引入其他组件作为业务逻辑的容器

## 一些流行的React Hooks

### useState Hooks（状态管理）

```jsx
const [thing, setThing] = useState();

setThing(thing => newThing); // use new thing
```

useState挂钩接收一个初始状态作为参数，并通过使用数组解构返回两个可以命名的变量，但是您要为其命名。第一个变量是实际状态，而第二个变量是通过提供新状态来更新状态的函数

useState挂钩为您提供了管理功能组件中的状态所需的一切：初始状态，最新状态和状态更新功能



### useEffect Hooks（副作用）

```jsx
useEffect(() => {
  // effect code
  return () => clearEffect(); // clear effect
}, []);
```

第二个参数是再次运行当前副作用的变量，为空则只在安装和卸载时触发，否则在变量修改时触发

> 建议

把不依赖props和state的函数提到你的组件外面

把仅被effect使用的函数放到effect里面

如果effect还需要用到组件内的函数，包括通过props传进来的函数，可以在定义它们的地方用useCallback包一层

### CUSTOM HOOKS（自定义挂钩）

