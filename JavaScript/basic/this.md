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

之前隐匿绑定，都是通过在对象内部包含一个指向函数的属性，并通过这个属性引用函数，从而把 this 间接(隐式)绑定到这个对象之上。而 JavaScript 是有直接绑定 this 的方法的 `call`、`apply`。具体使用用法可以查看[call、apply、bind的用法和区别](./call&apply&bind.md)

```js
function foo() {
  console.log(this.a)
}
var obj = {
  a:2
}
foo.call(obj) //2 通过 call 显式绑定到 obj 上
```

但是显式绑定`call`, `apply`还是一样会出现丢失绑定的问题。
```js
function foo() {
  console.log(this.a)
}
var obj = {
  a: 2
}
foo.call(obj)
var a = 'oops, global'
var bar = foo
bar() // 'oops, global'
```

除了 `bind` 硬式绑定不会出现丢失绑定的情况，其它显示绑定都会丢失，`bind` 在 ES5 开始程序内提供的内置方法 `Function.prototype.bind`。其实的原理是

```js
function foo(something) {
  console.log(this.a, something)
  return this.a + something
}

function bind(fn, obj){
  return function() {
    return fn.apply(obj, arguments) // 通过一个闭包，绑定 对象 和 arguments 的状态
  }
}
var obj = {
  a: 2
}
var bar = bind(foo, obj)
var b = bar(3)
console.log(b)
```

**new 绑定**

**new 绑定**,其实是通过 `new` 新建一个对象并把它绑定到构造函数 `foo()` 里的 `this` 中。

```js
function foo(a) {
  this.a = a
}
var bar = new foo(2)
console.log(bar.a) // 2
```

### `this` 绑定的优先级
