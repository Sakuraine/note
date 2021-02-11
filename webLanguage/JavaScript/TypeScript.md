# TypeScript

TypeScript 是 JavaScript 的 **超集**

TypeScript 是 **静态类型检查** 的 **弱类型**

## 安装

### for Mac

打开终端

```
$ npm install -g typescript
```

## 编译

打开终端

```
tsc <file-name.ts>
```

## 基础类型

### 布尔值

```typescript
let isDone: boolean = false;
```

### 数字

```typescript
let decLiteral: number = 6; // 10进制
let hexLiteral: number = 0xf00d; // 16进制
```

### 字符串

```typescript
let name: string = "bob";
```

### 数组

TypeScript像JavaScript一样可以操作数组元素。 有两种方式可以定义数组。 第一种，可以在元素类型后面接上`[]`，表示由此类型元素组成的一个数组：

```typescript
let list: number[] = [1, 2, 3];
```

第二种方式是使用数组泛型，`Array<元素类型>`：

```typescript
let list: Array<number> = [1, 2, 3];
```