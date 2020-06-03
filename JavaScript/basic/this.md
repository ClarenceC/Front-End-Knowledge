## this 关键字

在 JavaScript 中 this 是最复杂的机制之一。
很多程序员对 this 会有误解, 常见的有下面的情况:
1. 以为 this 是指向函数自身，其实不是，会被绑定的时候才会指向函数对象本身。
2. 把 this 理解成指向函数的作用域，会有某些情况下正确。

this 是在运行时进行绑定的，并不是编写时绑定，它的上下文取决于函数调用时的各种条件，并取决于函数的调用方式。当一个函数被调用时，会创建一个活动记录(执行上下文)，这个记录会包含函数在哪里被调用、函数的调用方式、传入参数等信息。this 就是这个记录的一个属性，会在函数执行的过程中用到。

### this 是如何被绑定

有下面几种方式来绑定 this 的:

- **默认绑定**, 函数直接使用不带任何修饰的函数引用进行调用的，就会默认绑定。如果在 strict mode 模式下则不会出现默认绑定。如果默认绑定函数在非 strict mode 下定义，在 strict mode下调用则不受影响。

```js
function foo() {
  console.log(this.a)
}
var a = 2
foo() // 2
```

- **隐匿绑定**, 需要考虑调用位置是否有上下文对象，或被某个对象拥有包含。

```js
function foo() {
  console.log(this.a)
}
var obj = {
  a: 2,
  foo: foo
}
var a = 3
obj.foo() // 2
```

当 foo 在 obj 内被调用的时候, this 调用位置会使用 obj 上下文来引用函数。因此你可以说函数被调用时 obj 对象"拥有"或"包含"它。

对象属性引用链只对引用上一层或最后一层调用位置中起作用。

```js
function foo() {
  console.log(this.a)
}
var obj2 = {
  a: 42,
  foo: foo
}
var obj1 = {
  a: 2,
  obj2: obj2
}
obj1.obj2.foo() //42
```

**隐匿绑定**，有一个常见的 this **隐式丢失**的情况, 也就是它丢失了**隐匿绑定** 会应用回 **默认绑定**， 从而把 this 绑定到全局对象或 undefined 上。

ExampleOne
```js
function foo() {
  console.log(this.a)
}
var obj = {
  a: 2,
  foo: foo
}
var bar = obj.foo
var a = 'oops, global'
bar() // 'oops, global' bar 丢失了 foo 的执行上下文
```

ExampleTwo
```js
function foo() {
  console.log(this.a)
}
function doFoo(fn) {
  // fn 引用的是 foo，参数传递其实是一种隐匿赋值
  fn() // 调用
}
var obj = {
  a: 2,
  foo: foo
}
var a = 'oops, global'
doFoo(obj.foo) // oops, global
```

ExampleThree
```js
function foo() {
  console.log(this.a)
}
var obj = {
  a: 2,
  foo: foo
}
var a = 'oops, global'
setTimeout(obj.foo, 100) // 'oops, global' 系统函数传递一样是会丢失执行上下文
```

- **显式绑定**

