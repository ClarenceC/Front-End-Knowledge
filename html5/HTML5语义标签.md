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
| 章节 | | |
|  |&lt;body&gt;| 代表html文档的内容，在文档中只能有一个`<body>` 元素。 |
|  |&lt;section&gt;<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 表示文档中的一个章节的内容，里面一般会这个章节的标题和内容 |
|  |&lt;nav&gt;<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 用来表示文档中导航链接的部分，常用来菜单，目录和索引等。 |
|  |&lt;article&gt;<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 用来表示内容期余部分的独立上的内容，也包括会有标题和完整独立的内容块 |
|  |`<h1>,<h2>,<h3>,<h4>,<h5>,<h6>`| 标题元素实现了六层文档标题，`<h1>` 是最大的标题，`<h6>` 是最小的标题。标题元素简要地描述章节的主题。 |
|  |`<header>`<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 主要用于展示介绍性内容，通常包含一组介绍性的或是辅助导航的实用元素。它可能包含一些标题元素，但也可能包含其他元素，比如 Logo、搜索框、作者名称，等等。 |
|  |`<footer>`<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 用于表示最近一个章节内容或者根节点（sectioning root ）元素的页脚。一个页脚通常包含该章节作者、版权数据或者与文档相关的链接等信息。 |
|  |`<address>`<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 用于放置提供了某个人或某个组织（等等）的联系信息。 |
|  |`<main>`<img width='16px' height='16px' src='./../images/HTML5_32.png'>| 主要用于呈现了文档的 `<body>` 或应用的主体部分。主体部分由与文档直接相关，或者扩展于文档的中心主题、应用的主要功能部分的内容组成。并且内容对于文档来说应当是唯一的。它不应包含在文档中重复出现的内容，比如侧栏、导航栏、版权信息、站点标志或搜索表单。`<main>` 元素不能是以下元素的后代：`<article>`、`<aside>`、`<footer>`、`<header>` 或 `<nav>`。 |