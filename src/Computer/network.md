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
