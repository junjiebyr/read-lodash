# lodash 源码——isSymbol.js

## 功能

判断参数是否为 symbol 类型

## 依赖

```js
import getTag from "./.internal/getTag.js";
```

[lodash 源码——getTag.js](internal/getTag.md)

## 源码分析

```js
/**
 * Checks if `value` is classified as a `Symbol` primitive or object.
 *
 * @since 4.0.0
 * @category Lang
 * @param {*} value The value to check.
 * @returns {boolean} Returns `true` if `value` is a symbol, else `false`.
 * @example
 *
 * isSymbol(Symbol.iterator)
 * // => true
 *
 * isSymbol('abc')
 * // => false
 */
function isSymbol(value) {
    const type = typeof value;
    return (
        type == "symbol" ||
        (type === "object" &&
            value != null &&
            getTag(value) == "[object Symbol]")
    );
}
```
先使用`typeof`判断是不是`symbol`，然后通过`Object.protoType.toString`来再次判断是不是`symbol`。