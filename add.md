# lodash源码——add.js

## 功能

实现两数相加

## 依赖

```js
import createMathOperation from './.internal/createMathOperation.js'
```
[lodash源码——createMathOperation.js](internal/lodash源码——createMathOperation.md)


## 源码分析
```js
/**
 * Adds two numbers.
 *
 * @since 3.4.0
 * @category Math
 * @param {number} augend The first number in an addition.
 * @param {number} addend The second number in an addition.
 * @returns {number} Returns the total.
 */
const add = createMathOperation((augend, addend) => augend + addend, 0)
```

调用了`createMathOperation`方法，传入一个`function`和默认值0，返回了一个函数
