# HTML5语义标签 section和article的区别

### `<div>`
> HTML Spec: “The div element has no special meaning at all.”

`div` 是没语义标签,使用得最多的标签, HTML5 更倾向于语义标签，在没办法用语义标签表达的时候才会使用没语义标签用来布局样式化和脚本编写等需要使用`div`。

### `<section>`

> HTML Spec: “The section element represents a generic section of a document or application. A section, in this context, is a thematic grouping of content, typically with a heading.”

`<section>` 是语义标签，在文档和应用通用的部分都使用，不过不是通用标签。`section` 我的理解是相互关联，联合一起来的相关性内容会使用 `<section>` 区分单独每一个章节回合，比如一般会使用在内容的章节的主题分组，标题分组标签页分组等。`<section>` 标签内部一般也会带有标题内容等，那和 `<article>` 怎样区分呢？




### `<article>`

> The article element represents a complete, or self-contained, composition in a document, page, application, or site and that is, in principle, independently distributable or reusable, e.g. in syndication. This could be a forum post, a magazine or newspaper article, a blog entry, a user-submitted comment, an interactive widget or gadget, or any other independent item of content.

`<article>` 是一个更独立更原子性的一个内容语义标签，可以使用在很多常见的地方，但是更原子性代表一个独立的个体，可以在其它地方重用重新组合等。比如 Forum post、 Blog post、 News story、Comment 等，`<article>` 有自己独立表达的标题和内容。



```
<article class="carousel">
	<section class="picture-titles">
		<!-- 
		Some code goes here.  
		maybe just an h3, who knows?
		--!>
	</section>
	<section class="pictures">
		<div>
			<img>
			<!-- etc. --!>
		</div>
	<section>
	<section class="arrow-nav">
		<!-- More code! --!>
	</section>
</article>
```



参考

[你如何理解 HTML5 的 section？会在什么场景使用？为什么这些场景使用 section 而不是 div？](https://www.zhihu.com/question/20227599)

[div section 和article的区别](https://www.jianshu.com/p/b818ceeedd13)

[HTML5 中 div section article 的区别](https://www.qianduan.net/html5-differences-in-the-div-section-article/)

[HTML Standard](https://html.spec.whatwg.org/multipage/sections.html#the-article-element)

[HTML5：div、section、article 的区别](https://www.jianshu.com/p/0c37d5d15969)
