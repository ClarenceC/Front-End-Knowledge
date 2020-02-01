## HTTP 首部

在 HTTP 报文首部中包含着平时在客户端和服务器处理至关重要的信息，下面我们一起整理一下。

还记得 [HTTP报文](./HTTP报文.md) 里面由下面两部分组成:
1. **报文首部** 报文主要为客户端和服务器分别处理请求和禹应提供所需要的信息。

2. **报文主体** 一般为用户和资源的信息都在这边。

而**报文首部** 分为两部分:
1. **请求报文首部** 由 HTTP方法，URI、HTTP版本、HTTP首部字段等组成。

2. **响应报文首部** 由 HTTP版本、状态码(数字和原因短语)、HTTP首部字段3部分构成。

### HTTP首部字段

首部字段是为了给浏览器或服务器提供报文主体大小、所使用的语言、认证信息等内容。
HTTP 首部字段结构分为 `首部字段名` : `字段值`像下面

```js
Content-Type: text/html
Keep-Alive: timeout=15, max=100 // 可以存在多值
```

### HTTP首部字段按用途分为4种类型

#### 通用首部字段(General Header Fields)
请求报文和响应报文都会使用的首部。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Cache-Control  |  控制缓存的行为  |
| Connection    |  逐步首部、连接的管理      |
| Date   | 创建报文的日期时间      |
| Pragma  | 报文指令 |
| Trailer  | 报文末端的首部一临览 |
| Transfer-Encoding  | 指定报文主体的传输编码方式 |
| Upgrade  | 升级为其他协议 |
| Via  | 代理服务器的相关信息 |
| Warning  | 错误通知 |

#### 请求首部字段(Request Header Fields)

从客户端浏览器向服务端发送请求报文时使用的首部。补充了请求的附加内容、客户端信息、响应内容相关优先级等信息。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Accept  |  用户代理可处理的媒体类型  |
| Accept-Charset  |  优先的字符集  |
| Accept-Encoding  |  优先的内容编码  |
| Accept-Language  |  优先的语言(自然语言)  |
| Authorization  |  Web认证信息  |
| Expect  |  期待服务器的特定行为  |
| From  |  用户的电子邮箱地址  |
| Host  |  请求资源所在的服务器  |
| If-Match  |  比较实体标记(ETag)  |
| If-Modified-Since  |  比较资源的更新时间  |
| If-None-Match  |  比较实体标记(与If-Match相反)  |
| If-Range  |  资源未更新时发送实体Byte的范围请求  |
| If-Unmodified-Since  |  比较资源的更新时间(与If-Modified-Since相反)  |
| Max-Forwards  | 最大传输逐跳数 |
| Proxy-Authorization  | 代理服务器要求客户端的认证信息 |
| Range | 实体的字节范围请求 |
| Referer | 对请求中 URI 的原始获取方 |
| TE | 传输编码的优先级 |
| User-Agent | HTTP 客户端程序的信息 |

#### 响应首部字段(Response Header Fields)

从服务器端向客户端返回响应报文时使用的首部，补充了响应的附加内容，也会要求客户端附加额外的内容信息。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Accept-Ranges  |  是否接受字节范围请求  |
| Age  |  推算资源创建经过时间  |
| ETag  |  资源的匹配信息  |
| Locations  |  令客户端重定向至指定 URI  |
| Proxy-Authenticate | 代理服务器对客户端的认证信息 |
| Retry-After | 对再次发起请求的时机要求  |
| Server | HTTP服务器的安装信息 |
| Vary | 代理服务器缓存的管理信息 |
| WWW-Authenticate | 服务器对客户端的认证信息 |

#### 实体首部字段(Response Header Fields)

针对请求报文和响应报文的实体部分使用的首部。补充了资源内容更新时间等与实体有关的信息。

| 首部字段名 | 用途                         |
|--------|--------------------------------|
| Allow | 资源可以支持的HTTP方法 |
| Content-Encoding | 实体主体适用的编码方式 |
| Content-Language | 实体主体的自然语言 |
| Content-Length | 实体主体的大小(单位: 字节) |
| Content-Location | 替代对应资源的URI |
| Content-MD5 | 实体主体的报文摘要 |
| Content-Range | 实体主体的报文范围 |
| Content-Type | 实体主体的媒体类型 |
| Expires | 实体主体的过期时间 |
| Last-Modified | 资源最后修改日期时间 |