## DOCTYPE作用和浏览器模式

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

`DOCTYPE` 是用来声明文档类型和 `DTD` 规范的，一个主要的用途便是文件的合法性验证。 如果文件代码不合法，那么浏览器解析时便会出一些差错。 `HTML` 编辑器通常也会在语法高亮的同时提供合法性验证。声明位于位于HTML文档中的第一行，处于标签之前。告知浏览器的解析器用什么文档标准解析这个文档。DOCTYPE不存在或格式不正确会导致文档以兼容模式呈现。

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

这些模式都是由以前网络上面浏览器战争引起的，各个浏览器都有自己实现的标准，HTML 5 为了不破坏当时即有的网站，浏览器不能直接弃用旧有的这些模式标准。因此，浏览器采用了两种模式，用以把能符合新规范的网站和老旧网站区分开，一种是标准模式另一种是怪异混杂模式。

HTML5 下可以通过 `document.compatMode` 获取当前处理的模式类型。比如 `document.compatMode === 'CSS1Compat'` 就是处于标准模式

- CSS1Compat：标准模式，浏览器使用W3C的标准解析渲染页面。在首行声明了 `<!DOCTYPE html>` 浏览器就会开启标准模式。标准模式则是对统一标准实现最好的模式，它要求标签必须闭合（唯一不需要闭合的就是DOCTYPE标签），不能使用已经废弃的标签等等。

- BackCompat：混合模式&怪异模式。不写 `DOCTYPE` 类型就会默认开启怪异模式。混杂模式是不可取的，因为其没有兼容性可言。在IE（IE6~IE9）中，混杂模式即使用IE5.5内核来解析并渲染页面。可能会出现一些奇怪显示的情况。

- CSS1Compat: 近标准模式，是在尽可能遵循标准的基础上兼容部分非标准代码，比如一些已经弃用的标签等。





参与引用

[怪异模式和标准模式](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Quirks_Mode_and_Standards_Mode)

[DOCTYPE与浏览器模式详解（标准模式&混杂模式)](https://www.cnblogs.com/imxiu/p/3541932.html)


[Doctype作用？DTD是啥？标准模式与兼容模式各有什么区别-](https://www.jianshu.com/p/c0026852f59a)

[简单聊一下DOCTYPE](https://zhuanlan.zhihu.com/p/32460261)

[DOCTYPE的作用：文档类型与浏览器模式](https://harttle.land/2016/01/22/doctype.html)

[DOCTYPE声明作用及用法详解](https://www.jb51.net/web/34217.html)