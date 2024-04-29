# Internet

The internet is a network of networks.

Technical Report Maturity Levels:

1. Working Draft - for review by the community
2. Candidate Recommendation - to gather implementation experience
3. Proposed Recommendation - for final endorsement
4. W3C Recommendation - recommends wide deployment
5. Later revisions - for producing a new edition

## IP - Internet Protocol

IP 地址是一个 32 位的二进制数，通常被分割为 4 个“8 位二进制数”（也就是 4 个字节）。IP 地址通常用“点分十进制”表示成（a.b.c.d）的形式，其中，a,b,c,d 都是 0~255 之间的十进制整数。

子网掩码与 IP 地址是组合使用的，IP 地址是计算机在网络内的唯一标识，而子网掩码是用于划分子网的。子网掩码与 IP 地址都是由 4 个数段组成，每个数段的取值范围是 0-255。

子网掩码由连续的 1 和 0 组成，连续的 1 表示网络地址，连续的 0 表示主机地址，通过 0 的个数可以计算出子网的容量（子网中主机的 IP 地址范围）。

比如 255.255.255.0，该子网掩码的二进制由 24 个 1 和 8 个 0 组成，8 个 0 表示该子网掩码划分出的子网容量为 256（2 的 8 次方），也就是说 192.168.1.0-255 都在同一个子网中，这 256 个地址中可用地址只有 254 个，因为规定每个子网的第一个 IP 地址为网段地址，最后一个 IP 地址为广播地址，都不可用。

IP 地址与子网掩码做“与”运算，得到的便是网络地址；IP 地址与取反后的子网掩码做“与”运算，得到的便是主机地址。

分类 | 特征 | 网络范围 | 主机地址范围 | 默认掩码
====|=======|==========|===========|============
A 类地址 | IP 地址以 0 开头 | 0-127.x.x.x | 从 1.0.0.0 到 126.255.255.255 | 255.0.0.0
B 类地址 | IP 地址以 10 开头 | 128-191.x.x.x | 从 128.0.0.0 到 191.255.255.255 | 255.255.0.0
C 类地址 | IP 地址以 110 开头 | 192-y.x.x.x | 从 192.0.0.0 到 223.255.255.255 | 255.255.255.0

## 网关(Gateway)

网关在网络层上实现网络互连，仅用于两个高层协议不同的网络互连。网关的结构也和路由器类似，不同的是互连层。网关既可以用于广域网互连，也可以用于局域网互连。

两台计算机要通讯，首先要判断是否处于同一个广播域内，即网络地址是否相同。如果网络地址相同，表示接受方在本网络上，那么可以把数据包直接发送到目标主机，否则就需要路由网关将数据包转发送到目的地。只有设置好网关的 IP 地址，TCP/IP 协议才能实现不同网络之间的相互通信。

## 统一资源标识符 (URL)

Uniform Resource Locator (URL) is a string of characters that specifies the location of a resource on the internet. It is used to identify a resource on the internet and is composed of several parts:

- Scheme: the protocol used to access the resource (e.g. http, https, ftp, etc.)
- Host: the domain name or IP address of the server where the resource is located
- Port: the port number on the server where the resource is located
- Path: the path to the resource on the server
- Query string: a set of parameters that can be passed to the server
- Fragment identifier: a portion of the document that is identified by the URL

```
URI = scheme ":" ["//" authority] path ["?" query] ["#" fragment]
authority = [userinfo "@"] host [":" port]
userinfo = username [":" password]
```
## NAT - Network Address Translation

A NAT works a bit like the post room in an office building - it receives all incoming mail directed to the building address and routes it to the individual recipients on their desks.

SNAT（源网络地址转换）实现没有公网 IP 的 ECS 实例借助有公网的 ECS 访问外网，但是外网无法访问到内网 IP；

DNAT（目的网络地址转换）实现外网通过端口映射访问到内网服务器，但是不能实现内网 ECS 访问到外网。

NAT-traversal technologies includes ICE, STUN, and TURN.

ICE - Interactive Connectivity Establishment
STUN - Session Traversal Utilities for NAT
TURN - Traversal Using Relays around NAT

STUN is a protocol that serves as a tool for other protocols in dealing with NAT. It can be used by an endpoint to determine the IP address and port allocated to it by a NAT, to perform connectivity checks between two endpoints, and as a keepalive protocol to maintain NAT bindings.

The TURN protocol is a specification allowing hosts behind NAT to control the operation of a relay server. The relay server allows hosts to exchange packets with its peers. The peers themselves may also be behind NATs.

WebRTC 1.0 - 2018-09-27 W3C Candidate Recommendation

[HTTP/3 explained](https://http3-explained.haxx.se/en/)

## DNS

Famiouse DNS servers:

- 1.0.0.1 CloudFlare
- 1.1.1.1 CloudFlare
- 8.8.8.8 Google
- 9.9.9.9 IBM
- x.x.x.x.xip.io Basecamp 内网 IP 解析

`1.0.0.1` abbreviates to `1.1`, so you can literally test by typing `ping 1.1`.

## 端口号

List of restricted ports on Chrome:

      1,    // tcpmux
      7,    // echo
      9,    // discard
      11,   // systat
      13,   // daytime
      15,   // netstat
      17,   // qotd
      19,   // chargen
      20,   // ftp data
      21,   // ftp access
      22,   // ssh
      23,   // telnet
      25,   // smtp
      37,   // time
      42,   // name
      43,   // nicname
      53,   // domain
      77,   // priv-rjs
      79,   // finger
      87,   // ttylink
      95,   // supdup
      101,  // hostriame
      102,  // iso-tsap
      103,  // gppitnp
      104,  // acr-nema
      109,  // pop2
      110,  // pop3
      111,  // sunrpc
      113,  // auth
      115,  // sftp
      117,  // uucp-path
      119,  // nntp
      123,  // NTP
      135,  // loc-srv /epmap
      139,  // netbios
      143,  // imap2
      179,  // BGP
      389,  // ldap
      465,  // smtp+ssl
      512,  // print / exec
      513,  // login
      514,  // shell
      515,  // printer
      526,  // tempo
      530,  // courier
      531,  // chat
      532,  // netnews
      540,  // uucp
      556,  // remotefs
      563,  // nntp+ssl
      587,  // stmp?
      601,  // ??
      636,  // ldap+ssl
      993,  // ldap+ssl
      995,  // pop3+ssl
      2049, // nfs
      3659, // apple-sasl / PasswordServer
      4045, // lockd
      6000, // X11
      6665, // Alternate IRC [Apple addition]
      6666, // Alternate IRC [Apple addition]
      6667, // Standard IRC [Apple addition]
      6668, // Alternate IRC [Apple addition]
      6669, // Alternate IRC [Apple addition]

## QUIC

The plan was to ship the final specification for QUIC version 1 in November 2018; this was later postponed to July 2019.

![network stack](https://http3-explained.haxx.se/images/quic-stack.png)

The IETF QUIC protocol is a transport protocol, on top of which other application protocols can be used. The initial application layer protocol is HTTP/3.

The work on sending protocols other than HTTP over QUIC has been postponed until after QUIC version 1 has shipped.

UDP is not a reliable transport, QUIC adds a layer on top of UDP that introduces reliability. It offers re-transmissions of packets, congestion control, pacing and the other features otherwise present in TCP.

- Multiple streams

A QUIC connection is made to a UDP port and IP address, but once established the connection is associated by its "connection ID". Over an established connection, either side can create streams and send data to the other end.

QUIC guarantees in-order delivery of streams, but not between streams. Streams are delivered in-order, but different streams may be delivered out-of-order. A lost packet only affects the stream to which the lost packet belongs.

QUIC separates logical streams within the physical connections. A number of parallel streams that can transfer data simultaneously over a single connection without affecting the other streams.

QUIC offers flow control on both connection and streams.

- Fast handshakes

QUIC offers both 0-RTT and 1-RTT connection setups, meaning that at best QUIC needs no extra round-trips at all when setting up a new connection. The faster of those two, the 0-RTT handshake, only works if there has been a previous connection established to a host and a secret from that connection has been cached.

- Early data

QUIC allows a client to include data already in the 0-RTT handshake. This feature allows a client to deliver data to the peer as fast as it possibly can, and that then of course allows the server to respond and send data back even sooner.

- Transport security

The transport security used in QUIC is using TLS 1.3 (RFC 8446) and there are never any unencrypted QUIC connections.
