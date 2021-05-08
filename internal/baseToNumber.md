# lodash 源码——baseToNumber.js

## 功能

将参数转成 number 类型的基本方法

## 依赖

```js
import isSymbol from "../isSymbol.js";
```

[lodash 源码——isSymbol.js](internal/isSymbol.md)

## 源码分析

```js
/** Used as references for various `Number` constants. */
const NAN = 0 / 0;

/**
 * The base implementation of `toNumber` which doesn't ensure correct
 * conversions of binary, hexadecimal, or octal string values.
 *
 * @private
 * @param {*} value The value to process.
 * @returns {number} Returns the number.
 */
function baseToNumber(value) {
    if (typeof value === "number") {
        return value;
    }
    if (isSymbol(value)) {
        return NAN;
    }
    return +value;
}
```
对`value`值进行判断，如果是`number`类型，直接返回。然后通过`isSymbol`判断`value`
是不是`symbol`，是的话返回`NAN`。最后通过类型转换返回`number`值。


## 注意事项
```js
let a = new Number(5);
console.log(typeof a)  // object

console.log(typeof +a) // number
```

