# JWT - JSON Web Tokens

## JWT 的优点

- 体积小，因而传输速度快

- 传输方式多样，可以通过 URL/POST 参数/HTTP 头部等方式传输

- 严格的结构化。它自身（在 payload 中）就包含了所有与用户相关的验证消息，如用户可访问路由、访问有效期等信息，服务器无需再去连接数据库验证信息的有效性，并且 payload 支持为你的应用而定制化。

- 支持跨域验证，可以应用于分布式站点的单点登录。

## JWT 的组成

一个 JWT 实际上就是一个字符串，它由三部分组成，头部（Header）、载荷（Payload）与签名(Signature)。

JWT 中常用的签名算法是 HS256，header 和 payload 必须进行 base64 编码。Payload 消息体是透明的，不能够携带敏感数据如密码等信息，使用签名可以保证消息不被篡改。

把 token 想象成一个安全的令牌。你在一个安全的前台验证你的身份（通过你的用户名和密码），如果你成功验证了自己，你就可以取得这个。当你走进大楼的时候（试图从调用 API 获取资源），你会被要求验证你的令牌，而不是在前台重新验证。基于令牌的身份验证是无状态的，所以不需要再回话中保存用户信息。这使我们可以扩展系统而不用担心用户是在哪儿登录的。我们可以从不止一个我们登录了域获取安全资源，而只使用一个相同的令牌。

登录验证和持有令牌的消息使用 HTTPS 安全通道，其他的数据传输可使用 HTTP 快速通道。用户退出登录时删除客户端的令牌。

方式 1：密钥只保存于服务器端，payload 中包含过期时间。
如果用户成功验证账号和密码，然后服务端生成一个 token，返回给用户。token 中的 payload 可以是加密过的信息。
用户获取到 token 后，应该在每次向服务器请求数据时附带这个 token，然后服务端验证 token。

方式 2：用户登录验证后，生成一个随机的密钥，客户端和服务器各保存一份。
客户端可以在 payload 中加入全部的请求参数，token 在客户端生成。服务端验证 token，可确保请求参数没有被篡改。

方式 3：用户登录验证后，将公钥保存到服务器上。
客户端用私钥生成 token，服务器端用公钥验证 token。

![示例](https://i.imgur.com/rYWf4tn.png)

### Token 过期前的回收方法

1. 每个用户都使用独立的私钥对 token 签名，私钥可以动态生成的或者是用户密码的哈希值，当清空和修改用户的秘钥后，所有该用户的 token 都会失效。
2. 在服务器 Redis 中存放 token 的 id，然后删除 id 让对应的 token 失效。

### 同一时间只允许一个用户设备登录

1. 用户每次登录生成新的 token 后，让之前发放的 token 失效。
2. 比对 token 发放的时间和用户最后一次登录的时间。
3. 设置 token 的过期时间，比如两个小时，token 过期后生成一个新的 token 给客户端，如果有多个端同时登录，其中只有一个端获得的新 token 是有效的。

JWE：JSON Web Encryption

可使用 AES 算法加密 token 内容。

传统的 Session-Cookie 方式会有几点问题：

1. 频繁查找 Session 的开销过大。因为 Session 存储在服务端，大部分接口的请求都需要查找 Session 以获取对应用户身份。不管是存储在持久层（数据库）还是内存中，频繁查找带来的压力会随着用户量的上升而急剧增大。

2. 不支持跨域，可扩展性差。举个例子：假设网站 A 和网站 B 的用户数据是共享的，当用户在网站 A 上登录以后，我们希望在访问网站 B 时也保持登录状态。这个时候就会出现一个情况：生成这个 SessionID 的服务器并不是验证这个 SessionID 的服务器，也就出现了跨域身份认证的问题。除非我们把身份认证的数据也共享，即将 Session 放在持久层单独存储，统一管理，这样就能在多域名下共享了，但是这样做的成本有点高。

3. 安全性较差。Session 放在 Cookie 中容易被 CSRF 攻击，而且在多域名的业务场景下需要额外的做兼容性处理，容易出现安全漏洞。

JWT 的缺点:

1. 数据臃肿
   因为 payload 只是用 Base64 编码，所以一旦存放数据大了，编码之后 JWT 会很长，每次 HTTP 请求都带上这个臃肿的 Header 开销也随之变大。

2. 无法废弃和续签

- 如果有效期设置过长，意味着这个 Token 泄漏后可以被长期利用，危害较大，所以一般我们都会设置一个较短的有效期。由于有效期较短，意味着需要经常进行重新授权的操作。

- 假设在用户操作过程中升级 / 变更了某些权限，势必需要刷新以更新数据。要解决这个问题，需要在服务端部署额外逻辑，常见的做法是增加刷新机制和黑名单机制，通过 Refresh Token 刷新 JWT，将需要废弃的 Token 加入到黑名单。

使用 JWT 的注意事项：

1. 因为 JWT 的前两个部分仅是做了 Base64 编码处理并非加密，所以在存放数据上不能存放敏感数据。

2. 用来签名 / 加密的密钥需要妥善保存。

3. 尽可能采用 HTTPS，确保不被窃听。

4. 如果存放在 Cookie 中则强烈建议开启 Http Only，其实官方推荐是放在 LocalStorage 里，然后通过 Header 头进行传递。

- Stateless Token: Contains all the session data inside the token. This way you don't need to store it anywhere.
- Steteful Token: Contains a session id. When the server receives the token he will need to retrieve the information about the session.

## refresh token

refresh token 是 OAuth2 认证中的一个概念，和 OAuth2 的 access token 一起生成，表示更新令牌，过期所需时间比 access toen 要长，可以用来获取下一次的 access token。

如果 JWT 需要添加 refresh token 支持，refresh token 需要满足的条件有一下几项：

1. 和 JWT 一起生成返回给客户端

2. 有实效时间，有效时间比 JWT 要长

3. 只能用来换取下一次 JWT，不能用于访问认证

4. 不能重复使用（可选）
