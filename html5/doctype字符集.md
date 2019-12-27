## DOCTYPE和字符集

### HTML5 DOCTYPE 的化繁为简

HTML5 遵守华繁为简准则，简化了 DOCTYPE, 
在HTML4 的时候 DOCTYPE 是下面这样样式的

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTA HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

在HTML5 的时候只需要

```html
<!DOCTYPE html>
```

就可以声明 HTML5 页面了

### DOCTYPE 声明的作用

`DOCTYPE` 是用来声明文档类型和 `DTD` 规范的，一个主要的用途便是文件的合法性验证。 如果文件代码不合法，那么浏览器解析时便会出一些差错。 `HTML` 编辑器通常也会在语法高亮的同时提供合法性验证。

**DTD**（document type definition，文档类型定义）是一系列的语法规则， 用来定义XML或(X)HTML的文件类型。浏览器会使用它来判断文档类型， 决定使用何种协议来解析，以及切换浏览器模式。

因为 HTML 4.01 是基于 SGML的， 所以在 HTML 4.01 之前会有很多不同的方式来配置 DTD 规则，这样浏览器才能正确地呈现浏览器规则内的内容，也会提示一些不符合规则的错误。

而 HTML5 是不基于 SGML，所以不需要引用 DTD。所以只需要简单写就可以了.

`<!DOCTYPE html>`

### DOCTYPE 模式

在以前 HTML 混乱的时代有很多种显示模式，比如:
- 怪异模式(Quirks)
- 近标准模式(Almost Standars)
- 标准模式(Standards)
- 非怪模式(no-quirks)






参与引用


