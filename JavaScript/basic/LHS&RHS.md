## LHS和RHS

### LHS和RHS是啥?

在 `JavaScript` 里面, 基于编译器立场理解赋值操作符表达式，操作符表达式可以分为 LHS(Left-Hand-Side) 和 RHS(Right-Hand-Side), 如果用 等号来作为例子，像 `var a = 1`

**LHS** 就表示对变量 `a` 进行作用域查询，查找是否有 `a` 变量并声明作用域。

**RHS** 就表示获取 `=` 右边的值。

如果 **LHS** 和 **RHS** 在当前作用域下都获取不了全部变量，就会往上一级查找。如果所有作用域都没有该变量就会抛出异常 `ReferenceError`。在 ES5 非“严格模式”下， JavaScript 还会为全局作用域中的变量自动创建变量声明，这是 JavaScript 的引擎自动操作的，"严格模式"下则不会。


