# concat

::: info
此函数与 lodash 完全兼容。您可以在我们的[兼容性库](../../../compatibility.md)中找到它，`es-toolkit/compat`。
:::

将多个数组和值连接成一个数组。

## 签名

```typescript
function concat<T>(...values: Array<T | T[]>): T[];
```

### 参数

- `values` (`...(T | T[])`): 要连接的值和/或数组。

### 返回

(`T[]`): 一个包含所有输入值的新的扁平化数组。

### 示例

```typescript
// 连接单个值
concat(1, 2, 3);
// 返回 [1, 2, 3]

// 连接值的数组
concat([1, 2], [3, 4]);
// 返回 [1, 2, 3, 4]

// 连接单个值和数组的混合
concat(1, [2, 3], 4);
// 返回 [1, 2, 3, 4]

// 连接嵌套数组
concat([1, [2, 3]], 4);
// 返回 [1, [2, 3], 4]
```