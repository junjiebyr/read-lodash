# lodash源码——getTag.js

## 功能

通过`Object.protoType.toString.call`方法获取参数类型


## 源码分析
```js
const toString = Object.prototype.toString

/**
 * Gets the `toStringTag` of `value`.
 *
 * @private
 * @param {*} value The value to query.
 * @returns {string} Returns the `toStringTag`.
 */
function getTag(value) {
  if (value == null) {
    return value === undefined ? '[object Undefined]' : '[object Null]'
  }
  return toString.call(value)
}
```
先用 `==` 判断是不是为`null`，然后在判断是否`===undefined`，如果都不是的话，
直接调用`Object.prototype.toString`返回值

## 注意
有点没闹懂， `toString.call(null)` 和 `toString.call(undefined)`直接可以得到对应的结果，为什么还要在用强等判断一遍
