## URL、URI和URN的区别

这是一篇科普文，我相信很多人跟我一样，都一直听的 <dfn>URL</dfn> 比较多，会以为 <dfn>URL</dfn> 和 <dfn>URI</dfn> 是一个很相像的东西，实际上他们表达的是不同的东西，下面我们一起来理清一下三个概念。


<dl>
  <dt>
    <dfn>URI</dfn>
  </dt>
  <dd><dfn>URI</dfn>, 全称统一资源标识符 Uniform Resource Identifier, 用来唯一的标识一个资源的。比如：网页文本，文档，图像文件，视频文件，脚本等。</dd>

可以理解为互联网由于大量资源存放在不同的服务器上面，需要交互获取的时候就需要一个统一可识别的标识来定义资源，所以定义了一套 URI 可扩展的命名规则来标识唯一资源。下面看一下 URI 规则。

![URI syntax](./../images/HTTP/URI_syntax_diagram.svg.png)

  <dt>
    <dfn>URL</dfn>
  </dt>
  <dd><dfn>URL</dfn>, 统一资源定位器 Uniform Resource Locator, 通称为Web地址，是对Web资源的引用，指定了它在计算机网络中的位置和检索它的机制标识。</dd>

典型的<dfn>URL</dfn>会采用`http://www.example.com/index.html`形式，由三部分组成:
`http`(网络协议 scheme)`://www.example.com`(域名host)`:8080`(端口号port)`/index.html`(路径文件名或参数path)组成。


  <dt>
    <dfn>URN</dfn>
  </dt>
  <dd><dfn>URN</dfn>, 全称为统一资源名称 Uniform Resource Name, 是通过名字来标识资源。是表示网络资源的路径和名称，<dfn>URN</dfn>是不依赖位置定位的。</dd>
</dl>

URL和URN都是URI的规则下面的实例。

![mcTKF](./../images/HTTP/mcTKf.jpg)

从上图可以看出 URI 是一整套的规则，URL 是表示网络地址某资源的定位，而 URN 是网络上某位置上面的具体文件名称参数。

再看一下下图:

![FbaKm](./../images/HTTP/FbaKm.png)

URI 统一资源标识符规则除了包含 URLs、URNs，还会有其它 URCs Datas等其它实例，所以别搞混了。

### 参考连接

- [HTTP 协议中 URI 和 URL 有什么区别？](https://www.zhihu.com/question/21950864)
- [URI和URL的区别](https://www.jianshu.com/p/ba15d066f777)
- [What is the difference between URI, URL and URN? [duplicate]](https://stackoverflow.com/questions/4913343/what-is-the-difference-between-uri-url-and-urn)
- [URL_WIKI](https://en.wikipedia.org/wiki/URL)