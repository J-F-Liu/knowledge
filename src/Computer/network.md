### 集线器（Hub）

集线器工作在物理层，属于 1 层设备，内部采用了总线型拓扑，采用了广播的方式，每发送一个数据所有的端口均可以收到。
无论哪个端口收到数据之后，都要广播到所有的端口，因此网络性能受到很大的限制。
在同一时间内必须是单向的，只能维持在半双工模式下，两个端口不能同时收发数据，并且当两个端口通信时，其他端口不能工作。

集线器主要用于共享网络的组建，它处于网络的一个星型结点，对连接在该结点的设备进行集中管理。

### 网桥（Network Bridge）

网桥，又称桥接器，工作在数据链路层，能从发来的数据包中提取 MAC 信息，并且根据 MAC 信息对数据包进行有目的的转发，而不采用广播的方式。
网桥有 2 个端口，分别连接两个集线器，用来沟通两个子网。把一个局域网一分为 2，中间用网桥连接，减少广播风暴的出现，提高网络的效率。
网桥的转发表是一对多的 (一个端口号对多个 MAC 地址)。

### 交换机（Switch）

交换机工作在数据链路层，属于 2 层设备，每个端口形成一张 MAC 地址转发表，根据数据包的 MAC 地址转发到对应的端口，而不是广播到所有的端口。
当交换机上的两个端口通信时，它们之间的通道是相互独立的，可以实现全双工通信，两个端口同时收发数据。
交换机的转发表是一对一的。如果转发表中没有找到和数据包的目的 MAC 地址对应的记录，交换机会对此数据包进行广播，发给本交换机的每一个端口。
交换机基于收到的源 MAC 地址来进行学习，放进转发表。从不同接口学到同一个 MAC 地址，则用后学到的覆盖先学到的，不是一个主机地址对应多个交换机端口。

网桥和交换机都有一定量的缓存，当网桥或交换机处理不及并且缓存用完了，以后再来的数据还是会丢失的。
当多台设备使用同一个交换机时，交换机可以实现负载均衡和带宽控制的功能。通过智能路由和流量控制，可以为不同设备提供不同的网络带宽和速度，从而达到更加高效的数据传输。
交换机主要是实现通过一根网线上网，但大家上网是分开拨号的，也就是用自己的宽带，不管如何下载，相互之间的网络是没有影响的。

相比于集线器，交换机的应用场景更广泛，其已逐渐替代集线器。

### 路由器 (Router)

路由器工作在 OSI 模型的网络层，提供异种网互连能力，连接对象包括局域网和广域网。
路由器的功能分为三部分，第一部分是网关，它就像一道闸门一样，控制着下行网络，不同网段之间通信，需要网关的帮助；第二部分是扩展有线网络端口；第三部分是无线接入点（AP），用于组建 WiFi 网络。
虽然有些交换机带有 AP，但实际上起到的依然是交换机的作用。
路由器就比交换机多了一个虚拟拨号功能，一样是通过一根网线上网，但是是共用一个宽带账号，不同设备都会相互影响网络。

MAC 地址通常是硬件自带的，由网卡生产商来分配的，而且已经固化到了网卡中去，一般来说是不可更改的。
IP 地址是在软件中实现的，描述的是设备所在的网络，由网络管理员或系统自动分配，也称为协议地址或者网络地址。
路由器可以给接入的设备分配 IP，根据 IP 地址来确定数据包转发的地址。

交换机分割冲突域，但是不分割广播域，而路由器分割广播域，广播数据不会穿过路由器。
路由器也可以当普通交换机使用，具备的线路连通的功能。
路由功能更多的体现在不同类型网络之间的互联上，如局域网与广域网之间的连接、不同协议的网络之间的连接等，所以路由器主要是用于不同类型的网络之间。
路由器一般都有防火墙的功能，能够对一些网络数据包选择性过滤。

### 中继器

由于长距离的传输，信号会有一定的损耗，中继器的作用是把物理层传输的信号放大。

### POE 供电 (Power Over Ethernet)

在现有的以太网 Cat.5 布线基础架构不作任何改动的情况下，在为一些基于 IP 的终端（如 IP 电话机、无线局域网接入点 AP、网络摄像机等）传输数据信号的同时，还能为此类设备提供直流供电的技术。
2003 年 6 月，IEEE 批准了 IEEE 802.3af (15.4W)，是首个 PoE 供电标准。IEEE802.3at (25.5W)在兼容 802.3af 的基础上，提供更大的供电功率，扩展到 25W 或更高。

区分标准 PoE 和非标准 PoE 只需用万用表测量。方法如下： 
启动设备，将万用电表调至电压测量档位，用万用电表两表笔分别点触 PSE 设备供电脚（通常是 RJ45 端口的 1/2,3/6 或者 4/5,7/8），如果测出有 48V 或其它电压值（12V、24V 等）稳定输出的设备即是非标产品。因为在这个过程中，PSE 不对受电设备（这里为万用表）做检测，直接采用 48V 或其它电压值供电。 
反之，如果测量不出电压，万用表表针在 2~10V 之间跳动，则为标准 POE。因为在这个阶段，PSE 在对 PD 端（这里为万用表）进行检测，而万用电表不是合法的 PD，PSE 不会供电，无稳定电压产生。

ICT: Information and Communication Technology

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

## Remote Access

There are three main ways to access your Raspberry Pi remotely over the internet:

SSH - Secure Shell, a cryptographic network protocol for secure remote access to devices over an unsecured network such as the internet.

VNC - Virtual Network Computing, a protocol for safely accessing the Raspberry Pi GUI or desktop.

RDP - Remote Desktop Protocol, a proprietary protocol developed by Microsoft that provides a user with a graphical interface to connect to another computer over a network connection.

All of these methods usually require port forwarding.
[Pinggy](https://Pinggy.io) is a tunneling tool that gives a public address to access your localhost, even while sitting behind a NAT or a firewall.
[]