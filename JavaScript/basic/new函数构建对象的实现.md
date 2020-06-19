## new 函数构建对象的实现

在使用 `new` 来调用函数时，构造函数会自动执行下面的操作。

1. 创建一个全新的对象。
2. 这个新对象会被执行[[Prototype]]的连接。
3. 这个新对象会绑定到函数调用的`this`。
4. 如果函数没有返回其他对象，那么 `new` 表达式中的函数调用会自动返回这个新对象。


来源 [mqyqingfeng](https://github.com/mqyqingfeng/Blog/issues/13)

```js
function objectFactory() { // 模拟 new
  var constructor = [].shift.call(arguments) // 分离构建函数和参数
  var obj = Object.create(constructor.prototype)  // 新建对象继承至构建函数原型对象的
  var ret = constructor.apply(obj, arguments) // 绑定到函数调用的 this
  return typeof ret === 'object' ? ret : obj // 返回对象
}
```

`ES6` 写法

```js
function _new(fn, ...args) {
  const obj = {}
  Object.setPrototypeOf(obj, fn.prototype)
  const ret = fn.apply(obj, args)
  return typeof ret === 'object' && ret ? ret : obj
}
```

or

```js
function ownNew(fn, ...args) {
  const obj = Object.create(fn.prototype)
  const result = fn.call(obj, ...args)
  return typeof result === 'object' && result ? result : obj
}
```