ICT: Information and Communication Technology

## HTTP - Hypertext Transfer Protocol

HTTP is an RPC(remote procedure call) protocol. RPC is a request–response protocol.

A client creates a Request containing a Url, Method, Headers, and optional Body and sends this to a server. The server then decodes this Request, does some work, and sends back a Response.

The Url works as a way to subdivide an IP address/domain into further addressable resources. The Method indicates what kind of operation we're trying to perform (get something, submit something, update something, etc.)

```
     Request
|-----------------|
| Url             |
| Method          |
| Headers         |
|-----------------|
| Body (optional) |
|-----------------|
```

A Response consists of a StatusCode, Headers, and optionally a Body. The client then decodes the Response, and can then operate on it. Usually the first thing it does is check the status code to see if its Request was successful or not, and then moves on to the information contained within the headers.

```
     Response
|-----------------|
| StatusCode      |
| Headers         |
|-----------------|
| Body (optional) |
|-----------------|
```

Both Request and Response include Headers. This is like key-value metadata for HTTP requests.

[HTTP/1.1 RFC](https://www.w3.org/Protocols/rfc2616/rfc2616-sec1.html)

1991-08-06 World Wide Web
1997-01 HTTP/1.1 RFC 2068
1999-06 HTTP/1.1 RFC 2616
2015-05-14 HTTP/2 RFC 7540
2019-09-12 HTTP/3 Internet-Draft

HTTP-over-QUIC was renamed to HTTP/3 in November 2018.

HTML5 2014-10-28 W3C Recommendation
ES6 2015-06-18 JavaScript 2015

### Response Status Code

200（OK） - 表示已在响应中发出
201（created）- 如果新资源被创建
202（accepted）- 已接受处理请求但尚未完成（异步处理）
204（无内容） - 资源有空表示
301（Moved Permanently） - 资源的 URI 已被更新
303（See Other） - 其他（如，负载均衡）
304（not modified）- 资源未更改（缓存）
400（bad request）- 坏请求（如，参数错误）
401 (Not Authorized) 未授权 , 请求要求进行身份验证
404（not found）- 资源不存在
406（not acceptable）- 服务端不支持所需表示
408 请求超时, 服务器等候请求时超时。
409（conflict）- 通用冲突
412（Precondition Failed）- 前置条件失败（如执行条件更新时的冲突）
415（unsupported media type）- 请求的媒体类型不受支持
500（internal server error）- 通用错误响应
502 (Bad Gateway) - 网关错误
503 (Service Unavailable) - 服务端当前无法处理请求
504 (Gateway Timeout) - 网关超时

### HTTP Method

RESTful Api
Verb Path Action Notes
GET /creature => Creature.all()
POST /creature => Creature.create() Create with no-id, id is auto-generated
POST /creature/1 => Creature.create() Create with id "1"
GET /creature/1 => Creature.show()
PUT /creature/1 => Creature.update()
PATCH /creature/1 => Creature.update() Partial update
DELETE /creature/1 => Creature.destroy()

# CORS

跨域资源共享 (Cross-origin resource sharing)，简称 CORS。

跨域请求与普通的 HTTP 请求不一样的是，添加了 Origin 请求头，它指示了请求来自于哪个站点，这个请求头是浏览器在发现本次为跨域请求时自动添加的，目的就是告知服务器本次请求是那个域发起的，而此时，如果服务器允许本次请求响应的数据是可以共享的，那么服务器需要添加一个 Access-Control-Allow-Origin 响应头，并指明可以共享数据的域。

在 CORS 中，所有的跨域请求被分为了两种类型，一种是简单请求，一种是复杂请求。

满足以下所有条件，被视为简单类型的请求：

1：请求方法必须是 GET、HEAD、POST 中的一种，其他方法不行；

2：请求头类型只能是 Accept、Accept-Language、Content-Language、Content-Type，添加其他额外请求头不行；

3：请求头 Content-Type 如果有，值只能是 text/plain、multipart/form-data、application/x-www-form-urlencoded 中的一种，其他值不行；

4：请求中的任意 XMLHttpRequestUpload 对象均没有注册任何事件监听器；

5：请求中没有使用 ReadableStream 对象。

而以上的条件有任意一条不满足，则视为复杂类型的请求；如果是复杂请求，浏览器会先发送 OPTIONS 方法的请求以取得服务器的确认，服务器则需要对 OPTIONS 请求做出响应，如果得不到服务器确认，浏览器就不会发送正式请求。

CORS 头信息及对应的含义：

Access-Control-Allow-Origin - 指示请求的资源能共享给哪些域，可以是具体的域名或者 \* 表示所有域。

Access-Control-Allow-Credentials - 指示当请求的凭证标记为 true 时，是否响应该请求。

Access-Control-Allow-Headers - 用在对预请求的响应中，指示实际的请求中可以使用哪些 HTTP 头。

Access-Control-Allow-Methods- 指定对预请求的响应中，哪些 HTTP 方法允许访问请求的资源。

Access-Control-Expose-Headers - 指示哪些 HTTP 头的名称能在响应中列出。

Access-Control-Max-Age - 指示预请求的结果能被缓存多久。

Access-Control-Request-Headers -用于发起一个预请求，告知服务器正式请求会使用那些 HTTP 头。

Access-Control-Request-Method - 用于发起一个预请求，告知服务器正式请求会使用哪一种 HTTP 请求方法。

Origin - 指示获取资源的请求是从什么域发起的。

## Proxy

A proxy acts as an intermediary. A proxy uses the same protocol throughout, it can alter the network flow, do caching or security scanning etc.

A forward proxy, or gateway, or just "proxy" provides proxy services to a client or a group of clients.

TOR (The Onion Router), routes internet traffic through multiple proxies for anonymity.

A forward proxy acts in behalf of clients (or requesting hosts), a reverse proxy acts in behalf of servers. Reverse proxies have several use cases, a few are:

- Load balancing: distribute the load to several web servers,
- Cache static content: offload the web servers by caching static content like pictures,
- Compression: compress and optimize content to speed up load time.

## Tunnel

Tunneling is the technique of using one protocol to transport data inside another protocol.
Tunneling transmits private network data and protocol information through public network by encapsulating the data.

Tunnel providers are called proxies.

For example you can use a SOCKS proxy as a HTTP tunnel, i.e. you transport HTTP over it. This is due to the fact that SOCKS is a protocol that is designed to tunnel IP packets.

HTTP tunneling is using a protocol of higher level (HTTP) to transport a lower level protocol (TCP).

A VPN client on your computer establishes a secure tunnel with the VPN server, replacing your local ISP routing. VPN connections encrypt and secure all of your network traffic, not just the HTTP or SOCKS calls from your browser like a proxy server.

VPNs are great when you need to use the WIFI at a local coffee shop: using a VPN instead of the potentially completely unencrypted local WIFI adds another layer of privacy.

localhost and 127.0.0.1 are indeed different things.
