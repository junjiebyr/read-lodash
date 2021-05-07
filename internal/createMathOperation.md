# lodash 源码——createMathOperation.js

## 功能

返回一个函数，实现两个数的数学运算

## 依赖

```js
import baseToNumber from "./baseToNumber.js";
import baseToString from "./baseToString.js";
```

[lodash 源码——baseToNumber.js](internal/lodash源码——baseToNumber.md)
[lodash 源码——baseToString.js](internal/lodash源码——baseToString.md)

## 源码分析

```js
/**
 * Creates a function that performs a mathematical operation on two values.
 *
 * @private
 * @param {Function} operator The function to perform the operation.
 * @param {number} [defaultValue] The value used for `undefined` arguments.
 * @returns {Function} Returns the new mathematical operation function.
 */
function createMathOperation(operator, defaultValue) {
    return (value, other) => {
        if (value === undefined && other === undefined) {
            return defaultValue;
        }
        if (value !== undefined && other === undefined) {
            return value;
        }
        if (other !== undefined && value === undefined) {
            return other;
        }
        // 如果有一个是字符串，则转成字符串的数学运算操作
        // 否则转成number类型操作
        if (typeof value === "string" || typeof other === "string") {
            value = baseToString(value);
            other = baseToString(other);
        } else {
            value = baseToNumber(value);
            other = baseToNumber(other);
        }
        return operator(value, other);
    };
}
```

最终返回一个函数。传入的`operator`数学运算方法，再判断数字类型后，对两个数字进行运算。
