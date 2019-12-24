HTML5 语言标签

| 元素列表 | Element |                            Description                            |
|--------|:-------:|:-----------------------------------------------------------------:|
|   根元素     |   |  |
|   |&lt;html&gt;| 代表 HTML 或 XHTML 文档的根。其他所有元素必须是这个元素的子节点。 |
| 文档元数据 | | |
|  |&lt;head&gt;| 代表关于文档元数据的一个集合，包括脚本或样式表的链接或内容 |
|  |&lt;title&gt;| 定义文档的标题， 将显示在浏览器的标题栏或标签上。该元素只能包含文本，包含的标签不会被解释。 |
|  |&lt;base&gt;| 定义页面上相对 URL 的基准 URL。 |
|  |&lt;line&gt;| 用于链接外部的 CSS 到该文档。 |
|  |&lt;meta&gt;| 定义其他 HTML 元素无法描述的元数据。 |
|  |&lt;style&gt;| 用户内联 css 样式引用。 |
| 脚本 | | |
|  |&lt;script&gt;| 定认一个内联脚本或者外部脚本。脚本语言是 JavaScript |
|  |&lt;noscript&gt;| 浏览器不支持脚本时显示的替代文字。 |
|  |&lt;template&gt;<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 通过 JavaScript 在运行时实例化内容的template容器。以前是通过 &lt;script type='text/template'&gt;&lt;/script&gt; 来访问模版内容，里面的内容被当做普通字符串处理，而新版 template 是可以把标签内内容转为DOM树被当做文档碎片DocumentFragment |
