## call、apply、bind对比和实现

### function.call(thisArg, arg1, arg2, ...)

函数可以通过 `call` 函数来绑定传参对象作为函数的 `this`, `arg1`、`arg2`是传到 `Function` 里面的参数对象调用。

```js
function Product(name, price) {
  this.name = name
  this.price = price
}

function Food(name, price) {
  Product.call(this, name, price)
  this.category = 'food'
}

console.log(new Food('cheese', 5).name) // 通过 new 来把 this 传到 Product 里面执行。
```

```js
var foo = {
  value: 1
}
function bar() {
  console.log(this.value)
}
bar.call(foo) // 1
```

#### call 函数手写实现

mqyqingfeng 的实现用的 `ES5` 语法
```js
Function.prototype.call = function(context) {
  var context = context || window
  context.fn = this // 获取当前调用 call2 的函数，并绑定到 conext 对象属性上
  var args = []
  for (var i = 1, len = arguments.length; i < len; i++) {
    args.push('arguments[' + i + ']')
  }
  var result = eval('context.fn('+ args +')') // 通过 eval 函数调用运行结果
  delete context.fn
  return result
}
```


`ES6` 语法

```js
Function.prototype.call = function(context, ...args) {
  const tempContext = (typeof context === 'object' ? context : window)
  const runFn = Symbol()
  tempContext[runFn] = this
  const result = tempContext[runFn](...args)
  delete tempContext[runFn]
  return result
}
```

### function.apply(thisArg, [argsArray])

apply 函数和 call 函数很像，都是函数可以通过 `apply` 函数来绑定传参对象作为函数的 `this`, 但是传参方面接受的参数是数组参数 `[argsArray]`

```js
function fun(arg1, arg2) {
  console.log(this.name, arg1 + arg2)
}
const obj = { name: 'foo' }
fun.apply(obj, [5, 2]) // foo 7
```


#### apply 函数手写实现

`ES5` 方法
```js
Function.prototype.apply = function(context, arr) {
  var context = Object(context) || window
  context.fn = this
  var result 
  if (!arr) {
    result = conext.fn()
  } else {
    var args = []
    for (var i = 0, len = arr.length; i < len; i++) {
      args.push('arr['+ i +']')
    }
    result = eval('context.fn(' + args + ')')
  }
  delete context.fn
  return result
}
```

`ES6` 方法
```js
Function.prototype.apply = function(context, args) {
  const tempContext = ( typeof context === 'object'? context : window )
  const runFn = Symbol()
  tempContext[runFn] = this
  const result = tempContext[runFn](...args)
  delete = tempContext[runFn]
  return result
}
```


从手动实现里可以看得出 `call`、`apply` 函数都是[隐式绑定](./this.md) `this` 实现的。而 `bind` 是硬绑定。

### function.bind(thisArg, arg1, arg2, ...) return function

`bind()` 方法创建一个新的函数，在 `bind()` 被调用时，这个新函数的 `this` 被指定为 `bind()` 的第一个参数，而其余参数将作为新函数的参数，供调用时使用。
`bind` 特别的地方在于会创建一个**绑定函数(bound function, BF)**, 绑定函数会绑定传进去的 `this` 对象，并在返回值返回。当执行 `bind` 生成的这个函数，就会调用绑定函数运行。


```js
function fun(arg1, arg2) {
  console.log(this.name, arg1 + arg2)
}
const obj = {
  name: 'foo'
}
const newFun = fun.bind(obj)
newFun(4, 5) // foo 9
```


#### bind 函数手写实现

`ES5` 实现来源 [mqyqingfeng](https://github.com/mqyqingfeng/Blog/issues/12)
```js
Function.prototype.bind = function(context) {
  if (typeof this !== 'function') {
    throw new Error('Function.prototype.bind - what is trying to be bound is not callable')
  }
  var self = this
  var args = Array.prototype.slice.call(arguments, 1)

  var fNOP = function () {}
  var fBound = function () {
    var bindArgs = Array.prototype.slice.call(arguments)
    var tempContext = this instanceof fNOP ? this : conext
    return self.apply(tempContext, args.concat(bindArgs))
  }
  fNOP.prototype = this.prototype // 让 fNOP 继承 this.prototype 的属性和方法
  fBound.prototype = new fNOP() // 创建 返回函数的继承链
  return fBound
}
```

**Polyfill**
```js
if (!Function.prototype.bind1) (function() {
  var slice = Array.prototype.slice
  Function.prototype.bind1 = function() {
    var thatFunc = this
    thatArg = arguments[0]
    var args = slice.call(arguments, 1)
    if (typeof thatFunc !== 'function') {
      throw new TypeError('Function.prototype.bind -' + 'what is trying to be bound is not callable')
    }
    return function() {
      var funcArgs = args.concat(slice.call(arguments))
      return thatFunc.apply(thatArg, funcArgs)
    }
  }
})()
```

`ES6` 实现
```js
Function.prototype.bind = function(context) {
  const runFun = this
  const bindObject = arguments[0]
  const args = Array.prototype.slice(arguments, 1)
  if (typeof runFun !== 'function') {
    throw new TypeError('Function.prototype.bind -' + 'what is trying to be bound is not callable')
  }
  return function(...params){
    return runFun.apply(bindObject, args.concat(params))
  }
}
```

### 参考引用

- [JavaScript深入之call和apply的模拟实现](https://github.com/mqyqingfeng/Blog/issues/11)
- [JavaScript深入之bind的模拟实现](https://github.com/mqyqingfeng/Blog/issues/12)
