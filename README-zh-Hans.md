*[English](README.md) ∙ [简体中文](README-zh-Hans.md)*

# 系统设计课程

欢迎来到这门课。我希望这门课程提供了一个很好的学习经验。

_这门课也可以在这里看到： [website](https://karanpratapsingh.com/courses/system-design) 以及 [leanpub](https://leanpub.com/systemdesign). 请不要吝惜你的小⭐⭐!_

# 目录

- **序**

  - [什么是系统设计?](#什么是系统设计)

- **第一章**

  - [IP](#ip)
  - [OSI 网络模型](#OSI网络模型)
  - [TCP 和 UDP](#TCP和UDP)
  - [DNS](#DNS)
  - [负载均衡](#负载均衡)
  - [集群](#集群)
  - [CDN](#content-delivery-network-cdn)
  - [缓存](#缓存)
  - [代理](#代理)
  - [可用性](#可用性)
  - [可伸缩性](#可伸缩性)
  - [存储](#存储)

- **第二章**

  - [数据库与DBMS](#数据库与DBMS)
  - [关系型数据库](#关系型数据库)
  - [非关系型数据库](#非关系型数据库)
  - [关系 vs 非关系 数据库](#关系vs非关系数据库)
  - [Database Replication](#database-replication)
  - [Indexes](#indexes)
  - [Normalization and Denormalization](#normalization-and-denormalization)
  - [ACID and BASE consistency models](#acid-and-base-consistency-models)
  - [CAP theorem](#cap-theorem)
  - [PACELC Theorem](#pacelc-theorem)
  - [Transactions](#transactions)
  - [Distributed Transactions](#distributed-transactions)
  - [Sharding](#sharding)
  - [Consistent Hashing](#consistent-hashing)
  - [Database Federation](#database-federation)

- **第三章**

  - [N-tier architecture](#n-tier-architecture)
  - [Message Brokers](#message-brokers)
  - [Message Queues](#message-queues)
  - [Publish-Subscribe](#publish-subscribe)
  - [Enterprise Service Bus (ESB)](#enterprise-service-bus-esb)
  - [Monoliths and Microservices](#monoliths-and-microservices)
  - [Event-Driven Architecture (EDA)](#event-driven-architecture-eda)
  - [Event Sourcing](#event-sourcing)
  - [Command and Query Responsibility Segregation (CQRS)](#command-and-query-responsibility-segregation-cqrs)
  - [API Gateway](#api-gateway)
  - [REST, GraphQL, gRPC](#rest-graphql-grpc)
  - [Long polling, WebSockets, Server-Sent Events (SSE)](#long-polling-websockets-server-sent-events-sse)

- **第四章**

  - [Geohashing and Quadtrees](#geohashing-and-quadtrees)
  - [Circuit breaker](#circuit-breaker)
  - [Rate Limiting](#rate-limiting)
  - [Service Discovery](#service-discovery)
  - [SLA, SLO, SLI](#sla-slo-sli)
  - [Disaster recovery](#disaster-recovery)
  - [Virtual Machines (VMs) and Containers](#virtual-machines-vms-and-containers)
  - [OAuth 2.0 and OpenID Connect (OIDC)](#oauth-20-and-openid-connect-oidc)
  - [Single Sign-On (SSO)](#single-sign-on-sso)
  - [SSL, TLS, mTLS](#ssl-tls-mtls)

- **第五章**

  - [System Design Interviews](#system-design-interviews)
  - [URL Shortener](#url-shortener)
  - [WhatsApp](#whatsapp)
  - [Twitter](#twitter)
  - [Netflix](#netflix)
  - [Uber](#uber)

- **附录**

  - [Next Steps](#next-steps)
  - [References](#references)

# 什么是系统设计?

在我们开始之前，让我们谈谈什么是系统设计。

系统设计是为满足特定需求的系统定义体系结构、接口和数据的过程。系统设计通过连贯和高效的系统满足您的业务或组织的需求。它需要一个系统的方法来构建和工程系统。一个好的系统设计需要我们考虑一切，从基础设施一直到数据和数据的存储方式。

## 为什么系统设计很重要？

系统设计帮助我们定义满足业务需求的解决方案。这是我们在构建系统时可以做出的最早的决定之一。通常情况下，从高层次的角度进行思考是非常必要的，因为这些决定以后很难纠正。随着系统的发展，它还使推断和管理体系结构更改变得更容易。

# IP

IP地址是在internet或本地网络上标识设备的唯一地址。IP是“互联网协议”的缩写，它是一套管理通过互联网或本地网络发送的数据格式的规则。

本质上，IP地址是允许信息在网络上的设备之间发送的标识符。它们包含位置信息，并使设备易于通信。互联网需要一种方法来区分不同的计算机、路由器和网站。IP地址提供了一种这样做的方式，并形成了互联网如何工作的一个重要部分。

## 版本

现在，让我们来了解一下IP地址的不同版本:

### IPv4

最初的互联网协议是IPv4，它使用32位数字点十进制表示法，只允许大约40亿个IP地址。最初，这已经足够了，但随着互联网普及率的增长，我们需要更好的东西。

*例如:102.22.192.181*

### IPv6

IPv6是1998年引入的一种新协议。自2000年代中期开始部署以来，互联网用户呈指数级增长，目前仍在进行中。

这个新协议使用128位字母数字十六进制表示法。这意味着IPv6可以提供大约340e+36个IP地址。这足以满足未来几年不断增长的需求。

*例如:2001:0db8:85a3:0000:0000:8a2e: 0370:7334*

## 类型

让我们来讨论一下IP地址的类型:

### Public (公网IP)

公网IP地址是一个主地址，与整个网络相关联的地址。在这种类型的IP地址中，每一个连接的设备都有相同的IP地址。

*例如:ISP提供给路由器的IP地址。*

### Private

私有IP地址是分配给每一个连接到你的互联网网络的设备的唯一IP号码，包括在你家里使用的电脑、平板电脑和智能手机等设备。

*例如:由您的家庭路由器为您的设备生成的IP地址。*

### Static（静态的）

静态IP地址不会改变，它是手动创建的，而不是被分配的。这些地址通常更贵，但更可靠。

*示例:它们通常用于重要的事情，如可靠的地理位置服务，远程访问，服务器托管等。*

### Dynamic（动态）

动态IP地址会随时变化，并不总是相同的。它是由DHCP服务器分配的。动态IP地址是最常见的互联网协议地址类型。它们的部署成本更低，并且允许我们根据需要在网络中重用IP地址。

它们更常用于消费设备和个人使用。

# OSI网络模型

OSI模型是一个逻辑和概念模型，它定义了开放系统使用的网络通信方式，以便与其他系统互连和通信。开放系统互连(OSI模型)也定义了一个逻辑网络，并通过使用不同的协议层有效地描述了计算机数据包的传输。

OSI模型可以看作是计算机网络的通用语言。它基于将一个通信系统分成七个抽象层的概念，每一层都堆叠在最后一层之上。

## 为什么 OSI 模型很重要？

开放系统互连(OSI)模型定义了在网络讨论和文档中使用的常用术语。这使得我们可以将一个非常复杂的通信过程分离开来，并对其组成部分进行评估。

虽然这个模型没有在今天最常见的TCP/IP网络中直接实现，但它仍然可以帮助我们做很多的事情，例如:

- 使故障排除更容易，并帮助识别整个堆栈中的威胁。
- 鼓励硬件制造商创建可以通过网络相互通信的网络产品。
- 这对培养安全第一的心态至关重要。
- 把一个复杂的功能分解成更简单的组件。

## 层次

OSI模型的七个抽象层可以从上到下定义如下:

![osi-model](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/osi-model/osi-model.png)

### Application 应用层

这是唯一直接与来自用户的数据交互的层。像网页浏览器和电子邮件客户端这样的软件应用程序依赖于应用层来发起通信。但是应该明确的是，客户端软件应用程序不是应用层的一部分，而是应用层负责协议和数据操作，软件依赖这些协议和数据操作来向用户显示有意义的数据。应用层协议包括HTTP和SMTP等。

### ****Presentation 表示层****

表示层也称为翻译层。来自应用层的数据在这里被提取并按照所需的格式进行操作，以便通过网络传输。表示层的功能是翻译、加密/解密和压缩。

### Session 会话层

这一层负责打开和关闭两个设备之间的通信。通信打开和关闭之间的时间称为会话。会话层确保会话保持打开的时间足够长，以传输正在交换的所有数据，然后迅速关闭会话，以避免浪费资源。会话层还与检查点同步数据传输。

### Transport 传输层

传输层(也称为第4层)负责两个设备之间的端到端通信。这包括从会话层获取数据，并在将其发送到网络层(第三层)之前将其分解为称为段的块。它还负责将接收设备上的段重新组合为会话层可以使用的数据。

### Network 网络层

网络层负责促进两个不同网络之间的数据传输。网络层在发送方设备上将传输层的段分解成更小的单元，称为包，并在接收方设备上将这些包重新组合。网络层还为数据找到到达目的地的最佳物理路径，这被称为路由。如果通信的两个设备在同一个网络上，则不需要网络层。

### Data Link 数据链路层

数据链路层与网络层非常相似，不同之处在于数据链路层方便同一网络上两台设备之间的数据传输。数据链路层从网络层接收数据包，并将它们分成称为帧的更小的片段。

### Physical 物理层

这一层包括涉及数据传输的物理设备，如电缆和交换机。这也是将数据转换为位流的层，位流是由1和0组成的字符串。两个设备的物理层还必须在一个信号约定上达成一致，以便两个设备上的1可以与0区分开来。

# TCP和UDP

## TCP

传输控制协议(TCP)是面向连接的，这意味着一旦建立了连接，数据就可以双向传输。TCP有内置的系统来检查错误，并确保数据按照发送的顺序发送，这使它成为传输静态图像、数据文件和网页等信息的完美协议。

![tcp](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/tcp-and-udp/tcp.png)

但是，虽然TCP天生可靠，但它的反馈机制也会导致更大的开销，转化为对网络上可用带宽的更多使用。

## UDP

用户数据报协议(UDP)是一种更简单、无连接的互联网协议，不需要错误检查和恢复服务。使用UDP，没有打开连接、维护连接或终止连接的开销。无论接收方是否收到数据，数据都会不断地发送到接收方。

![udp](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/tcp-and-udp/udp.png)

它主要用于实时通信，如广播或多播网络传输。当我们需要最低的延迟和数据延迟比数据丢失更糟糕时，我们应该使用UDP而不是TCP。

## TCP vs UDP

TCP是面向连接的协议，而UDP是无连接的协议。TCP和UDP之间的一个关键区别是速度，因为TCP比UDP相对慢。总的来说，UDP是一种更快、更简单、更有效的协议，然而，丢失数据包的重传只有TCP才可能实现。

TCP提供从用户到服务器的有序数据传输(反之亦然)，而UDP不专门用于端到端通信，也不检查接收方的准备情况。

| 功能 | TCP | UDP |
| --- | --- | --- |
| 连接 | 需要建立连接 | 无连接协议 |
| 保证传输 | 可以保证数据传输 | 无法确保数据传输 |
| 重传 | 丢失的数据包可以重新传输 | 不能重传丢失的数据包 |
| 速度/效率 | 比 UDP 慢 | 比 TCP 快 |
| 广播 | 不支持广播 | 支持广播 |
| 使用场景 | HTTPS,HTTP,SMTP,POP,FTP等 | 流媒体视频,DNS，网络电话等 |

# DNS

前面我们学习了使每台机器与其他机器连接的IP地址。但我们知道，人类对名字比数字更熟悉。像google.com这样的名字比122.250.192.232这样的名字更容易记住。

这就引出了域名系统(DNS)，它是一种分层和分散的命名系统，用于将人类可读的域名转换为IP地址。

## NDS 如何工作

![how-dns-works](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/domain-name-system/how-dns-works.png)

DNS 查找目标包括以下八个步骤:

1. 客户端在浏览器输入 example.com，查询就会传到互联网上，并被DNS解析器接收。
2. 然后，解析器递归地查询DNS根名称服务器。
3. 根服务器用顶级域(TLD)的地址响应解析器。
4. 然后解析器向 `.com` TLD发出请求。
5. 然后 TLD 服务器返回域名服务器的 IP 地址 example.com。
6. 最后，递归解析器向域的名称服务器发送一个查询。
7. [example.com](http://example.com) 的IP地址然后从名称服务器返回给解析器。
8. 然后，DNS解析器用最初请求的域的IP地址响应web浏览器。

一旦IP地址被解析，客户端应该能够从解析的IP地址请求内容。例如，解析的IP可能返回要在浏览器中呈现的网页。

## Server 种类

现在，让我们看看组成DNS基础结构的四组关键服务器。

### DNS Resolver

DNS解析器(也称为DNS递归解析器)是DNS查询中的第一站。递归解析器充当客户端和DNS名称服务器之间的中间人。从web客户端接收到DNS查询后，递归解析器要么响应缓存的数据，要么向根名称服务器发送请求，然后向TLD名称服务器发送另一个请求，最后向Authoritative名称服务器发送最后一个请求。在从Authoritative名称服务器接收到包含所请求IP地址的响应后，递归解析器然后向客户端发送响应。

### DNS root server

根服务器接受递归解析器的查询，其中包含一个域名，根命名服务器根据该域的扩展名(.com， .net， .org等)将递归解析器导向TLD命名服务器进行响应。根域名服务器由一家名为“互联网名称与数字地址分配机构”(ICANN)的非营利性机构监管。

每个递归解析器都知道13个DNS根名称服务器。注意，虽然有13个根名称服务器，但这并不意味着根名称服务器系统中只有13台机器。有13种类型的根名称服务器，但每一种服务器在世界各地都有多个副本，它们使用Anycast路由来提供快速响应。

### TLD nameserver

TLD命名服务器维护共享一个公共域扩展名的所有域名的信息，例如 .com、.net或URL中最后一个点后面的任何域名。

TLD名称服务器的管理由互联网编号分配机构(IANA)负责，它是ICANN的一个分支。IANA将TLD服务器分为两组:

- 通用顶级域名:这类域名包括 `.com`，`.org`，`.net`，`.edu`和 `.gov`。
- 国家代码顶级域:这些域包括特定于一个国家或州的任何域。例如 `.cn` 、`.uk`、`.us`、`.ru` 和 `.jp`。

### Authoritative DNS server

Authoritative 名称服务器通常是解析器在获取IP地址过程中的最后一步。该命名服务器包含特定于所服务的域名信息([例如google.com](http://xn--google-9v9ii49d.com/)),它可以提供一个递归解析器的IP地址,服务器的DNS记录,或如果域有一个CNAME记录(别名),它将为递归解析器提供一个别名域,此时递归解析器必须执行一个全新的DNS查询采购记录从一个权威的命名服务器(通常是一个包含一个IP地址的记录)。如果找不到域，则返回NXDOMAIN消息。

## 查询种类

在DNS系统中有三种类型的查询:

### 递归（Recursive）

在递归查询中，DNS客户端要求DNS服务器(通常是DNS递归解析器)用请求的资源记录或错误消息响应客户端，如果解析器找不到记录的话。

### 迭代（Iterative）

在迭代查询中，DNS客户端提供主机名，DNS解析器返回它所能返回的最佳答案。如果DNS解析器的缓存中有相关的DNS记录，它将返回它们。如果不是，它将DNS客户端引用到根服务器或另一个最接近所需DNS区域的Authoritative名称服务器。然后，DNS客户端必须直接对引用它的DNS服务器重复查询。

### 非递归（Non-recursive）

非递归查询是DNS解析器已经知道答案的查询。它要么立即返回DNS记录，因为它已经将其存储在本地缓存中，要么查询DNS Name Server，这是记录的权威，这意味着它肯定持有该主机名的正确IP。在这两种情况下，都不需要额外的查询(如递归查询或迭代查询)。相反，响应会立即返回给客户机。

## Record 种类

DNS记录(又名区域文件)是存在于 authoritative DNS服务器中的指令，提供有关域的信息，包括与该域关联的IP地址以及如何处理该域的请求。

这些记录由一系列用DNS语法编写的文本文件组成。DNS语法只是一个字符串，用作命令，告诉DNS服务器要做什么。所有DNS记录都有一个“TTL”，它代表生存时间，并指示DNS服务器刷新该记录的频率。

还有更多的记录类型，但现在，让我们看看一些最常用的记录类型:

- A(地址记录):这是保存一个域的IP地址的记录。
- AAAA (IPV6地址记录):包含一个域的IPv6地址的记录(与a记录相反，它存储IPv4地址)
- CNAME(规范名称记录):转发一个域或子域到另一个域，不提供IP地址。
- MX(邮件交换记录):将邮件定向到电子邮件服务器。
- TXT(文本记录):该记录允许管理员在记录中存储文本注释。这些记录通常用于电子邮件安全。
- NS(名称服务器记录):存储DNS表项的名称服务器。
- SOA(起始授权):存储关于域的管理信息。
- SRV(服务位置记录):为特定的服务指定端口。
- PTR(反向查找指针记录):在反向查找中提供域名。
- CERT(证书记录):存储公钥证书。

## 子域

子域名是主域名的附加部分。它通常用于在逻辑上将一个网站划分为多个部分。我们可以在主域中创建多个子域。

例如，[blog.example.com](http://blog.example.com/)，其中blog是子域，example是主域，.com是顶级域(TLD)。[类似的例子可以登录support.example.com或careers.example.com](http://xn--support-hc5khz5xw88awrvj4ln42fzda157h.example.xn--comcareers-ul8t.example.com/)。

## DNS 区域

DNS区域是域命名空间的一个独立部分，委托给负责维护DNS区域的个人、组织或公司等法人实体。DNS区域也是一种管理功能，允许对DNS组件(如authoritative名称服务器)进行细粒度控制。

## DNS 缓存

DNS缓存(有时称为DNS解析器缓存)是一种临时数据库，由计算机的操作系统维护，包含所有最近访问和试图访问网站和其他互联网域的记录。换句话说，DNS缓存只是最近DNS查找的一个记忆，当我们的计算机试图弄清楚如何加载一个网站时，它可以快速引用它。

域名系统在每个DNS记录上实现生存时间(TTL)。TTL指定记录可以被DNS客户端或服务器缓存的秒数。当记录存储在缓存中时，它所附带的TTL值也会被存储。服务器继续更新缓存中存储的记录的TTL，每秒钟倒数一次。当它为0时，记录将从缓存中删除或清除。这时，如果收到对该记录的查询，DNS服务器必须启动解析过程。

## 反向DNS

反向DNS查找是对与给定IP地址相关联的域名的DNS查询。这与更常用的正向DNS查找相反，后者查询DNS系统以返回IP地址。反向解析IP地址的过程使用PTR记录。如果服务器没有PTR记录，则无法解析反向查找。

反向查找通常用于电子邮件服务器。电子邮件服务器检查邮件是否来自有效的服务器，然后将其引入其网络。许多电子邮件服务器将拒绝来自任何不支持反向查找的服务器或来自不太可能是合法的服务器的邮件。

注:反向DNS查找并没有被普遍采用，因为它们对互联网的正常功能不是至关重要的。

## 举例

以下是一些广泛使用的托管DNS解决方案:

[https://aws.amazon.com/route53](https://aws.amazon.com/route53)

[https://www.cloudflare.com/dns](https://www.cloudflare.com/dns)

[https://cloud.google.com/dns](https://cloud.google.com/dns)
[https://azure.microsoft.com/en-in/services/dns](https://azure.microsoft.com/en-in/services/dns)
[https://ns1.com/products/managed-dns](https://ns1.com/products/managed-dns)

# 负载均衡

负载均衡使我们能够将传入的网络流量分布到多个资源上，通过只向在线的资源发送请求来确保高可用性和可靠性。这提供了根据需求增加或减少资源的灵活性。

![load-balancing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/load-balancer.png)

为了获得额外的可伸缩性和冗余，我们可以尝试在系统的每一层实现负载均衡:

![load-balancing-layers](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/load-balancer-layers.png)

## 为什么？

现代的高流量网站必须服务几十万，甚至几百万来自用户或客户端的并发请求。为了经济有效地扩展以满足这些高容量，现代计算最佳实践通常需要添加更多的服务器。

负载均衡器可以位于服务器前面，并在所有能够满足这些请求的服务器之间路由客户端请求，这种方式可以最大限度地提高速度和容量利用率。这确保了没有单个服务器过度工作，否则会降低性能。如果有一台服务器宕机，负载均衡器会将流量重定向到其他在线服务器。当一个新服务器被添加到服务器组中时，负载均衡器自动开始向它发送请求。

## 工作负载分布

这是负载均衡器提供的核心功能，有几种常见的变化:

- 基于主机:基于请求的主机名分发请求。
- 基于路径:使用整个URL分发请求，而不是只使用主机名。
- 基于内容:检查请求的消息内容。这允许基于参数值等内容进行分发。

## 层

一般来说，负载均衡器工作在以下两个层次之一:

### 网络层

这是在网络传输层(也称为第4层)工作的负载均衡器。它根据IP地址等网络信息执行路由，而不能执行基于内容的路由。这些通常是可以高速运行的专用硬件设备。

### 应用层

这是在应用层(也称为第7层)上运行的负载均衡器。负载均衡器可以完整地读取请求并执行基于内容的路由。这允许在充分理解流量的基础上管理负载。

## 种类

让我们看看不同类型的负载均衡器:

### 软负载

软件负载均衡器通常比硬件版本更容易部署。它们也倾向于更具成本效益和灵活性，并且它们与软件开发环境一起使用。软件方法为我们提供了根据环境的特定需求配置负载均衡器的灵活性。灵活性的提高可能以必须做更多的工作来设置负载平衡器为代价。与硬件版本相比，软件平衡器提供了更多的封闭盒方法，让我们可以更自由地进行更改和升级。

软件负载均衡器被广泛使用，可以作为需要配置和管理的可安装解决方案，也可以作为托管云服务。

### 硬件负载

顾名思义，硬件负载均衡器依赖于物理的内部硬件来分配应用程序和网络流量。这些设备可以处理大量的流量，但通常价格高昂，在灵活性方面也相当有限。

硬件负载均衡器包括需要作为新版本进行维护和更新的专有固件，以及发布的安全补丁。

### DNS

DNS负载均衡是在域名系统(DNS)中配置一个域的实践，以便跨一组服务器计算机分布对该域的客户机请求。

不幸的是，DNS负载均衡存在固有的问题，限制了其可靠性和效率。最重要的是，DNS不检查服务器和网络中断或错误。它总是为一个域返回相同的IP地址集，即使服务器关闭或无法访问。

## 路由算法

现在，我们来讨论一下常用的路由算法:

- **轮询:**将请求轮流分发到应用服务器。
- **加权轮询:**基于简单轮询技术，使用管理员可以通过DNS记录分配的权重来考虑不同的服务器特征，如计算和流量处理能力。
- **最少连接:**新请求被发送到与客户端的当前连接最少的服务器。考虑每个服务器的相对计算能力，确定哪一个服务器的连接最少。
- **最小响应时间:**将请求发送到根据结合最快响应时间和最少活动连接的公式所选择的服务器。
- **最小带宽:**该方法以每秒兆比特(Mbps)为单位度量流量，将客户端请求发送到流量最小Mbps的服务器。
- **哈希:**基于我们定义的键分发请求，例如客户端IP地址或请求URL。

## 优势

负载均衡在防止停机方面也起着关键作用，负载均衡的其他优点包括:

- 可伸缩性
- 冗余
- 灵活性
- 效率

## 冗余负载均衡器

您一定已经猜到了，负载均衡器本身可能存在单点故障。为了克服这个问题，可以在集群模式中使用第二个或N个负载均衡器。

而且，如果出现故障检测，主动负载均衡器出现故障，另一个被动负载均衡器可以接管，这将使我们的系统更具容错能力。

![redundant-load-balancing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/load-balancing/redundant-load-balancer.png)

## 特性

以下是负载均衡器的一些常用特性:

- **自动伸缩:**根据需求条件启动和关闭资源。
- **保持会话:**将相同的用户或设备分配给相同的资源以维护资源上的会话状态的能力。
- **运行状况检查:**确定资源是否出现故障或运行不良，以便从负载平衡池中删除该资源的能力。
- **持久连接:**允许服务器打开与客户机(如WebSocket)的持久连接。
- **加密:**处理加密连接，如TLS和SSL。
- **证书:**向客户端提供证书并对客户端证书进行身份验证。
- **压缩:**响应的压缩。
- **缓存:**应用程序层负载均衡器可以提供缓存响应的能力。
- **日志记录:**请求和响应元数据的日志记录可以作为重要的审计跟踪或分析数据来源。
- **请求跟踪:**为每个请求分配一个惟一的id，用于日志记录、监视和故障排除。
- **重定向:**基于请求路径等因素重定向传入请求的能力。
- **固定响应:**为请求(如错误消息)返回静态响应。

## 例子

以下是业界常用的一些负载均衡解决方案:

[https://aws.amazon.com/elasticloadbalancing](https://aws.amazon.com/elasticloadbalancing)

[https://azure.microsoft.com/en-in/services/load-balancer](https://azure.microsoft.com/en-in/services/load-balancer)
[https://cloud.google.com/load-balancing](https://cloud.google.com/load-balancing)
[https://www.digitalocean.com/products/load-balancer](https://www.digitalocean.com/products/load-balancer)

[https://www.nginx.com/](https://www.nginx.com/)

[http://www.haproxy.org/](http://www.haproxy.org/)

# 集群

在高层次上，计算机集群是由两台或两台以上的计算机或节点组成的一组，它们并行运行以实现一个共同的目标。这允许将由大量独立的、可并行的任务组成的工作负载分布到集群中的节点之间。因此，这些任务可以利用每台计算机的综合内存和处理能力来提高总体性能。

要建立一个计算机集群，单个节点应该连接到一个网络，以实现节点之间的通信。然后将节点连接在一起，形成集群。它可能在每个节点上都有共享存储设备或者本地存储。

![cluster](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/clustering/cluster.png)

通常，至少有一个节点被指定为领导（leader）节点，并充当到集群的入口点。领导节点可能负责将传入的工作委派给其他节点，并在必要时聚合结果并向用户返回响应。

理想情况下，集群的功能就像单个系统一样。访问集群的用户不应该需要知道系统是集群还是单独的机器。此外，集群的设计应尽量减少延迟并防止节点间通信的瓶颈。

## 种类

计算机集群一般可分为三类:

- 高可用性或故障转移
- 负载均衡
- 高性能计算

## 配置

两种最常用的高可用性(HA)集群配置是active-active和active-passive。

### Active-Active

![active-active](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/clustering/active-active.png)

active-active集群通常由至少两个节点组成，两个节点同时积极地运行同一种服务。双活集群的主要目的是实现负载均衡。负载均衡器将工作负载分布到所有节点上，以防止任何单个节点过载。因为有更多的节点可以服务，所以吞吐量和响应时间也会得到改善。

### Active-Passive

![active-passive](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/clustering/active-passive.png)

与双活集群配置类似，主从集群也至少包含两个节点。然而，正如主从的名称所暗示的那样，并非所有节点都将是活动的。例如，在两个节点的情况下，如果第一个节点已经是活动的，那么第二个节点必须是被动的或处于备用状态。

## 优势

集群计算的四大优势如下:

- 高可用性
- 可伸缩性
- 性能
- 具有成本效益

## 负载均衡 VS 集群

负载均衡与集群有一些共同的特征，但它们是不同的过程。集群提供冗余，提高容量和可用性。集群中的服务器彼此了解，并为一个共同的目的而一起工作。但是在负载均衡的情况下，服务器之间并不知道彼此。相反，它们对从负载均衡器收到的请求做出反应。

我们可以将负载平衡与集群结合使用，但它也适用于涉及具有共同目的的独立服务器的情况，如运行网站、业务应用程序、web服务或其他it资源。

## 挑战

集群带来的最明显的挑战是安装和维护的复杂性增加。必须在每个节点上安装和更新操作系统、应用程序及其依赖项。

如果集群中的节点不是同构的，这就会变得更加复杂。还必须密切监视每个节点的资源利用率，并且应该聚合日志，以确保软件运行正确。

此外，存储变得更加难以管理，共享存储设备必须防止节点之间的覆盖，分布式数据存储必须保持同步。

## 例子

集群在行业中经常使用，而且通常许多技术都提供某种类型的集群模式。例如:

- 容器(kubernets ，亚马逊 ECS 等)
- 数据库（Cassandra,MongoDB 等）
- 缓存（redis 等）

# 缓存

“在计算机科学中只有两件难事:缓存失效和命名。”—— Phil Karlton

![caching](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/caching.png)

缓存的主要目的是通过减少对底层较慢存储层的访问需求来提高数据检索性能。为了交换容量和速度，缓存通常暂时存储数据的子集，而数据库的数据通常是完整和持久的。

缓存利用了引用的局部性原则“最近请求的数据很可能再次被请求”。

## 缓存和内存

像计算机的内存一样，缓存是一种紧凑的、执行速度快的内存，它按层次结构存储数据，从第一级开始，它们被标记为L1、L2、L3等等。如果有请求，缓存也会被写入，比如有更新，需要将新内容保存到缓存中，以替换已保存的旧内容。

无论缓存是读还是写，它都是一个块一个块地执行。每个块还有一个标记，其中包括数据存储在缓存中的位置。当从缓存请求数据时，将通过标记进行搜索，以查找内存第一级(L1)中需要的特定内容。如果没有找到正确的数据，就在L2中进行更多的搜索。

如果在那里没有找到数据，则在L3中继续搜索，然后是L4，以此类推，直到找到数据，然后读取并加载数据。如果在缓存中根本找不到数据，就会将其写入缓存中，以便下次快速检索。

## 缓存命中与未命中

### 缓存命中

缓存命中描述从缓存中成功提供内容的情况。标记在内存中被快速搜索，当数据被找到并读取时，它被认为是缓存命中。

**Cold，Warm，以及 Hot 缓存**

缓存命中也可以描述为冷（cold）、warm（温）或 Hot（热）。在每一种方法中，都描述了读取数据的速度。

热缓存是一种以最快的速度从内存中读取数据的实例。这发生在从L1检索数据时。

冷缓存是读取数据的可能最慢的速率，但是它仍然是成功的，因此它仍然被认为是缓存命中。数据只在内存层次结构中较低的位置(如L3或更低)中找到。

温缓存用于描述L2或L3中的数据。它没有热缓存快，但仍然比冷缓存快。通常，称缓存为warm是用来表示它比热缓存更慢，更接近冷缓存。

### 缓存未命中

缓存丢失指的是在搜索内存时没有找到数据的实例。当发生这种情况时，内容将被传输并写入缓存。

## 缓存失效

缓存失效是计算机系统声明缓存条目无效并删除或替换它们的过程。如果数据被修改了，那么它应该在缓存中失效，否则，这可能导致不一致的应用程序行为。有三种缓存系统:

### 直写式高速缓存

![write-through-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/write-through-cache.png)

数据同时写入缓存和相应的数据库。

**优点:**快速检索，缓存和存储之间的数据完全一致。

**缺点:**写操作的延迟更高。

### 环绕写缓存

![write-around-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/write-around-cache.png)

写操作直接写入数据库或永久存储，绕过缓存。

**优点:**这可以减少延迟。

**缺点:**它增加了缓存丢失，因为缓存系统必须在缓存丢失的情况下从数据库中读取信息。因此，对于快速写入和重新读取信息的应用程序来说，这可能会导致更高的读延迟。读取从较慢的后端存储发生，并经历较高的延迟

### 回写缓存

![write-back-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/write-back-cache.png)

其中只对缓存层进行写操作，对缓存层的写操作完成后立即确认。然后，缓存将此写入异步同步到数据库。

**优点:**这将降低写密集型应用程序的延迟和高吞吐量。

**缺点:**如果缓存层崩溃，有数据丢失的风险。我们可以通过让多个副本承认缓存中的写操作来改进这一点。

## 清除策略

以下是一些最常见的缓存清除策略:

- **先进先出(FIFO):**缓存首先删除被访问的第一个块，而不考虑它之前被访问的频率或次数。
- **后进先出(LIFO):**缓存首先删除最近访问的块，而不考虑它之前被访问的频率或次数。
- 最近最少使用(LRU):首先丢弃最近最少使用的条目。
- 最近使用(MRU):与LRU相比，首先丢弃最近使用的条目。
- 最不常使用(LFU):计算物品被使用的频率。那些最不常被使用的首先被丢弃。
- 随机替换(RR):随机选择一个候选项，并在必要时丢弃它以腾出空间。

## 分布式缓存

![distributed-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/distributed-cache.png)

分布式缓存是一种系统，它将多台联网计算机的随机访问存储器(RAM)集中到一个单独的内存数据存储中，用作数据缓存，以提供对数据的快速访问。虽然大多数缓存传统上都在一个物理服务器或硬件组件中，但分布式缓存可以通过将多台计算机链接在一起，从而超越单台计算机的内存限制。

## 全局缓存

![global-cache](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/caching/global-cache.png)

顾名思义，我们将拥有一个所有应用程序节点都将使用的共享缓存。当在全局缓存中找不到请求的数据时，缓存负责从底层数据存储中找出缺失的数据块。

### 使用场景

缓存可以有许多真实的用例，例如:

- 数据库缓存
- 内容传送网络(CDN)
- DNS (Domain Name System)缓存
- API的缓存

**什么时候不使用缓存?**

让我们再看看一些不应该使用缓存的场景:

- 当访问缓存的时间与访问主数据存储的时间一样长时，缓存是没有帮助的。
- 当请求具有较低的重复(较高的随机性)时，缓存就不能很好地工作，因为缓存性能来自重复的内存访问模式。
- 当数据频繁更改时，缓存没有帮助，因为缓存的版本不同步，而且每次都必须访问主数据存储。

需要注意的是，缓存不应该用作永久数据存储。它们几乎总是在易失性内存中实现，因为它更快，因此应该被认为是瞬态的。

## 优势

下面是缓存的一些优点:

- 提高了性能
- 减少延迟
- 减少数据库的负载
- 降低网络成本
- 增加读吞吐量

## 例子

下面是一些常用的缓存技术:

- Redis
- Memcached
- Amazon Elasticache
- Aerospike

# Content Delivery Network (CDN)

内容传递网络(CDN)是一组地理上分布的服务器，它们一起工作以提供互联网内容的快速传递。一般来说，静态文件如HTML/CSS/JS、照片和视频都是从CDN提供的。

![cdn-map](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/content-delivery-network/cdn-map.png)

## 为什么使用CDN?

内容分发网络(CDN)增加了内容的可用性和冗余，同时降低了带宽成本并提高了安全性。为CDN的内容提供服务可以显著提高性能，因为用户从他们附近的数据中心接收内容，而我们的服务器不必为CDN完成的请求提供服务。

## CDN 如何工作？

![cdn](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/content-delivery-network/cdn.png)

在CDN中，原始服务器包含内容的原始版本，而边缘服务器数量众多，分布在世界各地的不同地点。

为了使访问者和网站服务器之间的距离最小化，CDN将其内容的缓存版本存储在多个地理位置，称为边缘位置。每个边缘位置包含几个缓存服务器，负责向其附近的访问者发送内容。

一旦静态资产被缓存到特定位置的所有CDN服务器上，所有后续网站访问者对静态资产的请求都将从这些边缘服务器而不是源服务器发送，从而减少源服务器负载并提高可伸缩性。

例如，当有人在英国请求我们的网站可能在美国托管，他们将从最近的边缘位置，如伦敦边缘位置服务。这比访问者向源服务器发出一个完整的请求要快得多，后者会增加延迟。

## 类型

CDN 一般分为两种类型：

### Push CDN

每当服务器上发生更改时，推送cdn就会接收新内容。我们完全负责提供内容，直接上传到CDN，并重写指向CDN的url。我们可以配置内容何时过期以及何时更新。只有当内容是新的或更改的时候才会上传内容，从而最小化流量，但最大化存储空间。

流量较少的网站或内容不经常更新的网站可以很好地使用推送cdn。内容只放在cdn上一次，而不是定期重新拉取。

### Pull CDN

在Pull CDN情况下，缓存会根据请求进行更新。当客户端发送一个请求，要求从CDN获取静态资产(如果CDN没有静态资产)时，它将从源服务器获取新更新的资产，并用这个新资产填充它的缓存，然后将这个新缓存的资产发送给用户。

与Push CDN相反，这需要更少的维护，因为CDN节点上的缓存更新是基于客户端到源服务器的请求执行的。流量大的网站使用拉式CDN效果很好，因为流量分布更均匀，只有最近请求的内容留在CDN上。

## 缺点

众所周知，好东西总是要付出额外的代价，所以让我们来讨论一下cdn的一些缺点:

- **额外费用:**使用CDN可能很贵，特别是对于高流量的服务。
- **限制:**一些组织和国家已经屏蔽了流行的cdn的域或IP地址。
- **位置:**如果我们的大多数受众位于一个CDN没有服务器的国家，我们网站上的数据可能要比没有使用任何CDN的情况下传播得更远。

## 例子

- Amazon CloudFront
- Google Cloud CDN
- Cloudflare CDN
- Fastly

# 代理

代理服务器是位于客户机和后端服务器之间的硬件/软件的中间部分。它接收来自客户机的请求并将其转发到源服务器。通常，代理用于过滤请求、记录请求，有时也用于转换请求(通过添加/删除标头、加密/解密或压缩)。

## 类型

有两种代理类型:

### 正向代理

正向代理，通常称为代理、代理服务器或web代理，是位于一组客户端机器前面的服务器。当这些计算机向互联网上的网站和服务发出请求时，代理服务器就会拦截这些请求，然后代表这些客户端与web服务器进行通信，就像中间人一样。

![forward-proxy](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/proxy/forward-proxy.png)

**优势**

正向代理有如下优势:

- 阻止访问某些内容
- 允许访问地理限制的某些内容
- 提供匿名
- 避免其他浏览限制

虽然代理提供了匿名的好处，但它们仍然可以跟踪我们的个人信息。代理服务器的设置和维护成本很高，需要进行配置。

### **反向代理**

反向代理是一个位于一个或多个web服务器前面的服务器，拦截来自客户端的请求。当客户端向网站的源服务器发送请求时，这些请求会被反向代理服务器拦截。

正向代理和反向代理之间的区别很微妙，但很重要。用一种简单的方法来总结它，即正向代理位于客户机前面，并确保没有原始服务器直接与该特定客户机通信。另一方面，反向代理位于源服务器前面，确保没有客户机直接与该源服务器通信。

![reverse-proxy](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/proxy/reverse-proxy.png)

引入反向代理会增加复杂性。单个反向代理是一个单点故障，配置多个反向代理(即故障转移)进一步增加了复杂性。

**优势**

下面是使用反向代理的一些优势:

- 改善安全
- 缓存
- SSL 加密
- 负载均衡
- 可扩展性和灵活性

## 负载均衡 **vs 反向代理**

等等，反向代理不是类似于负载均衡器吗?当我们有多个服务器时，负载均衡器是有用的。通常，负载均衡器将流量路由到一组服务相同功能的服务器上，而反向代理即使只对一个web服务器或应用服务器也很有用。反向代理也可以充当负载均衡器，但反过来就不行。

## 案例

下面是常用的一些代理方案:

- [Nginx](https://www.nginx.com/)
- [HAProxy](http://www.haproxy.org/)
- [Traefik](https://doc.traefik.io/traefik)
- [Envoy](https://www.envoyproxy.io/)

# 可用性

可用性是指系统在特定时期内保持运行以执行所需功能的时间。它是对系统、服务或机器在正常条件下保持运行的时间百分比的简单度量。

## **可用性的 9**

Availability is often quantified by uptime (or downtime) as a percentage of time the service is available. It is generally measured in the number of 9s.

Availability=Uptime(Uptime+Downtime)

If availability is 99.00% available, it is said to have "2 nines" of availability, and if it is 99.9%, it is called "3 nines", and so on.

可用性通常由正常运行时间(或停机时间)作为服务可用时间的百分比来量化。它通常以9的数量来衡量。

可用性=Uptime(正常运行时间+停机时间)

如果可用性为99.00%，则称为“2个9”可用性，如果是99.9%，则称为“3个9”，以此类推。

| Availability (Percent) | Downtime (Year) | Downtime (Month) | Downtime (Week) |
| --- | --- | --- | --- |
| 90% (one nine) | 36.53 days | 72 hours | 16.8 hours |
| 99% (two nines) | 3.65 days | 7.20 hours | 1.68 hours |
| 99.9% (three nines) | 8.77 hours | 43.8 minutes | 10.1 minutes |
| 99.99% (four nines) | 52.6 minutes | 4.32 minutes | 1.01 minutes |
| 99.999% (five nines) | 5.25 minutes | 25.9 seconds | 6.05 seconds |
| 99.9999% (six nines) | 31.56 seconds | 2.59 seconds | 604.8 milliseconds |
| 99.99999% (seven nines) | 3.15 seconds | 263 milliseconds | 60.5 milliseconds |
| 99.999999% (eight nines) | 315.6 milliseconds | 26.3 milliseconds | 6 milliseconds |
| 99.9999999% (nine nines) | 31.6 milliseconds | 2.6 milliseconds | 0.6 milliseconds |

## 可用性（顺序 vs 并行程序）

如果一个服务由多个容易发生故障的组件组成，那么该服务的整体可用性取决于组件是按顺序还是并行进行的。

### **顺序**

Overall availability decreases when two components are in sequence.

Availability (Total)=Availability (Foo)∗Availability (Bar)

For example, if both `Foo` and `Bar` each had 99.9% availability, their total availability in sequence would be 99.8%.

当两个组件按顺序排列时，整体可用性会下降。

可用性(总数)=可用性(Foo)∗可用性(Bar)

例如，如果`Foo` 和`Bar`都有99.9%的可用性，那么它们的总可用性将依次为99.8%。

### 并行

Overall availability increases when two components are in parallel.

Availability (Total)=1−(1−Availability (Foo))∗(1−Availability (Bar))

For example, if both `Foo` and `Bar` each had 99.9% availability, their total availability in parallel would be 99.9999%.

当两个组件并行时，整体可用性会提高。

可用性(Total)=1−(1−可用性(Foo))∗(1−可用性(Bar))

例如，如果'`Foo` 和`Bar` 都有99.9%的可用性，那么它们并行的总可用性将是99.9999%。

## 可用性 **vs 可靠性**

如果一个系统是可靠的，那么它就是可用的。然而，即使它是可用的，也不一定是可靠的。换句话说，高可靠性有助于高可用性，但即使在不可靠的系统中也有可能实现高可用性。

## 高可用性 **vs 容错性**

高可用性和容错性都适用于提供高正常运行时间级别的方法。然而，他们完成的目标不同。

容错系统业务不中断，但成本显著高于高可用系统;高可用系统业务中断最小。容错需要完全的硬件冗余，就像如果主系统出现故障，而不损失正常运行时间一样，另一个系统应该接管。

# 可伸缩性

可伸缩性是通过添加或删除资源以满足需求来衡量系统对变化的响应程度。

![scalability](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-I/scalability/scalability.png)

让我们讨论不同类型的伸缩：

## **垂直方向扩展**

垂直扩展(也称为向上扩展)通过向现有机器添加更多的功能来扩展系统的可伸缩性。换句话说，垂直扩展指的是通过增加硬件容量来改进应用程序的能力。

### **优势**

- 操作简单
- 更容易管理
- 数据一致

### **劣势**

- 高停机时间的风险
- 升级难度更大
- 可能单点故障

## **水平方向扩展**

水平扩展(也称为向外扩展)通过添加更多的机器来扩展系统的规模。它通过向现有的服务器池添加更多的实例来提高服务器的性能，允许负载更均匀地分配。

### 优势

- 增加冗余
- 更好的容错能力
- 灵活高效
- 更容易升级

### 劣势

- 增加了复杂性
- 数据不一致
- 下游业务负载增加

# 存储

存储是一种使系统能够暂时或永久地保留数据的机制。在系统设计的上下文中，这个主题通常被跳过，但是，重要的是要对一些常见的存储技术类型有一个基本的了解，这可以帮助我们对存储组件进行微调。让我们来讨论一些重要的存储概念:

## **RAID**

RAID (Redundant Array of Independent Disks)是一种将相同的数据存储在多个硬盘或固态硬盘(ssd)上的方法，以在硬盘故障的情况下保护数据。

但是，有不同的RAID级别，并不是所有级别都以提供冗余为目标。让我们来讨论一些常用的RAID级别:

- **RAID 0**:也称为条带化，将数据平均分配到阵列中的所有硬盘上。
- **RAID 1**:也称为镜像，一组数据的精确副本至少在两个硬盘中。如果一个驱动器失败了，其他驱动器仍然可以工作。
- **RAID 5**:条带校验。需要使用至少3个驱动器，跨多个驱动器(如RAID 0)划分数据，但也有一个分布在驱动器上的奇偶校验。
- **RAID 6**:双奇偶分条。RAID 6与RAID 5类似，但校验数据被写入两个驱动器。
- **RAID 10**: RAID 0和RAID 1分条+镜像。它通过镜像辅助驱动器上的所有数据来提供安全性，同时使用跨每组驱动器的分条来加速数据传输。

### **比较**

让我们来比较一下不同RAID级别的所有特性::

| Features | RAID 0 | RAID 1 | RAID 5 | RAID 6 | RAID 10 |
| --- | --- | --- | --- | --- | --- |
| 描述 | 分段 | 镜像 | 带有奇偶校验的条带化 | 用双奇偶校验条带 | 分段和镜像 |
| 最少磁盘数 | 2 | 2 | 3 | 4 | 4 |
| 读性能 | High | High | High | High | High |
| 写性能 | High | Medium | High | High | Medium |
| 成本 | Low | High | Low | Low | High |
| 容错 | None | 单驱动失败 | 单驱动失败 | 双驱动失败 | 每个子阵列最多有一个磁盘故障 |
| 空间利用率 | 100% | 50% | 67%-94% | 50%-80% | 50% |

## 卷 **Volumes**

卷是磁盘或磁带上固定数量的存储空间。术语卷通常用作存储本身的同义词，但是一个磁盘可能包含多个卷，或者一个卷可能跨越多个磁盘。

## 文件存储

File storage is a solution to store data as files and present it to its final users as a hierarchical directories structure. The main advantage is to provide a user-friendly solution to store and retrieve files. To locate a file in file storage, the complete path of the file is required. It is economical and easily structured and is usually found on hard drives, which means that they appear exactly the same for the user and on the hard drive.

文件存储是一种将数据存储为文件并将其作为分层目录结构呈现给最终用户的解决方案。它的主要优点是为存储和检索文件提供了一个用户友好的解决方案。要在文件存储中定位文件，需要文件的完整路径。它既经济又易于构造，通常在硬盘驱动器上找到，这意味着它们对用户和在硬盘驱动器上显示完全相同。

例如: [Amazon EFS](https://aws.amazon.com/efs), [Azure files](https://azure.microsoft.com/en-in/services/storage/files), [Google Cloud Filestore](https://cloud.google.com/filestore), etc.

## 块存储

块存储将数据划分为块(chunk)，并将它们存储为独立的块。每个数据块都有一个唯一的标识符，这使得存储系统可以将较小的数据块放在最方便的地方。

块存储还将数据与用户环境解耦，允许数据跨多个环境分布。这将创建到数据的多个路径，并允许用户快速检索数据。当用户或应用程序向块存储系统请求数据时，底层存储系统将数据块重新组合，并将数据呈现给用户或应用程序

例如:亚马逊EBS ([https://aws.amazon.com/ebs](https://aws.amazon.com/ebs))。

## 对象存储

对象存储也称为基于对象的存储，它将数据文件分解为称为对象的片段。然后，它将这些对象存储在单个存储库中，该存储库可以分布在多个网络系统中。

例如: [Amazon S3](https://aws.amazon.com/s3), [Azure Blob Storage](https://azure.microsoft.com/en-in/services/storage/blobs), [Google Cloud Storage](https://cloud.google.com/storage), etc.

## **NAS**

NAS(网络连接存储)是一种连接到网络的存储设备，它允许从中心位置为授权的网络用户存储和检索数据。NAS设备是灵活的，这意味着当我们需要额外的存储时，我们可以增加现有的存储。它更快、更便宜，并且提供了现场公共云的所有好处，让我们可以完全控制。

## **HDFS**

Hadoop分布式文件系统(HDFS)是一种设计用于在商用硬件上运行的分布式文件系统。HDFS具有很高的容错能力，被设计用于部署在低成本的硬件上。HDFS提供对应用程序数据的高吞吐量访问，适用于拥有大型数据集的应用程序。它与现有的分布式文件系统有许多相似之处。

HDFS设计用于在大型集群中跨机器可靠地存储非常大的文件。它将每个文件存储为块序列，除最后一个块外，文件中的所有块都是相同的大小。复制文件的块是为了容错。

# 数据库与DBMS

## 什么是数据库**?**

数据库是结构化信息或数据的有组织的集合，通常以电子方式存储在计算机系统中。数据库通常由数据库管理系统(DBMS)控制。数据和DBMS以及与之相关联的应用程序一起被称为数据库系统，通常简称为数据库。

## 什么是 **DBMS?**

一个数据库通常需要一个全面的数据库软件程序，称为数据库管理系统(DBMS)。DBMS充当数据库和最终用户或程序之间的接口，允许用户检索、更新和管理信息的组织和优化方式。DBMS还促进了对数据库的监督和控制，支持各种管理操作，如性能监视、调优以及备份和恢复。

## 组成部分

以下是在不同数据库类型中发现的一些常见组件:

### **Schema**

模式的作用是定义数据结构的形状，并指定什么类型的数据可以放在哪里。模式可以在整个数据库中严格执行，也可以在数据库的一部分上松散执行，或者它们可能根本不存在。

### **Table**

每个表都包含不同的列，就像电子表格一样。一个表可以只有两个列，也可以有100多个列，具体取决于表中所放信息的类型。

### **Column**

列包含一组特定类型的数据值，数据库的每一行对应一个值。列可以包含文本值、数字、枚举、时间戳等。

### **Row**

表中的数据按行记录。一个表中可能有数千或数百万行具有任何特定的信息。

## **Types**

![database-types](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/databases-and-dbms/database-types.png)

以下是不同类型的数据库:

- **[SQL](https://karanpratapsingh.com/courses/system-design/sql-databases)**
- **[NoSQL](https://karanpratapsingh.com/courses/system-design/nosql-databases)**
    - Document
    - Key-value
    - Graph
    - Timeseries
    - Wide column
    - Multi-model

SQL和NoSQL数据库是广泛的主题，后续将在SQL数据库和NoSQL数据库中分别讨论。了解它们在SQL和NoSQL数据库中如何相互比较。

## 挑战

大规模运行数据库时面临的一些常见挑战:

- **吸收显著增长的数据量**:来自传感器、连接机器和几十个其他来源的数据爆炸。
- **确保数据安全**:如今，数据泄露无处不在，确保数据安全且用户易于访问比以往任何时候都更重要。
- **跟上需求**:公司需要实时访问其数据，以支持及时决策和利用新机会。
- **管理和维护数据库和基础设施**:随着数据库变得越来越复杂和数据量的增长，公司面临着雇用额外的人才来管理数据库的费用。
- **消除对可伸缩性的限制**:如果一个业务想要生存就需要发展，它的数据管理也必须随之发展。但很难预测该公司将需要多少容量，特别是对于内部数据库。
- **确保数据驻留、数据主权或延迟需求**:一些组织有更适合在内部运行的用例。在这些情况下，为运行数据库预配置和预优化的工程系统是理想的。

# 关系型数据库

关系数据库是指数据项之间具有预定义关系的集合。这些项目被组织为一组带有列和行的表。表用于保存关于要在数据库中表示的对象的信息。表中的每一列保存某种类型的数据，字段存储属性的实际值。表中的行表示一个对象或实体的相关值的集合。

可以用称为主键的唯一标识符标记表中的每一行，并且可以使用外键使多个表中的行相互关联。可以通过多种不同的方式访问这些数据，而无需重新组织数据库表本身。关系数据库通常遵循[ACID一致性模型](https://karanpratapsingh.com/courses/system-design/acid-and-base-consistency-models#acid)。

## 物化视图

物化视图是由查询规范导出并存储以供以后使用的预先计算的数据集。由于数据是预先计算的，因此查询物化视图比对视图的基表执行查询要快。当查询频繁运行或非常复杂时，这种性能差异会非常显著。

它还支持数据子集设置，并提高在大型数据集上运行的复杂查询的性能，从而减少网络负载。物化视图还有其他用途，但它们主要用于性能和复制。

## N+1 查询问题

当数据访问层执行N个额外的SQL语句来获取在执行主SQL查询时可以检索到的相同数据时，就会出现N+1查询问题。N的值越大，执行的查询越多，对性能的影响也越大。

这在GraphQL和ORM(对象-关系映射)工具中很常见，可以通过优化SQL查询或使用批量处理连续请求并在底层发出单个数据请求的数据加载器来解决。

## 优势

让我们看看使用关系数据库的一些优点:

- 简单准确
- 可访问性
- 数据一致性
- 灵活性

## 劣势

以下是关系数据库的缺点:

- 维护费用昂贵
- 困难的模式进化
- 性能打击(加入，反常态化等)
- 由于水平可扩展性差，难以扩展

## 例子

下面是一些常用的关系数据库:
- [PostgreSQL](https://www.postgresql.org)
- [MySQL](https://www.mysql.com)
- [MariaDB](https://mariadb.org)
- [Amazon Aurora](https://aws.amazon.com/rds/aurora)

# 非关系型数据库

NoSQL是一个广泛的类别，包括任何不使用SQL作为其主要数据访问语言的数据库。这些类型的数据库有时也称为非关系型数据库。与关系型数据库不同，NoSQL数据库中的数据不必遵循预定义的模式。NoSQL数据库遵循[BASE一致性模型](https://karanpratapsingh.com/courses/system-design/acid-and-base-consistency-models#base)。

以下是不同类型的NoSQL数据库:

### Document

文档数据库(也称为面向文档的数据库或文档存储)是在文档中存储信息的数据库。它们是通用数据库，为事务性和分析性应用程序提供各种用例。

**优势**

- 只管且灵活
- 轻松的水平扩展
- 无 schema

**劣势**

- 无schema
- 非关系

**例如**

- [MongoDB](https://www.mongodb.com)
- [Amazon DocumentDB](https://aws.amazon.com/documentdb)
- [CouchDB](https://couchdb.apache.org)

### Key-value

键值数据库是最简单的NoSQL数据库类型之一，它将数据保存为一组键值对，每组键值对由两个数据项组成。它们有时也被称为键值存储。

**优势**

- 简单且性能很好
- 高流量下的高度可扩展
- 会话管理
- 优化查找

**劣势**

- 只具备基础的CRUD
- 不能过滤值
- 缺乏索引和搜寻功能
- 未能优化复杂查询

**例如**

- [Redis](https://redis.io)
- [Memcached](https://memcached.org)
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
- [Aerospike](https://aerospike.com)

### 图数据库

图数据库是一种NoSQL数据库，它使用图结构进行具有节点、边和属性的语义查询，以表示和存储数据，而不是表或文档。

图将存储中的数据项与节点和边的集合联系起来，边表示节点之间的关系。这种关系允许存储中的数据直接链接在一起，在许多情况下，只需要一个操作就可以检索。

**优势**

- 查询快
- 灵活性
- 明确的数据展示

**劣势**

- 复杂
- 不具备标准化查询

**使用场景**

- 欺诈检测
- 推荐引擎
- 社交网络
- 网络映射

**例如**

- [Neo4j](https://neo4j.com)
- [ArangoDB](https://www.arangodb.com)
- [Amazon Neptune](https://aws.amazon.com/neptune)
- [JanusGraph](https://janusgraph.org)

### 时序数据库

时间序列数据库是针对时间戳或时间序列数据优化的数据库。

**优势**

- 快速的插入和检索
- 高效的数据存储

**使用场景**

- 物联网数据
- 指标分析
- 应用监控
- 了解金融趋势

**例如**

- [InfluxDB](https://www.influxdata.com)
- [Apache Druid](https://druid.apache.org)

### 宽表（Wide column）

宽表数据库，也称为宽列存储，是模式不可知的。数据存储在列族中，而不是在行和列中。

**优势**

- 高度可扩展，可以处理 PB 级数据
- 非常适合实时大数据应用

**劣势**

- 昂贵
- 增加了写耗时

**使用场景**

- 商业分析
- 属性数据存储

**例如**

- [BigTable](https://cloud.google.com/bigtable)
- [Apache Cassandra](https://cassandra.apache.org)
- [ScyllaDB](https://www.scylladb.com)

### 多模（Multi-model）

多模数据库将不同的数据库模型(即关系、图、键值、文档等)组合成一个单一的、集成的后端。这意味着它们可以容纳各种数据类型、索引、查询，并在多个模型中存储数据。

**优势**

- 灵活性
- 适用于复杂项目
- 数据一致性

**劣势**

- 复杂
- 不太成熟

**例如**

- [ArangoDB](https://www.arangodb.com)
- [Azure Cosmos DB](https://azure.microsoft.com/en-in/services/cosmos-db)
- [Couchbase](https://www.couchbase.com)

# 关系vs非关系数据库

在数据库世界中，有两种主要的解决方案，SQL(关系)和NoSQL(非关系)数据库。它们的构建方式、存储信息的类型以及存储信息的方式都有所不同。关系数据库是结构化的并且具有预定义的模式，而非关系数据库是非结构化的、分布式的并且具有动态的模式。

## 高层差异

### 存储

SQL将数据存储在表中，其中每一行表示一个实体，每列表示关于该实体的一个数据点。

NoSQL数据库有不同的数据存储模型，如键值、图、文档等。

### Schema

在SQL中，每个记录都遵循一个固定的模式，这意味着必须在数据输入之前决定和选择列，并且每行必须有对应每列的数据。模式可以稍后修改，但这涉及到使用迁移修改数据库。

而在NoSQL中，模式是动态的。字段可以动态添加，每个_record_(或等效项)不必包含每个_field_的数据。

### 查询

SQL数据库使用SQL(结构化查询语言)来定义和操作数据，这是非常强大的。

在NoSQL数据库中，查询集中在文档集合上。不同的数据库有不同的查询语法。

### 可伸缩性

在大多数常见情况下，SQL数据库是垂直伸缩的，这可能会非常昂贵。跨多个服务器扩展关系数据库是可能的，但这是一个具有挑战性和耗时的过程。

另一方面，NoSQL数据库是水平可扩展的，这意味着我们可以轻松地向NoSQL数据库基础设施添加更多的服务器，以处理大流量。任何廉价的商用硬件或云实例都可以托管NoSQL数据库，因此比垂直扩展的成本效益高得多。许多NoSQL技术也自动地跨服务器分发数据。

### 可靠性

绝大多数关系数据库都是ACID兼容的。因此，当涉及到数据可靠性和执行事务的安全保证时，SQL数据库仍然是更好的选择。

大多数NoSQL解决方案为了性能和可伸缩性牺牲了ACID遵从性。

## 选择参考

一如既往，我们应该总是选择更适合需求的技术。所以，让我们看看选择基于SQL或NoSQL的数据库的一些原因:

**For SQL**

- 结构化数据，且拥有严格的 schema
- 存储关系数据
- 需要复杂的连接查询
- 交易型
- 根据索引查找非常快

**For NoSQL**

- 动态或灵活的 schema
- 存储非关系数据
- 不需要复杂的连接查询
- 数据密集型工作
- 高吞吐量

# Database Replication

Replication is a process that involves sharing information to ensure consistency between redundant resources such as multiple databases, to improve reliability, fault-tolerance, or accessibility.

## Master-Slave Replication

The master serves reads and writes, replicating writes to one or more slaves, which serve only reads. Slaves can also replicate additional slaves in a tree-like fashion. If the master goes offline, the system can continue to operate in read-only mode until a slave is promoted to a master or a new master is provisioned.

![master-slave-replication](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/database-replication/master-slave-replication.png)

### Advantages

- Backups of the entire database of relatively no impact on the master.
- Applications can read from the slave(s) without impacting the master.
- Slaves can be taken offline and synced back to the master without any downtime.

### Disadvantages

- Replication adds more hardware and additional complexity.
- Downtime and possibly loss of data when a master fails.
- All writes also have to be made to the master in a master-slave architecture.
- The more read slaves, the more we have to replicate, which will increase replication lag.

## Master-Master Replication

Both masters serve reads/writes and coordinate with each other. If either master goes down, the system can continue to operate with both reads and writes.

![master-master-replication](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/database-replication/master-master-replication.png)

### Advantages

- Applications can read from both masters.
- Distributes write load across both master nodes.
- Simple, automatic, and quick failover.

### Disadvantages

- Not as simple as master-slave to configure and deploy.
- Either loosely consistent or have increased write latency due to synchronization.
- Conflict resolution comes into play as more write nodes are added and as latency increases.

## Synchronous vs Asynchronous replication

The primary difference between synchronous and asynchronous replication is how the data is written to the replica. In synchronous replication, data is written to primary storage and the replica simultaneously. As such, the primary copy and the replica should always remain synchronized.

In contrast, asynchronous replication copies the data to the replica after the data is already written to the primary storage. Although the replication process may occur in near-real-time, it is more common for replication to occur on a scheduled basis and it is more cost-effective.

# Indexes

Indexes are well known when it comes to databases, they are used to improve the speed of data retrieval operations on the data store. An index makes the trade-offs of increased storage overhead, and slower writes (since we not only have to write the data but also have to update the index) for the benefit of faster reads. Indexes are used to quickly locate data without having to examine every row in a database table. Indexes can be created using one or more columns of a database table, providing the basis for both rapid random lookups and efficient access to ordered records.

![indexes](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/indexes/indexes.png)

An index is a data structure that can be perceived as a table of contents that points us to the location where actual data lives. So when we create an index on a column of a table, we store that column and a pointer to the whole row in the index. Indexes are also used to create different views of the same data. For large data sets, this is an excellent way to specify different filters or sorting schemes without resorting to creating multiple additional copies of the data.

One quality that database indexes can have is that they can be **dense** or **sparse**. Each of these index qualities comes with its own trade-offs. Let's look at how each index type would work:

## Dense Index

In a dense index, an index record is created for every row of the table. Records can be located directly as each record of the index holds the search key value and the pointer to the actual record.

![dense-index](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/indexes/dense-index.png)

Dense indexes require more maintenance than sparse indexes at write-time. Since every row must have an entry, the database must maintain the index on inserts, updates, and deletes. Having an entry for every row also means that dense indexes will require more memory. The benefit of a dense index is that values can be quickly found with just a binary search. Dense indexes also do not impose any ordering requirements on the data.

## Sparse Index

In a sparse index, records are created only for some of the records.

![sparse-index](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/indexes/sparse-index.png)

Sparse indexes require less maintenance than dense indexes at write-time since they only contain a subset of the values. This lighter maintenance burden means that inserts, updates, and deletes will be faster. Having fewer entries also means that the index will use less memory. Finding data is slower since a scan across the page typically follows the binary search. Sparse indexes are also optional when working with ordered data.

# Normalization and Denormalization

## Terms

Before we go any further, let's look at some commonly used terms in normalization and denormalization.

### Keys

**Primary key**: Column or group of columns that can be used to uniquely identify every row of the table.

**Composite key**: A primary key made up of multiple columns.

**Super key**: Set of all keys that can uniquely identify all the rows present in a table.

**Candidate key**: Attributes that identify rows uniquely in a table.

**Foreign key**: It is a reference to a primary key of another table.

**Alternate key**: Keys that are not primary keys are known as alternate keys.

**Surrogate key**: A system-generated value that uniquely identifies each entry in a table when no other column was able to hold properties of a primary key.

### Dependencies

**Partial dependency**: Occurs when the primary key determines some other attributes.

**Functional dependency**: It is a relationship that exists between two attributes, typically between the primary key and non-key attribute within a table.

**Transitive functional dependency**: Occurs when some non-key attribute determines some other attribute.

### Anomalies

Database anomaly happens when there is a flaw in the database due to incorrect planning or storing everything in a flat database. This is generally addressed by the process of normalization.

There are three types of database anomalies:

**Insertion anomaly**: Occurs when we are not able to insert certain attributes in the database without the presence of other attributes.

**Update anomaly**: Occurs in case of data redundancy and partial update. In other words, a correct update of the database needs other actions such as addition, deletion, or both.

**Deletion anomaly**: Occurs where deletion of some data requires deletion of other data.

**Example**

Let's consider the following table which is not normalized:

| ID  | Name   | Role              | Team |
| --- | ------ | ----------------- | ---- |
| 1   | Peter  | Software Engineer | A    |
| 2   | Brian  | DevOps Engineer   | B    |
| 3   | Hailey | Product Manager   | C    |
| 4   | Hailey | Product Manager   | C    |
| 5   | Steve  | Frontend Engineer | D    |

Let's imagine, we hired a new person "John" but they might not be assigned a team immediately. This will cause an _insertion anomaly_ as the team attribute is not yet present.

Next, let's say Hailey from Team C got promoted, to reflect that change in the database, we will need to update 2 rows to maintain consistency which can cause an _update anomaly_.

Finally, we would like to remove Team B but to do that we will also need to remove additional information such as name and role, this is an example of a _deletion anomaly_.

## Normalization

Normalization is the process of organizing data in a database. This includes creating tables and establishing relationships between those tables according to rules designed both to protect the data and to make the database more flexible by eliminating redundancy and inconsistent dependency.

### Why do we need normalization?

The goal of normalization is to eliminate redundant data and ensure data is consistent. A fully normalized database allows its structure to be extended to accommodate new types of data without changing the existing structure too much. As a result, applications interacting with the database are minimally affected.

### Normal forms

Normal forms are a series of guidelines to ensure that the database is normalized. Let's discuss some essential normal forms:

**1NF**

For a table to be in the first normal form (1NF), it should follow the following rules:

- Repeating groups are not permitted.
- Identify each set of related data with a primary key.
- Set of related data should have a separate table.
- Mixing data types in the same column is not permitted.

**2NF**

For a table to be in the second normal form (2NF), it should follow the following rules:

- Satisfies the first normal form (1NF).
- Should not have any partial dependency.

**3NF**

For a table to be in the third normal form (3NF), it should follow the following rules:

- Satisfies the second normal form (2NF).
- Transitive functional dependencies are not permitted.

**BCNF**

Boyce-Codd normal form (or BCNF) is a slightly stronger version of the third normal form (3NF) used to address certain types of anomalies not dealt with by 3NF as originally defined. Sometimes it is also known as the 3.5 normal form (3.5NF).

For a table to be in the Boyce-Codd normal form (BCNF), it should follow the following rules:

- Satisfied the third normal form (3NF).
- For every functional dependency X → Y, X should be the super key.

_There are more normal forms such as 4NF, 5NF, and 6NF but we won't discuss them here. Check out this [amazing video](https://www.youtube.com/watch?v=GFQaEYEc8_8) that goes into detail._

In a relational database, a relation is often described as _"normalized"_ if it meets the third normal form. Most 3NF relations are free of insertion, update, and deletion anomalies.

As with many formal rules and specifications, real-world scenarios do not always allow for perfect compliance. If you decide to violate one of the first three rules of normalization, make sure that your application anticipates any problems that could occur, such as redundant data and inconsistent dependencies.

### Advantages

Here are some advantages of normalization:

- Reduces data redundancy.
- Better data design.
- Increases data consistency.
- Enforces referential integrity.

### Disadvantages

Let's look at some disadvantages of normalization:

- Data design is complex.
- Slower performance.
- Maintenance overhead.
- Require more joins.

## Denormalization

Denormalization is a database optimization technique in which we add redundant data to one or more tables. This can help us avoid costly joins in a relational database. It attempts to improve read performance at the expense of some write performance. Redundant copies of the data are written in multiple tables to avoid expensive joins.

Once data becomes distributed with techniques such as federation and sharding, managing joins across the network further increases complexity. Denormalization might circumvent the need for such complex joins.

_Note: Denormalization does not mean reversing normalization._

### Advantages

Let's look at some advantages of denormalization:

- Retrieving data is faster.
- Writing queries is easier.
- Reduction in number of tables.
- Convenient to manage.

### Disadvantages

Below are some disadvantages of denormalization:

- Expensive inserts and updates.
- Increases complexity of database design.
- Increases data redundancy.
- More chances of data inconsistency.

# ACID and BASE consistency models

Let's discuss the ACID and BASE consistency models.

## ACID

The term ACID stands for Atomicity, Consistency, Isolation, and Durability. ACID properties are used for maintaining data integrity during transaction processing.

In order to maintain consistency before and after a transaction relational databases follow ACID properties. Let us understand these terms:

### Atomic

All operations in a transaction succeed or every operation is rolled back.

### Consistent

On the completion of a transaction, the database is structurally sound.

### Isolated

Transactions do not contend with one another. Contentious access to data is moderated by the database so that transactions appear to run sequentially.

### Durable

Once the transaction has been completed and the writes and updates have been written to the disk, it will remain in the system even if a system failure occurs.

## BASE

With the increasing amount of data and high availability requirements, the approach to database design has also changed dramatically. To increase the ability to scale and at the same time be highly available, we move the logic from the database to separate servers. In this way, the database becomes more independent and focused on the actual process of storing data.

In the NoSQL database world, ACID transactions are less common as some databases have loosened the requirements for immediate consistency, data freshness, and accuracy in order to gain other benefits, like scale and resilience.

BASE properties are much looser than ACID guarantees, but there isn't a direct one-for-one mapping between the two consistency models. Let us understand these terms:

### Basic Availability

The database appears to work most of the time.

### Soft-state

Stores don't have to be write-consistent, nor do different replicas have to be mutually consistent all the time.

### Eventual consistency

The data might not be consistent immediately but eventually, it becomes consistent. Reads in the system are still possible even though they may not give the correct response due to inconsistency.

## ACID vs BASE Trade-offs

There's no right answer to whether our application needs an ACID or a BASE consistency model. Both the models have been designed to satisfy different requirements. While choosing a database we need to keep the properties of both the models and the requirements of our application in mind.

Given BASE's loose consistency, developers need to be more knowledgeable and rigorous about consistent data if they choose a BASE store for their application. It's essential to be familiar with the BASE behavior of the chosen database and work within those constraints.

On the other hand, planning around BASE limitations can sometimes be a major disadvantage when compared to the simplicity of ACID transactions. A fully ACID database is the perfect fit for use cases where data reliability and consistency are essential.

# CAP Theorem

CAP theorem states that a distributed system can deliver only two of the three desired characteristics Consistency, Availability, and Partition tolerance (CAP).

![cap-theorem](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/cap-theorem/cap-theorem.png)

Let's take a detailed look at the three distributed system characteristics to which the CAP theorem refers.

### Consistency

Consistency means that all clients see the same data at the same time, no matter which node they connect to. For this to happen, whenever data is written to one node, it must be instantly forwarded or replicated across all the nodes in the system before the write is deemed "successful".

### Availability

Availability means that any client making a request for data gets a response, even if one or more nodes are down.

### Partition tolerance

Partition tolerance means the system continues to work despite message loss or partial failure. A system that is partition-tolerant can sustain any amount of network failure that doesn't result in a failure of the entire network. Data is sufficiently replicated across combinations of nodes and networks to keep the system up through intermittent outages.

## Consistency-Availability Tradeoff

We live in a physical world and can't guarantee the stability of a network, so distributed databases must choose Partition Tolerance (P). This implies a tradeoff between Consistency (C) and Availability (A).

### CA database

A CA database delivers consistency and availability across all nodes. It can't do this if there is a partition between any two nodes in the system, and therefore can't deliver fault tolerance.

**Example**: [PostgreSQL](https://www.postgresql.org), [MariaDB](https://mariadb.org).

### CP database

A CP database delivers consistency and partition tolerance at the expense of availability. When a partition occurs between any two nodes, the system has to shut down the non-consistent node until the partition is resolved.

**Example**: [MongoDB](https://www.mongodb.com), [Apache HBase](https://hbase.apache.org).

### AP database

An AP database delivers availability and partition tolerance at the expense of consistency. When a partition occurs, all nodes remain available but those at the wrong end of a partition might return an older version of data than others. When the partition is resolved, the AP databases typically re-syncs the nodes to repair all inconsistencies in the system.

**Example**: [Apache Cassandra](https://cassandra.apache.org), [CouchDB](https://couchdb.apache.org).

# PACELC Theorem

The PACELC theorem is an extension of the CAP theorem. The CAP theorem states that in the case of network partitioning (P) in a distributed system, one has to choose between Availability (A) and Consistency (C).

PACELC extends the CAP theorem by introducing latency (L) as an additional attribute of a distributed system. The theorem states that else (E), even when the system is running normally in the absence of partitions, one has to choose between latency (L) and consistency (C).

_The PACELC theorem was first described by [Daniel J. Abadi](https://scholar.google.com/citations?user=zxeEF2gAAAAJ)._

![pacelc-theorem](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/pacelc-theorem/pacelc-theorem.png)

PACELC theorem was developed to address a key limitation of the CAP theorem as it makes no provision for performance or latency.

For example, according to the CAP theorem, a database can be considered Available if a query returns a response after 30 days. Obviously, such latency would be unacceptable for any real-world application.

# Transactions

A transaction is a series of database operations that are considered to be a _"single unit of work"_. The operations in a transaction either all succeed, or they all fail. In this way, the notion of a transaction supports data integrity when part of a system fails. Not all databases choose to support ACID transactions, usually because they are prioritizing other optimizations that are hard or theoretically impossible to implement together.

_Usually, relational databases support ACID transactions, and non-relational databases don't (there are exceptions)._

## States

A transaction in a database can be in one of the following states:

![transaction-states](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/transactions/transaction-states.png)

### Active

In this state, the transaction is being executed. This is the initial state of every transaction.

### Partially Committed

When a transaction executes its final operation, it is said to be in a partially committed state.

### Committed

If a transaction executes all its operations successfully, it is said to be committed. All its effects are now permanently established on the database system.

### Failed

The transaction is said to be in a failed state if any of the checks made by the database recovery system fails. A failed transaction can no longer proceed further.

### Aborted

If any of the checks fail and the transaction has reached a failed state, then the recovery manager rolls back all its write operations on the database to bring the database back to its original state where it was prior to the execution of the transaction. Transactions in this state are aborted.

The database recovery module can select one of the two operations after a transaction aborts:

- Restart the transaction
- Kill the transaction

### Terminated

If there isn't any roll-back or the transaction comes from the _committed state_, then the system is consistent and ready for a new transaction and the old transaction is terminated.

# Distributed Transactions

A distributed transaction is a set of operations on data that is performed across two or more databases. It is typically coordinated across separate nodes connected by a network, but may also span multiple databases on a single server.

## Why do we need distributed transactions?

Unlike an ACID transaction on a single database, a distributed transaction involves altering data on multiple databases. Consequently, distributed transaction processing is more complicated, because the database must coordinate the committing or rollback of the changes in a transaction as a self-contained unit.

In other words, all the nodes must commit, or all must abort and the entire transaction rolls back. This is why we need distributed transactions.

Now, let's look at some popular solutions for distributed transactions:

## Two-Phase commit

![two-phase-commit](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/distributed-transactions/two-phase-commit.png)

The two-phase commit (2PC) protocol is a distributed algorithm that coordinates all the processes that participate in a distributed transaction on whether to commit or abort (roll back) the transaction.

This protocol achieves its goal even in many cases of temporary system failure and is thus widely used. However, it is not resilient to all possible failure configurations, and in rare cases, manual intervention is needed to remedy an outcome.

This protocol requires a coordinator node, which basically coordinates and oversees the transaction across different nodes. The coordinator tries to establish the consensus among a set of processes in two phases, hence the name.

### Phases

Two-phase commit consists of the following phases:

**Prepare phase**

The prepare phase involves the coordinator node collecting consensus from each of the participant nodes. The transaction will be aborted unless each of the nodes responds that they're _prepared_.

**Commit phase**

If all participants respond to the coordinator that they are _prepared_, then the coordinator asks all the nodes to commit the transaction. If a failure occurs, the transaction will be rolled back.

### Problems

Following problems may arise in the two-phase commit protocol:

- What if one of the nodes crashes?
- What if the coordinator itself crashes?
- It is a blocking protocol.

## Three-phase commit

![three-phase-commit](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/distributed-transactions/three-phase-commit.png)

Three-phase commit (3PC) is an extension of the two-phase commit where the commit phase is split into two phases. This helps with the blocking problem that occurs in the two-phase commit protocol.

### Phases

Three-phase commit consists of the following phases:

**Prepare phase**

This phase is the same as the two-phase commit.

**Pre-commit phase**

Coordinator issues the pre-commit message and all the participating nodes must acknowledge it. If a participant fails to receive this message in time, then the transaction is aborted.

**Commit phase**

This step is also similar to the two-phase commit protocol.

### Why is the Pre-commit phase helpful?

The pre-commit phase accomplishes the following:

- If the participant nodes are found in this phase, that means that _every_ participant has completed the first phase. The completion of prepare phase is guaranteed.
- Every phase can now time out and avoid indefinite waits.

## Sagas

![sagas](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/distributed-transactions/sagas.png)

A saga is a sequence of local transactions. Each local transaction updates the database and publishes a message or event to trigger the next local transaction in the saga. If a local transaction fails because it violates a business rule then the saga executes a series of compensating transactions that undo the changes that were made by the preceding local transactions.

### Coordination

There are two common implementation approaches:

- **Choreography**: Each local transaction publishes domain events that trigger local transactions in other services.
- **Orchestration**: An orchestrator tells the participants what local transactions to execute.

### Problems

- The Saga pattern is particularly hard to debug.
- There's a risk of cyclic dependency between saga participants.
- Lack of participant data isolation imposes durability challenges.
- Testing is difficult because all services must be running to simulate a transaction.

# Sharding

Before we discuss sharding, let's talk about data partitioning:

## Data Partitioning

Data partitioning is a technique to break up a database into many smaller parts. It is the process of splitting up a database or a table across multiple machines to improve the manageability, performance, and availability of a database.

### Methods

There are many different ways one could use to decide how to break up an application database into multiple smaller DBs. Below are three of the most popular methods used by various large-scale applications:

**Horizontal Partitioning (or Sharding)**

In this strategy, we split the table data horizontally based on the range of values defined by the _partition key_. It is also referred to as **_database sharding_**.

**Vertical Partitioning**

In vertical partitioning, we partition the data vertically based on columns. We divide tables into relatively smaller tables with few elements, and each part is present in a separate partition.

In this tutorial, we will specifically focus on sharding.

## What is sharding?

Sharding is a database architecture pattern related to _horizontal partitioning_, which is the practice of separating one table's rows into multiple different tables, known as _partitions_ or _shards_. Each partition has the same schema and columns, but also a subset of the shared data. Likewise, the data held in each is unique and independent of the data held in other partitions.

![sharding](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/sharding/sharding.png)

The justification for data sharding is that, after a certain point, it is cheaper and more feasible to scale horizontally by adding more machines than to scale it vertically by adding powerful servers. Sharding can be implemented at both application or the database level.

## Partitioning criteria

There are a large number of criteria available for data partitioning. Some most commonly used criteria are:

### Hash-Based

This strategy divides the rows into different partitions based on a hashing algorithm rather than grouping database rows based on continuous indexes.

The disadvantage of this method is that dynamically adding/removing database servers becomes expensive.

### List-Based

In list-based partitioning, each partition is defined and selected based on the list of values on a column rather than a set of contiguous ranges of values.

### Range Based

Range partitioning maps data to various partitions based on ranges of values of the partitioning key. In other words, we partition the table in such a way that each partition contains rows within a given range defined by the partition key.

Ranges should be contiguous but not overlapping, where each range specifies a non-inclusive lower and upper bound for a partition. Any partitioning key values equal to or higher than the upper bound of the range are added to the next partition.

### Composite

As the name suggests, composite partitioning partitions the data based on two or more partitioning techniques. Here we first partition the data using one technique, and then each partition is further subdivided into sub-partitions using the same or some other method.

## Advantages

But why do we need sharding? Here are some advantages:

- **Availability**: Provides logical independence to the partitioned database, ensuring the high availability of our application. Here individual partitions can be managed independently.
- **Scalability**: Proves to increase scalability by distributing the data across multiple partitions.
- **Security**: Helps improve the system's security by storing sensitive and non-sensitive data in different partitions. This could provide better manageability and security to sensitive data.
- **Query Performance**: Improves the performance of the system. Instead of querying the whole database, now the system has to query only a smaller partition.
- **Data Manageability**: Divides tables and indexes into smaller and more manageable units.

## Disadvantages

- **Complexity**: Sharding increases the complexity of the system in general.
- **Joins across shards**: Once a database is partitioned and spread across multiple machines it is often not feasible to perform joins that span multiple database shards. Such joins will not be performance efficient since data has to be retrieved from multiple servers.
- **Rebalancing**: If the data distribution is not uniform or there is a lot of load on a single shard, in such cases we have to rebalance our shards so that the requests are as equally distributed among the shards as possible.

## When to use sharding?

Here are some reasons where sharding might be the right choice:

- Leveraging existing hardware instead of high-end machines.
- Maintain data in distinct geographic regions.
- Quickly scale by adding more shards.
- Better performance as each machine is under less load.
- When more concurrent connections are required.

# Consistent Hashing

Let's first understand the problem we're trying to solve.

## Why do we need this?

In traditional hashing-based distribution methods, we use a hash function to hash our partition keys (i.e. request ID or IP). Then if we use the modulo against the total number of nodes (server or databases). This will give us the node where we want to route our request.

![simple-hashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/consistent-hashing/simple-hashing.png)

$$
\begin{align*}
& Hash(key_1) \to H_1 \bmod N = Node_0 \\
& Hash(key_2) \to H_2 \bmod N = Node_1 \\
& Hash(key_3) \to H_3 \bmod N = Node_2 \\
& ... \\
& Hash(key_n) \to H_n \bmod N = Node_{n-1}
\end{align*}
$$

Where,

`key`: Request ID or IP.

`H`: Hash function result.

`N`: Total number of nodes.

`Node`: The node where the request will be routed.

The problem with this is if we add or remove a node, it will cause `N` to change, meaning our mapping strategy will break as the same requests will now map to a different server. As a consequence, the majority of requests will need to be redistributed which is very inefficient.

We want to uniformly distribute requests among different nodes such that we should be able to add or remove nodes with minimal effort. Hence, we need a distribution scheme that does not depend directly on the number of nodes (or servers), so that, when adding or removing nodes, the number of keys that need to be relocated is minimized.

Consistent hashing solves this horizontal scalability problem by ensuring that every time we scale up or down, we do not have to re-arrange all the keys or touch all the servers.

Now that we understand the problem, let's discuss consistent hashing in detail.

## How does it work

Consistent Hashing is a distributed hashing scheme that operates independently of the number of nodes in a distributed hash table by assigning them a position on an abstract circle, or hash ring. This allows servers and objects to scale without affecting the overall system.

![consistent-hashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/consistent-hashing/consistent-hashing.png)

Using consistent hashing, only `K/N` data would require re-distributing.

$$
R = K/N
$$

Where,

`R`: Data that would require re-distribution.

`K`: Number of partition keys.

`N`: Number of nodes.

The output of the hash function is a range let's say `0...m-1` which we can represent on our hash ring. We hash the requests and distribute them on the ring depending on what the output was. Similarly, we also hash the node and distribute them on the same ring as well.

$$
\begin{align*}
& Hash(key_1) = P_1 \\
& Hash(key_2) = P_2 \\
& Hash(key_3) = P_3 \\
& ... \\
& Hash(key_n) = P_{m-1}
\end{align*}
$$

Where,

`key`: Request/Node ID or IP.

`P`: Position on the hash ring.

`m`: Total range of the hash ring.

Now, when the request comes in we can simply route it to the closest node in a clockwise (can be counterclockwise as well) manner. This means that if a new node is added or removed, we can use the nearest node and only a _fraction_ of the requests need to be re-routed.

In theory, consistent hashing should distribute the load evenly however it doesn't happen in practice. Usually, the load distribution is uneven and one server may end up handling the majority of the request becoming a _hotspot_, essentially a bottleneck for the system. We can fix this by adding extra nodes but that can be expensive.

Let's see how we can address these issues.

## Virtual Nodes

In order to ensure a more evenly distributed load, we can introduce the idea of a virtual node, sometimes also referred to as a VNode.

Instead of assigning a single position to a node, the hash range is divided into multiple smaller ranges, and each physical node is assigned several of these smaller ranges. Each of these subranges is considered a VNode. Hence, virtual nodes are basically existing physical nodes mapped multiple times across the hash ring to minimize changes to a node's assigned range.

![virtual-nodes](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/consistent-hashing/virtual-nodes.png)

For this, we can use `k` number of hash functions.

$$
\begin{align*}
& Hash_1(key_1) = P_1 \\
& Hash_2(key_2) = P_2 \\
& Hash_3(key_3) = P_3 \\
& . . . \\
& Hash_k(key_n) = P_{m-1}
\end{align*}
$$

Where,

`key`: Request/Node ID or IP.

`k`: Number of hash functions.

`P`: Position on the hash ring.

`m`: Total range of the hash ring.

As VNodes help spread the load more evenly across the physical nodes on the cluster by diving the hash ranges into smaller subranges, this speeds up the re-balancing process after adding or removing nodes. This also helps us reduce the probability of hotspots.

## Data replication

To ensure high availability and durability, consistent hashing replicates each data item on multiple `N` nodes in the system where the value `N` is equivalent to the _replication factor_.

The replication factor is the number of nodes that will receive the copy of the same data. In eventually consistent systems, this is done asynchronously.

## Advantages

Let's look at some advantages of consistent hashing:

- Makes rapid scaling up and down more predictable.
- Facilitates partitioning and replication across nodes.
- Enables scalability and availability.
- Reduces hotspots.

## Disadvantages

Below are some disadvantages of consistent hashing:

- Increases complexity.
- Cascading failures.
- Load distribution can still be uneven.
- Key management can be expensive when nodes transiently fail.

## Examples

Let's look at some examples where consistent hashing is used:

- Data partitioning in [Apache Cassandra](https://cassandra.apache.org).
- Load distribution across multiple storage hosts in [Amazon DynamoDB](https://aws.amazon.com/dynamodb).

# Database Federation

Federation (or functional partitioning) splits up databases by function. The federation architecture makes several distinct physical databases appear as one logical database to end-users.

All of the components in a federation are tied together by one or more federal schemas that express the commonality of data throughout the federation. These federated schemas are used to specify the information that can be shared by the federation components and to provide a common basis for communication among them.

![database-federation](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-II/database-federation/database-federation.png)

Federation also provides a cohesive, unified view of data derived from multiple sources. The data sources for federated systems can include databases and various other forms of structured and unstructured data.

## Characteristics

Let's look at some key characteristics of a federated database:

- **Transparency**: Federated database masks user differences and implementations of underlying data sources. Therefore, the users do not need to be aware of where the data is stored.
- **Heterogeneity**: Data sources can differ in many ways. A federated database system can handle different hardware, network protocols, data models, etc.
- **Extensibility**: New sources may be needed to meet the changing needs of the business. A good federated database system needs to make it easy to add new sources.
- **Autonomy**: A Federated database does not change existing data sources, interfaces should remain the same.
- **Data integration**: A federated database can integrate data from different protocols, database management systems, etc.

## Advantages

Here are some advantages of federated databases:

- Flexible data sharing.
- Autonomy among the database components.
- Access heterogeneous data in a unified way.
- No tight coupling of applications with legacy databases.

## Disadvantages

Below are some disadvantages of federated databases:

- Adds more hardware and additional complexity.
- Joining data from two databases is complex.
- Dependence on autonomous data sources.
- Query performance and scalability.

# N-tier architecture

N-tier architecture divides an application into logical layers and physical tiers. Layers are a way to separate responsibilities and manage dependencies. Each layer has a specific responsibility. A higher layer can use services in a lower layer, but not the other way around.

![n-tier-architecture](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/n-tier-architecture/n-tier-architecture.png)

Tiers are physically separated, running on separate machines. A tier can call to another tier directly, or use asynchronous messaging. Although each layer might be hosted in its own tier, that's not required. Several layers might be hosted on the same tier. Physically separating the tiers improves scalability and resiliency and adds latency from the additional network communication.

An N-tier architecture can be of two types:

- In a closed layer architecture, a layer can only call the next layer immediately down.
- In an open layer architecture, a layer can call any of the layers below it.

A closed-layer architecture limits the dependencies between layers. However, it might create unnecessary network traffic, if one layer simply passes requests along to the next layer.

## Types of N-Tier architectures

Let's look at some examples of N-Tier architecture:

### 3-Tier architecture

3-Tier is widely used and consists of the following different layers:

- **Presentation layer**: Handles user interactions with the application.
- **Business Logic layer**: Accepts the data from the application layer, validates it as per business logic and passes it to the data layer.
- **Data Access layer**: Receives the data from the business layer and performs the necessary operation on the database.

### 2-Tier architecture

In this architecture, the presentation layer runs on the client and communicates with a data store. There is no business logic layer or immediate layer between client and server.

### Single Tier or 1-Tier architecture

It is the simplest one as it is equivalent to running the application on a personal computer. All of the required components for an application to run are on a single application or server.

## Advantages

Here are some advantages of using N-tier architecture:

- Can improve availability.
- Better security as layers can behave like a firewall.
- Separate tiers allow us to scale them as needed.
- Improve maintenance as different people can manage different tiers.

## Disadvantages

Below are some disadvantages of N-tier architecture:

- Increased complexity of the system as a whole.
- Increased network latency as the number of tiers increases.
- Expensive as every tier will have its own hardware cost.
- Difficult to manage network security.

# Message Brokers

A message broker is a software that enables applications, systems, and services to communicate with each other and exchange information. The message broker does this by translating messages between formal messaging protocols. This allows interdependent services to _"talk"_ with one another directly, even if they were written in different languages or implemented on different platforms.

![message-broker](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/message-brokers/message-broker.png)

Message brokers can validate, store, route, and deliver messages to the appropriate destinations. They serve as intermediaries between other applications, allowing senders to issue messages without knowing where the receivers are, whether or not they are active, or how many of them there are. This facilitates the decoupling of processes and services within systems.

## Models

Message brokers offer two basic message distribution patterns or messaging styles:

- **[Point-to-Point messaging](https://karanpratapsingh.com/courses/system-design/message-queues)**: This is the distribution pattern utilized in message queues with a one-to-one relationship between the message's sender and receiver.
- **[Publish-subscribe messaging](https://karanpratapsingh.com/courses/system-design/publish-subscribe)**: In this message distribution pattern, often referred to as _"pub/sub"_, the producer of each message publishes it to a topic, and multiple message consumers subscribe to topics from which they want to receive messages.

_We will discuss these messaging patterns in detail in the later tutorials._

## Message brokers vs Event streaming

Message brokers can support two or more messaging patterns, including message queues and pub/sub, while event streaming platforms only offer pub/sub-style distribution patterns. Designed for use with high volumes of messages, event streaming platforms are readily scalable. They're capable of ordering streams of records into categories called _topics_ and storing them for a predetermined amount of time. Unlike message brokers, however, event streaming platforms cannot guarantee message delivery or track which consumers have received the messages.

Event streaming platforms offer more scalability than message brokers but fewer features that ensure fault tolerance like message resending, as well as more limited message routing and queueing capabilities.

## Message brokers vs Enterprise Service Bus (ESB)

[Enterprise Service Bus (ESB)](https://karanpratapsingh.com/courses/system-design/enterprise-service-bus) infrastructure is complex and can be challenging to integrate and expensive to maintain. It's difficult to troubleshoot them when problems occur in production environments, they're not easy to scale, and updating is tedious.

Whereas message brokers are a _"lightweight"_ alternative to ESBs that provide similar functionality, a mechanism for inter-service communication, at a lower cost. They're well-suited for use in the [microservices architectures](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) that have become more prevalent as ESBs have fallen out of favor.

## Examples

Here are some commonly used message brokers:

- [NATS](https://nats.io)
- [Apache Kafka](https://kafka.apache.org)
- [RabbitMQ](https://www.rabbitmq.com)
- [ActiveMQ](https://activemq.apache.org)

# Message Queues

A message queue is a form of service-to-service communication that facilitates asynchronous communication. It asynchronously receives messages from producers and sends them to consumers.

Queues are used to effectively manage requests in large-scale distributed systems. In small systems with minimal processing loads and small databases, writes can be predictably fast. However, in more complex and large systems writes can take an almost non-deterministic amount of time.

![message-queue](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/message-queues/message-queue.png)

## Working

Messages are stored in the queue until they are processed and deleted. Each message is processed only once by a single consumer. Here's how it works:

- A producer publishes a job to the queue, then notifies the user of the job status.
- A consumer picks up the job from the queue, processes it, then signals that the job is complete.

## Advantages

Let's discuss some advantages of using a message queue:

- **Scalability**: Message queues make it possible to scale precisely where we need to. When workloads peak, multiple instances of our application can add all requests to the queue without the risk of collision.
- **Decoupling**: Message queues remove dependencies between components and significantly simplify the implementation of decoupled applications.
- **Performance**: Message queues enable asynchronous communication, which means that the endpoints that are producing and consuming messages interact with the queue, not each other. Producers can add requests to the queue without waiting for them to be processed.
- **Reliability**: Queues make our data persistent, and reduce the errors that happen when different parts of our system go offline.

## Features

Now, let's discuss some desired features of message queues:

### Push or Pull Delivery

Most message queues provide both push and pull options for retrieving messages. Pull means continuously querying the queue for new messages. Push means that a consumer is notified when a message is available. We can also use long-polling to allow pulls to wait a specified amount of time for new messages to arrive.

### FIFO (First-In-First-Out) Queues

In these queues, the oldest (or first) entry, sometimes called the _"head"_ of the queue, is processed first.

### Schedule or Delay Delivery

Many message queues support setting a specific delivery time for a message. If we need to have a common delay for all messages, we can set up a delay queue.

### At-Least-Once Delivery

Message queues may store multiple copies of messages for redundancy and high availability, and resend messages in the event of communication failures or errors to ensure they are delivered at least once.

### Exactly-Once Delivery

When duplicates can't be tolerated, FIFO (first-in-first-out) message queues will make sure that each message is delivered exactly once (and only once) by filtering out duplicates automatically.

### Dead-letter Queues

A dead-letter queue is a queue to which other queues can send messages that can't be processed successfully. This makes it easy to set them aside for further inspection without blocking the queue processing or spending CPU cycles on a message that might never be consumed successfully.

### Ordering

Most message queues provide best-effort ordering which ensures that messages are generally delivered in the same order as they're sent and that a message is delivered at least once.

### Poison-pill Messages

Poison pills are special messages that can be received, but not processed. They are a mechanism used in order to signal a consumer to end its work so it is no longer waiting for new inputs, and are similar to closing a socket in a client/server model.

### Security

Message queues will authenticate applications that try to access the queue, this allows us to encrypt messages over the network as well as in the queue itself.

### Task Queues

Tasks queues receive tasks and their related data, run them, then deliver their results. They can support scheduling and can be used to run computationally-intensive jobs in the background.

## Backpressure

If queues start to grow significantly, the queue size can become larger than memory, resulting in cache misses, disk reads, and even slower performance. Backpressure can help by limiting the queue size, thereby maintaining a high throughput rate and good response times for jobs already in the queue. Once the queue fills up, clients get a server busy or HTTP 503 status code to try again later. Clients can retry the request at a later time, perhaps with [exponential backoff](https://en.wikipedia.org/wiki/Exponential_backoff) strategy.

## Examples

Following are some widely used message queues:

- [Amazon SQS](https://aws.amazon.com/sqs)
- [RabbitMQ](https://www.rabbitmq.com)
- [ActiveMQ](https://activemq.apache.org)
- [ZeroMQ](https://zeromq.org)

# Publish-Subscribe

Similar to a message queue, publish-subscribe is also a form of service-to-service communication that facilitates asynchronous communication. In a pub/sub model, any message published to a topic is pushed immediately to all the subscribers of the topic.

![publish-subscribe](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/publish-subscribe/publish-subscribe.png)

The subscribers to the message topic often perform different functions, and can each do something different with the message in parallel. The publisher doesn't need to know who is using the information that it is broadcasting, and the subscribers don't need to know where the message comes from. This style of messaging is a bit different than message queues, where the component that sends the message often knows the destination it is sending to.

## Working

Unlike message queues, which batch messages until they are retrieved, message topics transfer messages with little or no queuing and push them out immediately to all subscribers. Here's how it works:

- A message topic provides a lightweight mechanism to broadcast asynchronous event notifications and endpoints that allow software components to connect to the topic in order to send and receive those messages.
- To broadcast a message, a component called a _publisher_ simply pushes a message to the topic.
- All components that subscribe to the topic (known as _subscribers_) will receive every message that was broadcasted.

## Advantages

Let's discuss some advantages of using publish-subscribe:

- **Eliminate Polling**: Message topics allow instantaneous, push-based delivery, eliminating the need for message consumers to periodically check or _"poll"_ for new information and updates. This promotes faster response time and reduces the delivery latency which can be particularly problematic in systems where delays cannot be tolerated.
- **Dynamic Targeting**: Pub/Sub makes the discovery of services easier, more natural, and less error-prone. Instead of maintaining a roster of peers where an application can send messages, a publisher will simply post messages to a topic. Then, any interested party will subscribe its endpoint to the topic, and start receiving these messages. Subscribers can change, upgrade, multiply or disappear and the system dynamically adjusts.
- **Decoupled and Independent Scaling**: Publishers and subscribers are decoupled and work independently from each other, which allows us to develop and scale them independently.
- **Simplify Communication**: The Publish-Subscribe model reduces complexity by removing all the point-to-point connections with a single connection to a message topic, which will manage subscriptions and decide what messages should be delivered to which endpoints.

## Features

Now, let's discuss some desired features of publish-subscribe:

### Push Delivery

Pub/Sub messaging instantly pushes asynchronous event notifications when messages are published to the message topic. Subscribers are notified when a message is available.

### Multiple Delivery Protocols

In the Publish-Subscribe model, topics can typically connect to multiple types of endpoints, such as message queues, serverless functions, HTTP servers, etc.

### Fanout

This scenario happens when a message is sent to a topic and then replicated and pushed to multiple endpoints. Fanout provides asynchronous event notifications which in turn allows for parallel processing.

### Filtering

This feature empowers the subscriber to create a message filtering policy so that it will only get the notifications it is interested in, as opposed to receiving every single message posted to the topic.

### Durability

Pub/Sub messaging services often provide very high durability, and at least once delivery, by storing copies of the same message on multiple servers.

### Security

Message topics authenticate applications that try to publish content, this allows us to use encrypted endpoints and encrypt messages in transit over the network.

## Examples

Here are some technologies commonly used for publish-subscribe:

- [Amazon SNS](https://aws.amazon.com/sns)
- [Google Pub/Sub](https://cloud.google.com/pubsub)

# Enterprise Service Bus (ESB)

An Enterprise Service Bus (ESB) is an architectural pattern whereby a centralized software component performs integrations between applications. It performs transformations of data models, handles connectivity, performs message routing, converts communication protocols, and potentially manages the composition of multiple requests. The ESB can make these integrations and transformations available as a service interface for reuse by new applications.

![enterprise-service-bus](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/enterprise-service-bus/enterprise-service-bus.png)

## Advantages

In theory, a centralized ESB offers the potential to standardize and dramatically simplify communication, messaging, and integration between services across the enterprise. Here are some advantages of using an ESB:

- **Improved developer productivity**: Enables developers to incorporate new technologies into one part of an application without touching the rest of the application.
- **Simpler, more cost-effective scalability**: Components can be scaled independently of others.
- **Greater resilience**: Failure of one component does not impact the others, and each microservice can adhere to its own availability requirements without risking the availability of other components in the system.

## Disadvantages

While ESBs were deployed successfully in many organizations, in many other organizations the ESB came to be seen as a bottleneck. Here are some disadvantages of using an ESB:

- Making changes or enhancements to one integration could destabilize others who use that same integration.
- A single point of failure can bring down all communications.
- Updates to the ESB often impact existing integrations, so there is significant testing required to perform any update.
- ESB is centrally managed which makes cross-team collaboration challenging.
- High configuration and maintenance complexity.

## Examples

Below are some widely used Enterprise Service Bus (ESB) technologies:

- [Azure Service Bus](https://azure.microsoft.com/en-in/services/service-bus)
- [IBM App Connect](https://www.ibm.com/in-en/cloud/app-connect)
- [Apache Camel](https://camel.apache.org)
- [Fuse ESB](https://www.redhat.com/en/technologies/jboss-middleware/fuse)

# Monoliths and Microservices

## Monoliths

A monolith is a self-contained and independent application. It is built as a single unit and is responsible for not just a particular task, but can perform every step needed to satisfy a business need.

![monolith](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/monoliths-microservices/monolith.png)

### Advantages

Following are some advantages of monoliths:

- Simple to develop or debug.
- Fast and reliable communication.
- Easy monitoring and testing.
- Supports ACID transactions.

### Disadvantages

Some common disadvantages of monoliths are:

- Maintenance becomes hard as the codebase grows.
- Tightly coupled application, hard to extend.
- Requires commitment to a particular technology stack.
- On each update, the entire application is redeployed.
- Reduced reliability as a single bug can bring down the entire system.
- Difficult to scale or adopt new technologies.

## Modular monoliths

A Modular Monolith is an approach where we build and deploy a single application (that's the _Monolith_ part), but we build it in a way that breaks up the code into independent modules for each of the features needed in our application.

This approach reduces the dependencies of a module in such as way that we can enhance or change a module without affecting other modules. When done right, this can be really beneficial in the long term as it reduces the complexity that comes with maintaining a monolith as the system grows.

## Microservices

A microservices architecture consists of a collection of small, autonomous services where each service is self-contained and should implement a single business capability within a bounded context. A bounded context is a natural division of business logic that provides an explicit boundary within which a domain model exists.

![microservices](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/monoliths-microservices/microservices.png)

Each service has a separate codebase, which can be managed by a small development team. Services can be deployed independently and a team can update an existing service without rebuilding and redeploying the entire application.

Services are responsible for persisting their own data or external state (database per service). This differs from the traditional model, where a separate data layer handles data persistence.

### Characteristics

The microservices architecture style has the following characteristics:

- **Loosely coupled**: Services should be loosely coupled so that they can be independently deployed and scaled. This will lead to the decentralization of development teams and thus, enabling them to develop and deploy faster with minimal constraints and operational dependencies.
- **Small but focused**: It's about scope and responsibilities and not size, a service should be focused on a specific problem. Basically, _"It does one thing and does it well"_. Ideally, they can be independent of the underlying architecture.
- **Built for businesses**: The microservices architecture is usually organized around business capabilities and priorities.
- **Resilience & Fault tolerance**: Services should be designed in such a way that they still function in case of failure or errors. In environments with independently deployable services, failure tolerance is of the highest importance.
- **Highly maintainable**: Service should be easy to maintain and test because services that cannot be maintained will be rewritten.

### Advantages

Here are some advantages of microservices architecture:

- Loosely coupled services.
- Services can be deployed independently.
- Highly agile for multiple development teams.
- Improves fault tolerance and data isolation.
- Better scalability as each service can be scaled independently.
- Eliminates any long-term commitment to a particular technology stack.

### Disadvantages

Microservices architecture brings its own set of challenges:

- Complexity of a distributed system.
- Testing is more difficult.
- Expensive to maintain (individual servers, databases, etc.).
- Inter-service communication has its own challenges.
- Data integrity and consistency.
- Network congestion and latency.

### Best practices

Let's discuss some microservices best practices:

- Model services around the business domain.
- Services should have loose coupling and high functional cohesion.
- Isolate failures and use resiliency strategies to prevent failures within a service from cascading.
- Services should only communicate through well-designed APIs. Avoid leaking implementation details.
- Data storage should be private to the service that owns the data
- Avoid coupling between services. Causes of coupling include shared database schemas and rigid communication protocols.
- Decentralize everything. Individual teams are responsible for designing and building services. Avoid sharing code or data schemas.
- Fail fast by using a [circuit breaker](https://karanpratapsingh.com/courses/system-design/circuit-breaker) to achieve fault tolerance.
- Ensure that the API changes are backward compatible.

### Pitfalls

Below are some common pitfalls of microservices architecture:

- Service boundaries are not based on the business domain.
- Underestimating how hard is to build a distributed system.
- Shared database or common dependencies between services.
- Lack of Business Alignment.
- Lack of clear ownership.
- Lack of idempotency.
- Trying to do everything [ACID instead of BASE](https://karanpratapsingh.com/courses/system-design/acid-and-base-consistency-models).
- Lack of design for fault tolerance may result in cascading failures.

## Beware of the distributed monolith

Distributed Monolith is a system that resembles the microservices architecture but is tightly coupled within itself like a monolithic application. Adopting microservices architecture comes with a lot of advantages. But while making one, there are good chances that we might end up with a distributed monolith.

Our microservices are just a distributed monolith if any of these apply to it:

- Requires low latency communication.
- Services don't scale easily.
- Dependency between services.
- Sharing the same resources such as databases.
- Tightly coupled systems.

One of the primary reasons to build an application using microservices architecture is to have scalability. Therefore, microservices should have loosely coupled services which enable every service to be independent. The distributed monolith architecture takes this away and causes most components to depend on one another, increasing design complexity.

## Microservices vs Service-oriented architecture (SOA)

You might have seen _Service-oriented architecture (SOA)_ mentioned around the internet, sometimes even interchangeably with microservices, but they are different from each other and the main distinction between the two approaches comes down to _scope_.

Service-oriented architecture (SOA) defines a way to make software components reusable via service interfaces. These interfaces utilize common communication standards and focus on maximizing application service reusability whereas microservices are built as a collection of various smallest independent service units focused on team autonomy and decoupling.

## Why you don't need microservices

![architecture-range](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/monoliths-microservices/architecture-range.png)

So, you might be wondering, monoliths seem like a bad idea to begin with, why would anyone use that?

Well, it depends. While each approach has its own advantages and disadvantages, it is advised to start with a monolith when building a new system. It is important to understand, that microservices are not a silver bullet, instead, they solve an organizational problem. Microservices architecture is about your organizational priorities and team as much as it's about technology.

Before making the decision to move to microservices architecture, you need to ask yourself questions like:

- _"Is the team too large to work effectively on a shared codebase?"_
- _"Are teams blocked on other teams?"_
- _"Does microservices deliver clear business value for us?"_
- _"Is my business mature enough to use microservices?"_
- _"Is our current architecture limiting us with communication overhead?"_

If your application does not require to be broken down into microservices, you don't need this. There is no absolute necessity that all applications should be broken down into microservices.

We frequently draw inspiration from companies such as Netflix and their use of microservices, but we overlook the fact that we are not Netflix. They went through a lot of iterations and models before they had a market-ready solution, and this architecture became acceptable for them when they identified and solved the problem they were trying to tackle.

That's why it's essential to understand in-depth if your business _actually_ needs microservices. What I'm trying to say is microservices are solutions to complex concerns and if your business doesn't have complex issues, you don't need them.

# Event-Driven Architecture (EDA)

Event-Driven Architecture (EDA) is about using events as a way to communicate within a system. Generally, leveraging a message broker to publish and consume events asynchronously. The publisher is unaware of who is consuming an event and the consumers are unaware of each other. Event-Driven Architecture is simply a way of achieving loose coupling between services within a system.

## What is an event?

An event is a data point that represents state changes in a system. It doesn't specify what should happen and how the change should modify the system, it only notifies the system of a particular state change. When a user makes an action, they trigger an event.

## Components

Event-driven architectures have three key components:

- **Event producers**: Publishes an event to the router.
- **Event routers**: Filters and pushes the events to consumers.
- **Event consumers**: Uses events to reflect changes in the system.

![event-driven-architecture](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/event-driven-architecture/event-driven-architecture.png)

_Note: Dots in the diagram represents different events in the system._

## Patterns

There are several ways to implement the event-driven architecture, and which method we use depends on the use case but here are some common examples:

- [Sagas](https://karanpratapsingh.com/courses/system-design/distributed-transactions#sagas)
- [Publish-Subscribe](https://karanpratapsingh.com/courses/system-design/publish-subscribe)
- [Event Sourcing](https://karanpratapsingh.com/courses/system-design/event-sourcing)
- [Command and Query Responsibility Segregation (CQRS)](https://karanpratapsingh.com/courses/system-design/command-and-query-responsibility-segregation)

_Note: Each of these methods is discussed separately._

## Advantages

Let's discuss some advantages:

- Decoupled producers and consumers.
- Highly scalable and distributed.
- Easy to add new consumers.
- Improves agility.

## Challenges

Here are some challenges of event-drive architecture:

- Guaranteed delivery.
- Error handling is difficult.
- Event-driven systems are complex in general.
- Exactly once, in-order processing of events.

## Use cases

Below are some common use cases where event-driven architectures are beneficial:

- Metadata and metrics.
- Server and security logs.
- Integrating heterogeneous systems.
- Fanout and parallel processing.

## Examples

Here are some widely used technologies for implementing event-driven architectures:

- [NATS](https://nats.io)
- [Apache Kafka](https://kafka.apache.org)
- [Amazon EventBridge](https://aws.amazon.com/eventbridge)
- [Amazon SNS](https://aws.amazon.com/sns)
- [Google PubSub](https://cloud.google.com/pubsub)

# Event Sourcing

Instead of storing just the current state of the data in a domain, use an append-only store to record the full series of actions taken on that data. The store acts as the system of record and can be used to materialize the domain objects.

![event-sourcing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/event-sourcing/event-sourcing.png)

This can simplify tasks in complex domains, by avoiding the need to synchronize the data model and the business domain, while improving performance, scalability, and responsiveness. It can also provide consistency for transactional data, and maintain full audit trails and history that can enable compensating actions.

## Event sourcing vs Event-Driven Architecture (EDA)

Event sourcing is seemingly constantly being confused with [Event-driven Architecture (EDA)](https://karanpratapsingh.com/courses/system-design/event-driven-architecture). Event-driven architecture is about using events to communicate between service boundaries. Generally, leveraging a message broker to publish and consume events asynchronously within other boundaries.

Whereas, event sourcing is about using events as a state, which is a different approach to storing data. Rather than storing the current state, we're instead going to be storing events. Also, event sourcing is one of the several patterns to implement an event-driven architecture.

## Advantages

Let's discuss some advantages of using event sourcing:

- Excellent for real-time data reporting.
- Great for fail-safety, data can be reconstituted from the event store.
- Extremely flexible, any type of message can be stored.
- Preferred way of achieving audit logs functionality for high compliance systems.

## Disadvantages

Following are the disadvantages of event sourcing:

- Requires an extremely efficient network infrastructure.
- Requires a reliable way to control message formats, such as a schema registry.
- Different events will contain different payloads.

# Command and Query Responsibility Segregation (CQRS)

Command Query Responsibility Segregation (CQRS) is an architectural pattern that divides a system's actions into commands and queries. It was first described by [Greg Young](https://twitter.com/gregyoung).

In CQRS, a _command_ is an instruction, a directive to perform a specific task. It is an intention to change something and doesn't return a value, only an indication of success or failure. And, a _query_ is a request for information that doesn't change the system's state or cause any side effects.

![command-and-query-responsibility-segregation](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/command-and-query-responsibility-segregation/command-and-query-responsibility-segregation.png)

The core principle of CQRS is the separation of commands and queries. They perform fundamentally different roles within a system, and separating them means that each can be optimized as needed, which distributed systems can really benefit from.

## CQRS with Event Sourcing

The CQRS pattern is often used along with the Event Sourcing pattern. CQRS-based systems use separate read and write data models, each tailored to relevant tasks and often located in physically separate stores.

When used with the Event Sourcing pattern, the store of events is the write model and is the official source of information. The read model of a CQRS-based system provides materialized views of the data, typically as highly denormalized views.

## Advantages

Let's discuss some advantages of CQRS:

- Allows independent scaling of read and write workloads.
- Easier scaling, optimizations, and architectural changes.
- Closer to business logic with loose coupling.
- The application can avoid complex joins when querying.
- Clear boundaries between the system behavior.

## Disadvantages

Below are some disadvantages of CQRS:

- More complex application design.
- Message failures or duplicate messages can occur.
- Dealing with eventual consistency is a challenge.
- Increased system maintenance efforts.

## Use cases

Here are some scenarios where CQRS will be helpful:

- The performance of data reads must be fine-tuned separately from the performance of data writes.
- The system is expected to evolve over time and might contain multiple versions of the model, or where business rules change regularly.
- Integration with other systems, especially in combination with event sourcing, where the temporal failure of one subsystem shouldn't affect the availability of the others.
- Better security to ensure that only the right domain entities are performing writes on the data.

# API Gateway

The API Gateway is an API management tool that sits between a client and a collection of backend services. It is a single entry point into a system that encapsulates the internal system architecture and provides an API that is tailored to each client. It also has other responsibilities such as authentication, monitoring, load balancing, caching, throttling, logging, etc.

![api-gateway](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/api-gateway/api-gateway.png)

## Why do we need an API Gateway?

The granularity of APIs provided by microservices is often different than what a client needs. Microservices typically provide fine-grained APIs, which means that clients need to interact with multiple services. Hence, an API gateway can provide a single entry point for all clients with some additional features and better management.

## Features

Below are some desired features of an API Gateway:

- Authentication and Authorization
- [Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery)
- [Reverse Proxy](https://karanpratapsingh.com/courses/system-design/proxy#reverse-proxy)
- [Caching](https://karanpratapsingh.com/courses/system-design/caching)
- Security
- Retry and [Circuit breaking](https://karanpratapsingh.com/courses/system-design/circuit-breaker)
- [Load balancing](https://karanpratapsingh.com/courses/system-design/load-balancing)
- Logging, Tracing
- API composition
- [Rate limiting](https://karanpratapsingh.com/courses/system-design/rate-limiting) and throttling
- Versioning
- Routing
- IP whitelisting or blacklisting

## Advantages

Let's look at some advantages of using an API Gateway:

- Encapsulates the internal structure of an API.
- Provides a centralized view of the API.
- Simplifies the client code.
- Monitoring, analytics, tracing, and other such features.

## Disadvantages

Here are some possible disadvantages of an API Gateway:

- Possible single point of failure.
- Might impact performance.
- Can become a bottleneck if not scaled properly.
- Configuration can be challenging.

## Backend For Frontend (BFF) pattern

In the Backend For Frontend (BFF) pattern, we create separate backend services to be consumed by specific frontend applications or interfaces. This pattern is useful when we want to avoid customizing a single backend for multiple interfaces. This pattern was first described by [Sam Newman](https://samnewman.io).

Also, sometimes the output of data returned by the microservices to the front end is not in the exact format or filtered as needed by the front end. To solve this issue, the frontend should have some logic to reformat the data, and therefore, we can use BFF to shift some of this logic to the intermediate layer.

![backend-for-frontend](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/api-gateway/backend-for-frontend.png)

The primary function of the backend for the frontend pattern is to get the required data from the appropriate service, format the data, and sent it to the frontend.

_[GraphQL](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#graphql) performs really well as a backend for frontend (BFF)._

### When to use this pattern?

We should consider using a Backend For Frontend (BFF) pattern when:

- A shared or general purpose backend service must be maintained with significant development overhead.
- We want to optimize the backend for the requirements of a specific client.
- Customizations are made to a general-purpose backend to accommodate multiple interfaces.

## Examples

Following are some widely used gateways technologies:

- [Amazon API Gateway](https://aws.amazon.com/api-gateway)
- [Apigee API Gateway](https://cloud.google.com/apigee)
- [Azure API Gateway](https://azure.microsoft.com/en-in/services/api-management)
- [Kong API Gateway](https://konghq.com/kong)

# REST, GraphQL, gRPC

A good API design is always a crucial part of any system. But it is also important to pick the right API technology. So, in this tutorial, we will briefly discuss different API technologies such as REST, GraphQL, and gRPC.

## What's an API?

Before we even get into API technologies, let's first understand what is an API.

API stands for Application Programming Interface. It is a set of definitions and protocols for building and integrating application software. It's sometimes referred to as a contract between an information provider and an information user establishing the content required from the producer and the content required by the consumer.

In other words, if you want to interact with a computer or system to retrieve information or perform a function, an API helps you communicate what you want to that system so it can understand and complete the request.

## REST

A [REST API](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm) (also known as RESTful API) is an application programming interface that conforms to the constraints of REST architectural style and allows for interaction with RESTful web services. REST stands for Representational State Transfer and it was first introduced by [Roy Fielding](https://roy.gbiv.com) in the year 2000.

_In REST API, the fundamental unit is a resource._

### Concepts

Let's discuss some concepts of a RESTful API.

**Constraints**

In order for an API to be considered _RESTful_, it has to conform to these architectural constraints:

- **Uniform Interface**: There should be a uniform way of interacting with a given server.
- **Client-Server**: A client-server architecture managed through HTTP.
- **Stateless**: No client context shall be stored on the server between requests.
- **Cacheable**: Every response should include whether the response is cacheable or not and for how much duration responses can be cached at the client-side.
- **Layered system**: An application architecture needs to be composed of multiple layers.
- **Code on demand**: Return executable code to support a part of your application. _(optional)_

**HTTP Verbs**

HTTP defines a set of request methods to indicate the desired action to be performed for a given resource. Although they can also be nouns, these request methods are sometimes referred to as _HTTP verbs_. Each of them implements a different semantic, but some common features are shared by a group of them.

Below are some commonly used HTTP verbs:

- **GET**: Request a representation of the specified resource.
- **HEAD**: Response is identical to a `GET` request, but without the response body.
- **POST**: Submits an entity to the specified resource, often causing a change in state or side effects on the server.
- **PUT**: Replaces all current representations of the target resource with the request payload.
- **DELETE**: Deletes the specified resource.
- **PATCH**: Applies partial modifications to a resource.

**HTTP response codes**

[HTTP response status codes](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes) indicate whether a specific HTTP request has been successfully completed.

There are five classes defined by the standard:

- 1xx - Informational responses.
- 2xx - Successful responses.
- 3xx - Redirection responses.
- 4xx - Client error responses.
- 5xx - Server error responses.

For example, HTTP 200 means that the request was successful.

### Advantages

Let's discuss some advantages of REST API:

- Simple and easy to understand.
- Flexible and portable.
- Good caching support.
- Client and server are decoupled.

### Disadvantages

Let's discuss some disadvantages of REST API:

- Over-fetching of data.
- Sometimes multiple round trips to the server are required.

### Use cases

REST APIs are pretty much used universally and are the default standard for designing APIs. Overall REST APIs are quite flexible and can fit almost all scenarios.

### Example

Here's an example usage of a REST API that operates on a **users** resource.

| URI           | HTTP verb | Description         |
| ------------- | --------- | ------------------- |
| /users        | GET       | Get all users       |
| /users/\{id\} | GET       | Get a user by id    |
| /users        | POST      | Add a new user      |
| /users/\{id\} | PATCH     | Update a user by id |
| /users/\{id\} | DELETE    | Delete a user by id |

_There is so much more to learn when it comes to REST APIs, I will highly recommend looking into [Hypermedia as the Engine of Application State (HATEOAS)](https://en.wikipedia.org/wiki/HATEOAS)._

## GraphQL

[GraphQL](https://graphql.org) is a query language and server-side runtime for APIs that prioritizes giving clients exactly the data they request and no more. It was developed by [Facebook](https://engineering.fb.com) and later open-sourced in 2015.

GraphQL is designed to make APIs fast, flexible, and developer-friendly. Additionally, GraphQL gives API maintainers the flexibility to add or deprecate fields without impacting existing queries. Developers can build APIs with whatever methods they prefer, and the GraphQL specification will ensure they function in predictable ways to clients.

_In GraphQL, the fundamental unit is a query._

### Concepts

Let's briefly discuss some key concepts in GraphQL:

**Schema**

A GraphQL schema describes the functionality clients can utilize once they connect to the GraphQL server.

**Queries**

A query is a request made by the client. It can consist of fields and arguments for the query. The operation type of a query can also be a [mutation](https://graphql.org/learn/queries/#mutations) which provides a way to modify server-side data.

**Resolvers**

Resolver is a collection of functions that generate responses for a GraphQL query. In simple terms, a resolver acts as a GraphQL query handler.

### Advantages

Let's discuss some advantages of GraphQL:

- Eliminates over-fetching of data.
- Strongly defined schema.
- Code generation support.
- Payload optimization.

### Disadvantages

Let's discuss some disadvantages of GraphQL:

- Shifts complexity to server-side.
- Caching becomes hard.
- Versioning is ambiguous.
- N+1 problem.

### Use cases

GraphQL proves to be essential in the following scenarios:

- Reducing app bandwidth usage as we can query multiple resources in a single query.
- Rapid prototyping for complex systems.
- When we are working with a graph-like data model.

### Example

Here's a GraphQL schema that defines a `User` type and a `Query` type.

```graphql
type Query {
  getUser: User
}

type User {
  id: ID
  name: String
  city: String
  state: String
}
```

Using the above schema, the client can request the required fields easily without having to fetch the entire resource or guess what the API might return.

```graphql
{
  getUser {
    id
    name
    city
  }
}
```

This will give the following response to the client.

```json
{
  "getUser": {
    "id": 123,
    "name": "Karan",
    "city": "San Francisco"
  }
}
```

_Learn more about GraphQL at [graphql.org](https://graphql.org)._

## gRPC

[gRPC](https://grpc.io) is a modern open-source high-performance [Remote Procedure Call (RPC)](https://en.wikipedia.org/wiki/Remote_procedure_call) framework that can run in any environment. It can efficiently connect services in and across data centers with pluggable support for load balancing, tracing, health checking, authentication and much more.

### Concepts

Let's discuss some key concepts of gRPC.

**Protocol buffers**

Protocol buffers provide a language and platform-neutral extensible mechanism for serializing structured data in a forward and backward-compatible way. It's like JSON, except it's smaller and faster, and it generates native language bindings.

**Service definition**

Like many RPC systems, gRPC is based on the idea of defining a service and specifying the methods that can be called remotely with their parameters and return types. gRPC uses protocol buffers as the [Interface Definition Language (IDL)](https://en.wikipedia.org/wiki/Interface_description_language) for describing both the service interface and the structure of the payload messages.

### Advantages

Let's discuss some advantages of gRPC:

- Lightweight and efficient.
- High performance.
- Built-in code generation support.
- Bi-directional streaming.

### Disadvantages

Let's discuss some disadvantages of gRPC:

- Relatively new compared to REST and GraphQL.
- Limited browser support.
- Steeper learning curve.
- Not human readable.

### Use cases

Below are some good use cases for gRPC:

- Real-time communication via bi-directional streaming.
- Efficient inter-service communication in microservices.
- Low latency and high throughput communication.
- Polyglot environments.

### Example

Here's a basic example of a gRPC service defined in a `*.proto` file. Using this definition, we can easily code generate the `HelloService` service in the programming language of our choice.

```protobuf
service HelloService {
  rpc SayHello (HelloRequest) returns (HelloResponse);
}

message HelloRequest {
  string greeting = 1;
}

message HelloResponse {
  string reply = 1;
}
```

## REST vs GraphQL vs gRPC

Now that we know how these API designing techniques work, let's compare them based on the following parameters:

- Will it cause tight coupling?
- How _chatty_ (distinct API calls to get needed information) are the APIs?
- What's the performance like?
- How complex is it to integrate?
- How well does the caching work?
- Built-in tooling and code generation?
- What's API discoverability like?
- How easy is it to version APIs?

| Type    | Coupling | Chattiness | Performance | Complexity | Caching | Codegen | Discoverability | Versioning |
| ------- | -------- | ---------- | ----------- | ---------- | ------- | ------- | --------------- | ---------- |
| REST    | Low      | High       | Good        | Medium     | Great   | Bad     | Good            | Easy       |
| GraphQL | Medium   | Low        | Good        | High       | Custom  | Good    | Good            | Custom     |
| gRPC    | High     | Medium     | Great       | Low        | Custom  | Great   | Bad             | Hard       |

### Which API technology is better?

Well, the answer is none of them. There is no silver bullet as each of these technologies has its own advantages and disadvantages. Users only care about using our APIs in a consistent way, so make sure to focus on your domain and requirements when designing your API.

# Long polling, WebSockets, Server-Sent Events (SSE)

Web applications were initially developed around a client-server model, where the web client is always the initiator of transactions like requesting data from the server. Thus, there was no mechanism for the server to independently send, or push, data to the client without the client first making a request. Let's discuss some approaches to overcome this problem.

## Long polling

HTTP Long polling is a technique used to push information to a client as soon as possible from the server. As a result, the server does not have to wait for the client to send a request.

In Long polling, the server does not close the connection once it receives a request from the client. Instead, the server responds only if any new message is available or a timeout threshold is reached.

![long-polling](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/long-polling-websockets-server-sent-events/long-polling.png)

Once the client receives a response, it immediately sends a new request to the server to have a new pending connection to send data to the client, and the operation is repeated. With this approach, the server emulates a real-time server push feature.

### Working

Let's understand how long polling works:

1. The client makes an initial request and waits for a response.
2. The server receives the request and delays sending anything until an update is available.
3. Once an update is available, the response is sent to the client.
4. The client receives the response and makes a new request immediately or after some defined interval to establish a connection again.

### Advantages

Here are some advantages of long polling:

- Easy to implement, good for small-scale projects.
- Nearly universally supported.

### Disadvantages

A major downside of long polling is that it is usually not scalable. Below are some of the other reasons:

- Creates a new connection each time, which can be intensive on the server.
- Reliable message ordering can be an issue for multiple requests.
- Increased latency as the server needs to wait for a new request.

## WebSockets

WebSocket provides full-duplex communication channels over a single TCP connection. It is a persistent connection between a client and a server that both parties can use to start sending data at any time.

The client establishes a WebSocket connection through a process known as the WebSocket handshake. If the process succeeds, then the server and client can exchange data in both directions at any time. The WebSocket protocol enables the communication between a client and a server with lower overheads, facilitating real-time data transfer from and to the server.

![websockets](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/long-polling-websockets-server-sent-events/websockets.png)

This is made possible by providing a standardized way for the server to send content to the client without being asked and allowing for messages to be passed back and forth while keeping the connection open.

### Working

Let's understand how WebSockets work:

1. The client initiates a WebSocket handshake process by sending a request.
2. The request also contains an [HTTP Upgrade](https://en.wikipedia.org/wiki/HTTP/1.1_Upgrade_header) header that allows the request to switch to the WebSocket protocol (`ws://`).
3. The server sends a response to the client, acknowledging the WebSocket handshake request.
4. A WebSocket connection will be opened once the client receives a successful handshake response.
5. Now the client and server can start sending data in both directions allowing real-time communication.
6. The connection is closed once the server or the client decides to close the connection.

### Advantages

Below are some advantages of WebSockets:

- Full-duplex asynchronous messaging.
- Better origin-based security model.
- Lightweight for both client and server.

### Disadvantages

Let's discuss some disadvantages of WebSockets:

- Terminated connections aren't automatically recovered.
- Older browsers don't support WebSockets (becoming less relevant).

## Server-Sent Events (SSE)

Server-Sent Events (SSE) is a way of establishing long-term communication between client and server that enables the server to proactively push data to the client.

![server-sent-events](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-III/long-polling-websockets-server-sent-events/server-sent-events.png)

It is unidirectional, meaning once the client sends the request it can only receive the responses without the ability to send new requests over the same connection.

### Working

Let's understand how server-sent events work:

1. The client makes a request to the server.
2. The connection between client and server is established and it remains open.
3. The server sends responses or events to the client when new data is available.

### Advantages

- Simple to implement and use for both client and server.
- Supported by most browsers.
- No trouble with firewalls.

### Disadvantages

- Unidirectional nature can be limiting.
- Limitation for the maximum number of open connections.
- Does not support binary data.

# Geohashing and Quadtrees

## Geohashing

Geohashing is a [geocoding](https://en.wikipedia.org/wiki/Address_geocoding) method used to encode geographic coordinates such as latitude and longitude into short alphanumeric strings. It was created by [Gustavo Niemeyer](https://twitter.com/gniemeyer) in 2008.

For example, San Francisco with coordinates `37.7564, -122.4016` can be represented in geohash as `9q8yy9mf`.

### How does Geohashing work?

Geohash is a hierarchical spatial index that uses Base-32 alphabet encoding, the first character in a geohash identifies the initial location as one of the 32 cells. This cell will also contain 32 cells. This means that to represent a point, the world is recursively divided into smaller and smaller cells with each additional bit until the desired precision is attained. The precision factor also determines the size of the cell.

![geohashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/geohashing.png)

Geohashing guarantees that points are spatially closer if their Geohashes share a longer prefix which means the more characters in the string, the more precise the location. For example, geohashes `9q8yy9mf` and `9q8yy9vx` are spatially closer as they share the prefix `9q8yy9`.

Geohashing can also be used to provide a degree of anonymity as we don't need to expose the exact location of the user because depending on the length of the geohash we just know they are somewhere within an area.

The cell sizes of the geohashes of different lengths are as follows:

| Geohash length | Cell width | Cell height |
| -------------- | ---------- | ----------- |
| 1              | 5000 km    | 5000 km     |
| 2              | 1250 km    | 1250 km     |
| 3              | 156 km     | 156 km      |
| 4              | 39.1 km    | 19.5 km     |
| 5              | 4.89 km    | 4.89 km     |
| 6              | 1.22 km    | 0.61 km     |
| 7              | 153 m      | 153 m       |
| 8              | 38.2 m     | 19.1 m      |
| 9              | 4.77 m     | 4.77 m      |
| 10             | 1.19 m     | 0.596 m     |
| 11             | 149 mm     | 149 mm      |
| 12             | 37.2 mm    | 18.6 mm     |

### Use cases

Here are some common use cases for Geohashing:

- It is a simple way to represent and store a location in a database.
- It can also be shared on social media as URLs since it is easier to share, and remember than latitudes and longitudes.
- We can efficiently find the nearest neighbors of a point through very simple string comparisons and efficient searching of indexes.

### Examples

Geohashing is widely used and it is supported by popular databases.

- [MySQL](https://www.mysql.com)
- [Redis](http://redis.io)
- [Amazon DynamoDB](https://aws.amazon.com/dynamodb)
- [Google Cloud Firestore](https://cloud.google.com/firestore)

## Quadtrees

A quadtree is a tree data structure in which each internal node has exactly four children. They are often used to partition a two-dimensional space by recursively subdividing it into four quadrants or regions. Each child or leaf node stores spatial information. Quadtrees are the two-dimensional analog of [Octrees](https://en.wikipedia.org/wiki/Octree) which are used to partition three-dimensional space.

![quadtree](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree.png)

### Types of Quadtrees

Quadtrees may be classified according to the type of data they represent, including areas, points, lines, and curves. The following are common types of quadtrees:

- Point quadtrees
- Point-region (PR) quadtrees
- Polygonal map (PM) quadtrees
- Compressed quadtrees
- Edge quadtrees

### Why do we need Quadtrees?

Aren't latitudes and longitudes enough? Why do we need quadtrees? While in theory using latitude and longitude we can determine things such as how close points are to each other using [euclidean distance](https://en.wikipedia.org/wiki/Euclidean_distance), for practical use cases it is simply not scalable because of its CPU-intensive nature with large data sets.

![quadtree-subdivision](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree-subdivision.png)

Quadtrees enable us to search points within a two-dimensional range efficiently, where those points are defined as latitude/longitude coordinates or as cartesian (x, y) coordinates. Additionally, we can save further computation by only subdividing a node after a certain threshold. And with the application of mapping algorithms such as the [Hilbert curve](https://en.wikipedia.org/wiki/Hilbert_curve), we can easily improve range query performance.

### Use cases

Below are some common uses of quadtrees:

- Image representation, processing, and compression.
- Spacial indexing and range queries.
- Location-based services like Google Maps, Uber, etc.
- Mesh generation and computer graphics.
- Sparse data storage.

# Circuit breaker

The circuit breaker is a design pattern used to detect failures and encapsulates the logic of preventing a failure from constantly recurring during maintenance, temporary external system failure, or unexpected system difficulties.

![circuit-breaker](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/circuit-breaker/circuit-breaker.png)

The basic idea behind the circuit breaker is very simple. We wrap a protected function call in a circuit breaker object, which monitors for failures. Once the failures reach a certain threshold, the circuit breaker trips, and all further calls to the circuit breaker return with an error, without the protected call being made at all. Usually, we'll also want some kind of monitor alert if the circuit breaker trips.

## Why do we need circuit breaking?

It's common for software systems to make remote calls to software running in different processes, probably on different machines across a network. One of the big differences between in-memory calls and remote calls is that remote calls can fail, or hang without a response until some timeout limit is reached. What's worse is if we have many callers on an unresponsive supplier, then we can run out of critical resources leading to cascading failures across multiple systems.

## States

Let's discuss circuit breaker states:

### Closed

When everything is normal, the circuit breakers remain closed, and all the request passes through to the services as normal. If the number of failures increases beyond the threshold, the circuit breaker trips and goes into an open state.

### Open

In this state circuit breaker returns an error immediately without even invoking the services. The Circuit breakers move into the half-open state after a certain timeout period elapses. Usually, it will have a monitoring system where the timeout will be specified.

### Half-open

In this state, the circuit breaker allows a limited number of requests from the service to pass through and invoke the operation. If the requests are successful, then the circuit breaker will go to the closed state. However, if the requests continue to fail, then it goes back to the open state.

# Rate Limiting

Rate limiting refers to preventing the frequency of an operation from exceeding a defined limit. In large-scale systems, rate limiting is commonly used to protect underlying services and resources. Rate limiting is generally used as a defensive mechanism in distributed systems, so that shared resources can maintain availability. It also protects our APIs from unintended or malicious overuse by limiting the number of requests that can reach our API in a given period of time.

![rate-limiting](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/rate-limiting/rate-limiting.png)

## Why do we need Rate Limiting?

Rate limiting is a very important part of any large-scale system and it can be used to accomplish the following:

- Avoid resource starvation as a result of Denial of Service (DoS) attacks.
- Rate Limiting helps in controlling operational costs by putting a virtual cap on the auto-scaling of resources which if not monitored might lead to exponential bills.
- Rate limiting can be used as defense or mitigation against some common attacks.
- For APIs that process massive amounts of data, rate limiting can be used to control the flow of that data.

## Algorithms

There are various algorithms for API rate limiting, each with its advantages and disadvantages. Let's briefly discuss some of these algorithms:

### Leaky Bucket

Leaky Bucket is an algorithm that provides a simple, intuitive approach to rate limiting via a queue. When registering a request, the system appends it to the end of the queue. Processing for the first item on the queue occurs at a regular interval or first-in, first-out (FIFO). If the queue is full, then additional requests are discarded (or leaked).

### Token Bucket

Here we use a concept of a _bucket_. When a request comes in, a token from the bucket must be taken and processed. The request will be refused if no token is available in the bucket, and the requester will have to try again later. As a result, the token bucket gets refreshed after a certain time period.

### Fixed Window

The system uses a window size of `n` seconds to track the fixed window algorithm rate. Each incoming request increments the counter for the window. It discards the request if the counter exceeds a threshold.

### Sliding Log

Sliding Log rate-limiting involves tracking a time-stamped log for each request. The system stores these logs in a time-sorted hash set or table. It also discards logs with timestamps beyond a threshold. When a new request comes in, we calculate the sum of logs to determine the request rate. If the request would exceed the threshold rate, then it is held.

### Sliding Window

Sliding Window is a hybrid approach that combines the fixed window algorithm's low processing cost and the sliding log's improved boundary conditions. Like the fixed window algorithm, we track a counter for each fixed window. Next, we account for a weighted value of the previous window's request rate based on the current timestamp to smooth out bursts of traffic.

## Rate Limiting in Distributed Systems

Rate Limiting becomes complicated when distributed systems are involved. The two broad problems that come with rate limiting in distributed systems are:

### Inconsistencies

When using a cluster of multiple nodes, we might need to enforce a global rate limit policy. Because if each node were to track its rate limit, a consumer could exceed a global rate limit when sending requests to different nodes. The greater the number of nodes, the more likely the user will exceed the global limit.

The simplest way to solve this problem is to use sticky sessions in our load balancers so that each consumer gets sent to exactly one node but this causes a lack of fault tolerance and scaling problems. Another approach might be to use a centralized data store like [Redis](https://redis.io) but this will increase latency and cause race conditions.

### Race Conditions

This issue happens when we use a naive _"get-then-set"_ approach, in which we retrieve the current rate limit counter, increment it, and then push it back to the datastore. This model's problem is that additional requests can come through in the time it takes to perform a full cycle of read-increment-store, each attempting to store the increment counter with an invalid (lower) counter value. This allows a consumer to send a very large number of requests to bypass the rate limiting controls.

One way to avoid this problem is to use some sort of distributed locking mechanism around the key, preventing any other processes from accessing or writing to the counter. Though the lock will become a significant bottleneck and will not scale well. A better approach might be to use a _"set-then-get"_ approach, allowing us to quickly increment and check counter values without letting the atomic operations get in the way.

# Service Discovery

Service discovery is the detection of services within a computer network. Service Discovery Protocol (SDP) is a networking standard that accomplishes the detection of networks by identifying resources.

## Why do we need Service Discovery?

In a monolithic application, services invoke one another through language-level methods or procedure calls. However, modern microservices-based applications typically run in virtualized or containerized environments where the number of instances of a service and their locations change dynamically. Consequently, we need a mechanism that enables the clients of service to make requests to a dynamically changing set of ephemeral service instances.

## Implementations

There are two main service discovery patterns:

### Client-side discovery

![client-side-service-discovery](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/service-discovery/client-side-service-discovery.png)

In this approach, the client obtains the location of another service by querying a service registry which is responsible for managing and storing the network locations of all the services.

### Server-side discovery

![server-side-service-discovery](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/service-discovery/server-side-service-discovery.png)

In this approach, we use an intermediate component such as a load balancer. The client makes a request to the service via a load balancer which then forwards the request to an available service instance.

## Service Registry

A service registry is basically a database containing the network locations of service instances to which the clients can reach out. A Service Registry must be highly available and up-to-date.

## Service Registration

We also need a way to obtain service information, often known as service registration. Let's look at two possible service registration approaches:

### Self-Registration

When using the self-registration model, a service instance is responsible for registering and de-registering itself in the Service Registry. In addition, if necessary, a service instance sends heartbeat requests to keep its registration alive.

### Third-party Registration

The registry keeps track of changes to running instances by polling the deployment environment or subscribing to events. When it detects a newly available service instance, it records it in its database. The Service Registry also de-registers terminated service instances.

## Service mesh

Service-to-service communication is essential in a distributed application but routing this communication, both within and across application clusters, becomes increasingly complex as the number of services grows. Service mesh enables managed, observable, and secure communication between individual services. It works with a service discovery protocol to detect services. [Istio](https://istio.io/latest/about/service-mesh) and [envoy](https://www.envoyproxy.io) are some of the most commonly used service mesh technologies.

## Examples

Here are some commonly used service discovery infrastructure tools:

- [etcd](https://etcd.io)
- [Consul](https://www.consul.io)
- [Apache Thrift](https://thrift.apache.org)
- [Apache Zookeeper](https://zookeeper.apache.org)

# SLA, SLO, SLI

Let's briefly discuss SLA, SLO, and SLI. These are mostly related to the business and site reliability side of things but good to know nonetheless.

## Why are they important?

SLAs, SLOs, and SLIs allow companies to define, track and monitor the promises made for a service to its users. Together, SLAs, SLOs, and SLIs should help teams generate more user trust in their services with an added emphasis on continuous improvement to incident management and response processes.

## SLA

An SLA, or Service Level Agreement, is an agreement made between a company and its users of a given service. The SLA defines the different promises that the company makes to users regarding specific metrics, such as service availability.

_SLAs are often written by a company's business or legal team._

## SLO

An SLO, or Service Level Objective, is the promise that a company makes to users regarding a specific metric such as incident response or uptime. SLOs exist within an SLA as individual promises contained within the full user agreement. The SLO is the specific goal that the service must meet in order to comply with the SLA. SLOs should always be simple, clearly defined, and easily measured to determine whether or not the objective is being fulfilled.

## SLI

An SLI, or Service Level Indicator, is a key metric used to determine whether or not the SLO is being met. It is the measured value of the metric described within the SLO. In order to remain in compliance with the SLA, the SLI's value must always meet or exceed the value determined by the SLO.

# Disaster recovery

Disaster recovery (DR) is a process of regaining access and functionality of the infrastructure after events like a natural disaster, cyber attack, or even business disruptions.

Disaster recovery relies upon the replication of data and computer processing in an off-premises location not affected by the disaster. When servers go down because of a disaster, a business needs to recover lost data from a second location where the data is backed up. Ideally, an organization can transfer its computer processing to that remote location as well in order to continue operations.

_Disaster Recovery is often not actively discussed during system design interviews but it's important to have some basic understanding of this topic. You can learn more about disaster recovery from [AWS Well-Architected Framework](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/plan-for-disaster-recovery-dr.html)._

## Why is disaster recovery important?

Disaster recovery can have the following benefits:

- Minimize interruption and downtime
- Limit damages
- Fast restoration
- Better customer retention

## Terms

Let's discuss some important terms relevantly for disaster recovery:

![disaster-recovery](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/disaster-recovery/disaster-recovery.png)

### RTO

Recovery Time Objective (RTO) is the maximum acceptable delay between the interruption of service and restoration of service. This determines what is considered an acceptable time window when service is unavailable.

### RPO

Recovery Point Objective (RPO) is the maximum acceptable amount of time since the last data recovery point. This determines what is considered an acceptable loss of data between the last recovery point and the interruption of service.

## Strategies

A variety of disaster recovery (DR) strategies can be part of a disaster recovery plan.

### Back-up

This is the simplest type of disaster recovery and involves storing data off-site or on a removable drive.

### Cold Site

In this type of disaster recovery, an organization sets up basic infrastructure in a second site.

### Hot site

A hot site maintains up-to-date copies of data at all times. Hot sites are time-consuming to set up and more expensive than cold sites, but they dramatically reduce downtime.

# Virtual Machines (VMs) and Containers

Before we discuss virtualization vs containerization, let's learn what are virtual machines (VMs) and Containers.

## Virtual Machines (VM)

A Virtual Machine (VM) is a virtual environment that functions as a virtual computer system with its own CPU, memory, network interface, and storage, created on a physical hardware system. A software called a hypervisor separates the machine's resources from the hardware and provisions them appropriately so they can be used by the VM.

VMs are isolated from the rest of the system, and multiple VMs can exist on a single piece of hardware, like a server. They can be moved between host servers depending on the demand or to use resources more efficiently.

### What is a Hypervisor?

A Hypervisor sometimes called a Virtual Machine Monitor (VMM), isolates the operating system and resources from the virtual machines and enables the creation and management of those VMs. The hypervisor treats resources like CPU, memory, and storage as a pool of resources that can be easily reallocated between existing guests or new virtual machines.

### Why use a Virtual Machine?

Server consolidation is a top reason to use VMs. Most operating system and application deployments only use a small amount of the physical resources available. By virtualizing our servers, we can place many virtual servers onto each physical server to improve hardware utilization. This keeps us from needing to purchase additional physical resources.

A VM provides an environment that is isolated from the rest of a system, so whatever is running inside a VM won't interfere with anything else running on the host hardware. Because VMs are isolated, they are a good option for testing new applications or setting up a production environment. We can also run a single-purpose VM to support a specific use case.

## Containers

A container is a standard unit of software that packages up code and all its dependencies such as specific versions of runtimes and libraries so that the application runs quickly and reliably from one computing environment to another. Containers offer a logical packaging mechanism in which applications can be abstracted from the environment in which they actually run. This decoupling allows container-based applications to be deployed easily and consistently, regardless of the target environment.

### Why do we need containers?

Let's discuss some advantages of using containers:

**Separation of responsibility**

Containerization provides a clear separation of responsibility, as developers focus on application logic and dependencies, while operations teams can focus on deployment and management.

**Workload portability**

Containers can run virtually anywhere, greatly easing development and deployment.

**Application isolation**

Containers virtualize CPU, memory, storage, and network resources at the operating system level, providing developers with a view of the OS logically isolated from other applications.

**Agile development**

Containers allow developers to move much more quickly by avoiding concerns about dependencies and environments.

**Efficient operations**

Containers are lightweight and allow us to use just the computing resources we need.

## Virtualization vs Containerization

![virtualization-vs-containerization](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/virtual-machines-and-containers/virtualization-vs-containerization.png)

In traditional virtualization, a hypervisor virtualizes physical hardware. The result is that each virtual machine contains a guest OS, a virtual copy of the hardware that the OS requires to run, and an application and its associated libraries and dependencies.

Instead of virtualizing the underlying hardware, containers virtualize the operating system so each container contains only the application and its dependencies making them much more lightweight than VMs. Containers also share the OS kernel and use a fraction of the memory VMs require.

# OAuth 2.0 and OpenID Connect (OIDC)

## OAuth 2.0

OAuth 2.0, which stands for Open Authorization, is a standard designed to provide consented access to resources on behalf of the user, without ever sharing the user's credentials. OAuth 2.0 is an authorization protocol and not an authentication protocol, it is designed primarily as a means of granting access to a set of resources, for example, remote APIs or user's data.

### Concepts

The OAuth 2.0 protocol defines the following entities:

- **Resource Owner**: The user or system that owns the protected resources and can grant access to them.
- **Client**: The client is the system that requires access to the protected resources.
- **Authorization Server**: This server receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner.
- **Resource Server**: A server that protects the user's resources and receives access requests from the Client. It accepts and validates an Access Token from the Client and returns the appropriate resources.
- **Scopes**: They are used to specify exactly the reason for which access to resources may be granted. Acceptable scope values, and which resources they relate to, are dependent on the Resource Server.
- **Access Token**: A piece of data that represents the authorization to access resources on behalf of the end-user.

### How does OAuth 2.0 work?

Let's learn how OAuth 2.0 works:

![oauth2](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/oauth2-and-openid-connect/oauth2.png)

1. The client requests authorization from the Authorization Server, supplying the client id and secret as identification. It also provides the scopes and an endpoint URI to send the Access Token or the Authorization Code.
2. The Authorization Server authenticates the client and verifies that the requested scopes are permitted.
3. The resource owner interacts with the authorization server to grant access.
4. The Authorization Server redirects back to the client with either an Authorization Code or Access Token, depending on the grant type. A Refresh Token may also be returned.
5. With the Access Token, the client can request access to the resource from the Resource Server.

### Disadvantages

Here are the most common disadvantages of OAuth 2.0:

- Lacks built-in security features.
- No standard implementation.
- No common set of scopes.

## OpenID Connect

OAuth 2.0 is designed only for _authorization_, for granting access to data and features from one application to another. OpenID Connect (OIDC) is a thin layer that sits on top of OAuth 2.0 that adds login and profile information about the person who is logged in.

When an Authorization Server supports OIDC, it is sometimes called an identity provider (IdP), since it provides information about the Resource Owner back to the Client. OpenID Connect is relatively new, resulting in lower adoption and industry implementation of best practices compared to OAuth.

### Concepts

The OpenID Connect (OIDC) protocol defines the following entities:

- **Relying Party**: The current application.
- **OpenID Provider**: This is essentially an intermediate service that provides a one-time code to the Relying Party.
- **Token Endpoint**: A web server that accepts the One-Time Code (OTC) and provides an access code that's valid for an hour. The main difference between OIDC and OAuth 2.0 is that the token is provided using JSON Web Token (JWT).
- **UserInfo Endpoint**: The Relying Party communicates with this endpoint, providing a secure token and receiving information about the end-user

Both OAuth 2.0 and OIDC are easy to implement and are JSON based, which is supported by most web and mobile applications. However, the OpenID Connect (OIDC) specification is more strict than that of basic OAuth.

# Single Sign-On (SSO)

Single Sign-On (SSO) is an authentication process in which a user is provided access to multiple applications or websites by using only a single set of login credentials. This prevents the need for the user to log separately into the different applications.

The user credentials and other identifying information are stored and managed by a centralized system called Identity Provider (IdP). The Identity Provider is a trusted system that provides access to other websites and applications.

Single Sign-On (SSO) based authentication systems are commonly used in enterprise environments where employees require access to multiple applications of their organizations.

## Components

Let's discuss some key components of Single Sign-On (SSO).

### Identity Provider (IdP)

User Identity information is stored and managed by a centralized system called Identity Provider (IdP). The Identity Provider authenticates the user and provides access to the service provider.

The identity provider can directly authenticate the user by validating a username and password or by validating an assertion about the user's identity as presented by a separate identity provider. The identity provider handles the management of user identities in order to free the service provider from this responsibility.

### Service Provider

A service provider provides services to the end-user. They rely on identity providers to assert the identity of a user, and typically certain attributes about the user are managed by the identity provider. Service providers may also maintain a local account for the user along with attributes that are unique to their service.

### Identity Broker

An identity broker acts as an intermediary that connects multiple service providers with various different identity providers. Using Identity Broker, we can perform single sign-on over any application without the hassle of the protocol it follows.

## SAML

Security Assertion Markup Language is an open standard that allows clients to share security information about identity, authentication, and permission across different systems. SAML is implemented with the Extensible Markup Language (XML) standard for sharing data.

SAML specifically enables identity federation, making it possible for identity providers (IdPs) to seamlessly and securely pass authenticated identities and their attributes to service providers.

## How does SSO work?

Now, let's discuss how Single Sign-On works:

![sso](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/single-sign-on/sso.png)

1. The user requests a resource from their desired application.
2. The application redirects the user to the Identity Provider (IdP) for authentication.
3. The user signs in with their credentials (usually, username and password).
4. Identity Provider (IdP) sends a Single Sign-On response back to the client application.
5. The application grants access to the user.

## SAML vs OAuth 2.0 and OpenID Connect (OIDC)

There are many differences between SAML, OAuth, and OIDC. SAML uses XML to pass messages, while OAuth and OIDC use JSON. OAuth provides a simpler experience, while SAML is geared towards enterprise security.

OAuth and OIDC use RESTful communication extensively, which is why mobile, and modern web applications find OAuth and OIDC a better experience for the user. SAML, on the other hand, drops a session cookie in a browser that allows a user to access certain web pages. This is great for short-lived workloads.

OIDC is developer-friendly and simpler to implement, which broadens the use cases for which it might be implemented. It can be implemented from scratch pretty fast, via freely available libraries in all common programming languages. SAML can be complex to install and maintain, which only enterprise-size companies can handle well.

OpenID Connect is essentially a layer on top of the OAuth framework. Therefore, it can offer a built-in layer of permission that asks a user to agree to what the service provider might access. Although SAML is also capable of allowing consent flow, it achieves this by hard-coding carried out by a developer and not as part of its protocol.

_Both of these authentication protocols are good at what they do. As always, a lot depends on our specific use cases and target audience._

## Advantages

Following are the benefits of using Single Sign-On:

- Ease of use as users only need to remember one set of credentials.
- Ease of access without having to go through a lengthy authorization process.
- Enforced security and compliance to protect sensitive data.
- Simplifying the management with reduced IT support cost and admin time.

## Disadvantages

Here are some disadvantages of Single Sign-On:

- Single Password Vulnerability, if the main SSO password gets compromised, all the supported applications get compromised.
- The authentication process using Single Sign-On is slower than traditional authentication as every application has to request the SSO provider for verification.

## Examples

These are some commonly used Identity Providers (IdP):

- [Okta](https://www.okta.com)
- [Google](https://cloud.google.com/architecture/identity/single-sign-on)
- [Auth0](https://auth0.com)
- [OneLogin](https://www.onelogin.com)

# SSL, TLS, mTLS

Let's briefly discuss some important communication security protocols such as SSL, TLS, and mTLS. I would say that from a _"big picture"_ system design perspective, this topic is not very important but still good to know about.

## SSL

SSL stands for Secure Sockets Layer, and it refers to a protocol for encrypting and securing communications that take place on the internet. It was first developed in 1995 but since has been deprecated in favor of TLS (Transport Layer Security).

### Why is it called an SSL certificate if it is deprecated?

Most major certificate providers still refer to certificates as SSL certificates, which is why the naming convention persists.

### Why was SSL so important?

Originally, data on the web was transmitted in plaintext that anyone could read if they intercepted the message. SSL was created to correct this problem and protect user privacy. By encrypting any data that goes between the user and a web server, SSL also stops certain kinds of cyber attacks by preventing attackers from tampering with data in transit.

## TLS

Transport Layer Security, or TLS, is a widely adopted security protocol designed to facilitate privacy and data security for communications over the internet. TLS evolved from a previous encryption protocol called Secure Sockets Layer (SSL). A primary use case of TLS is encrypting the communication between web applications and servers.

There are three main components to what the TLS protocol accomplishes:

- **Encryption**: hides the data being transferred from third parties.
- **Authentication**: ensures that the parties exchanging information are who they claim to be.
- **Integrity**: verifies that the data has not been forged or tampered with.

## mTLS

Mutual TLS, or mTLS, is a method for mutual authentication. mTLS ensures that the parties at each end of a network connection are who they claim to be by verifying that they both have the correct private key. The information within their respective TLS certificates provides additional verification.

### Why use mTLS?

mTLS helps ensure that the traffic is secure and trusted in both directions between a client and server. This provides an additional layer of security for users who log in to an organization's network or applications. It also verifies connections with client devices that do not follow a login process, such as Internet of Things (IoT) devices.

Nowadays, mTLS is commonly used by microservices or distributed systems in a [zero trust security model](https://en.wikipedia.org/wiki/Zero_trust_security_model) to verify each other.

# System Design Interviews

System design is a very extensive topic and system design interviews are designed to evaluate your capability to produce technical solutions to abstract problems, as such, they're not designed for a specific answer. The unique aspect of system design interviews is the two-way nature between the candidate and the interviewer.

Expectations are quite different at different engineering levels as well. This is because someone with a lot of practical experience will approach it quite differently from someone who's new in the industry. As a result, it's hard to come up with a single strategy that will help us stay organized during the interview.

Let's look at some common strategies for the system design interviews:

## Requirements clarifications

System design interview questions, by nature, are vague or abstract. Asking questions about the exact scope of the problem, and clarifying functional requirements early in the interview is essential. Usually, requirements are divided into three parts:

### Functional requirements

These are the requirements that the end user specifically demands as basic functionalities that the system should offer. All these functionalities need to be necessarily incorporated into the system as part of the contract.

For example:

- "What are the features that we need to design for this system?"
- "What are the edge cases we need to consider, if any, in our design?"

### Non-functional requirements

These are the quality constraints that the system must satisfy according to the project contract. The priority or extent to which these factors are implemented varies from one project to another. They are also called non-behavioral requirements. For example, portability, maintainability, reliability, scalability, security, etc.

For example:

- "Each request should be processed with the minimum latency"
- "System should be highly available"

### Extended requirements

These are basically "nice to have" requirements that might be out of the scope of the system.

For example:

- "Our system should record metrics and analytics"
- "Service health and performance monitoring?"

## Estimation and Constraints

Estimate the scale of the system we're going to design. It is important to ask questions such as:

- "What is the desired scale that this system will need to handle?"
- "What is the read/write ratio of our system?"
- "How many requests per second?"
- "How much storage will be needed?"

These questions will help us scale our design later.

## Data model design

Once we have the estimations, we can start with defining the database schema. Doing so in the early stages of the interview would help us to understand the data flow which is the core of every system. In this step, we basically define all the entities and relationships between them.

- "What are the different entities in the system?"
- "What are the relationships between these entities?"
- "How many tables do we need?"
- "Is NoSQL a better choice here?"

## API design

Next, we can start designing APIs for the system. These APIs will help us define the expectations from the system explicitly. We don't have to write any code, just a simple interface defining the API requirements such as parameters, functions, classes, types, entities, etc.

For example:

```tsx
createUser(name: string, email: string): User
```

It is advised to keep the interface as simple as possible and come back to it later when covering extended requirements.

## High-level component design

Now we have established our data model and API design, it's time to identify system components (such as Load Balancers, API Gateway, etc.) that are needed to solve our problem and draft the first design of our system.

- "Is it best to design a monolithic or a microservices architecture?"
- "What type of database should we use?"

Once we have a basic diagram, we can start discussing with the interviewer how the system will work from the client's perspective.

## Detailed design

Now it's time to go into detail about the major components of the system we designed. As always discuss with the interviewer which component may need further improvements.

Here is a good opportunity to demonstrate your experience in the areas of your expertise. Present different approaches, advantages, and disadvantages. Explain your design decisions, and back them up with examples. This is also a good time to discuss any additional features the system might be able to support, though this is optional.

- "How should we partition our data?"
- "What about load distribution?"
- "Should we use cache?"
- "How will we handle a sudden spike in traffic?"

Also, try not to be too opinionated about certain technologies, statements like "I believe that NoSQL databases are just better, SQL databases are not scalable" reflect poorly. As someone who has interviewed a lot of people over the years, my two cents here would be to be humble about what you know and what you do not. Use your existing knowledge with examples to navigate this part of the interview.

## Identify and resolve bottlenecks

Finally, it's time to discuss bottlenecks and approaches to mitigate them. Here are some important questions to ask:

- "Do we have enough database replicas?"
- "Is there any single point of failure?"
- "Is database sharding required?"
- "How can we make our system more robust?"
- "How to improve the availability of our cache?"

Make sure to read the engineering blog of the company you're interviewing with. This will help you get a sense of what technology stack they're using and which problems are important to them.

# URL Shortener

Let's design a URL shortener, similar to services like [Bitly](https://bitly.com), [TinyURL](https://tinyurl.com/app).

## What is a URL Shortener?

A URL shortener service creates an alias or a short URL for a long URL. Users are redirected to the original URL when they visit these short links.

For example, the following long URL can be changed to a shorter URL.

**Long URL**: [https://karanpratapsingh.com/courses/system-design/url-shortener](https://karanpratapsingh.com/courses/system-design/url-shortener)

**Short URL**: [https://bit.ly/3I71d3o](https://bit.ly/3I71d3o)

## Why do we need a URL shortener?

URL shortener saves space in general when we are sharing URLs. Users are also less likely to mistype shorter URLs. Moreover, we can also optimize links across devices, this allows us to track individual links.

## Requirements

Our URL shortening system should meet the following requirements:

### Functional requirements

- Given a URL, our service should generate a _shorter and unique_ alias for it.
- Users should be redirected to the original URL when they visit the short link.
- Links should expire after a default timespan.

### Non-functional requirements

- High availability with minimal latency.
- The system should be scalable and efficient.

### Extended requirements

- Prevent abuse of services.
- Record analytics and metrics for redirections.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic related assumptions with your interviewer._

### Traffic

This will be a read-heavy system, so let's assume a `100:1` read/write ratio with 100 million links generated per month.

**Reads/Writes Per month**

For reads per month:

$$
100 \times 100 \space million = 10 \space billion/month
$$

Similarly for writes:

$$
1 \times 100 \space million = 100 \space million/month
$$

**What would be Requests Per Second (RPS) for our system?**

100 million requests per month translate into 40 requests per second.

$$
\frac{100 \space million}{(30 \space days \times 24 \space hrs \times 3600 \space seconds)} = \sim 40 \space URLs/second
$$

And with a `100:1` read/write ratio, the number of redirections will be:

$$
100 \times 40 \space URLs/second = 4000 \space requests/second
$$

### Bandwidth

Since we expect about 40 URLs every second, and if we assume each request is of size 500 bytes then the total incoming data for write requests would be:

$$
40 \times 500 \space bytes = 20 \space KB/second
$$

Similarly, for the read requests, since we expect about 4K redirections, the total outgoing data would be:

$$
4000 \space URLs/second \times 500 \space bytes = \sim 2 \space MB/second
$$

### Storage

For storage, we will assume we store each link or record in our database for 10 years. Since we expect around 100M new requests every month, the total number of records we will need to store would be:

$$
100 \space million \times 10\space years \times 12 \space months = 12 \space billion
$$

Like earlier, if we assume each stored record will be approximately 500 bytes. We will need around 6TB of storage:

$$
12 \space billion \times 500 \space bytes = 6 \space TB
$$

### Cache

For caching, we will follow the classic [Pareto principle](https://en.wikipedia.org/wiki/Pareto_principle) also known as the 80/20 rule. This means that 80% of the requests are for 20% of the data, so we can cache around 20% of our requests.

Since we get around 4K read or redirection requests each second, this translates into 350M requests per day.

$$
4000 \space URLs/second \times 24 \space hours \times 3600 \space seconds = \sim 350 \space million \space requests/day
$$

Hence, we will need around 35GB of memory per day.

$$
20 \space percent \times 350 \space million \times 500 \space bytes = 35 \space GB/day
$$

### High-level estimate

Here is our high-level estimate:

| Type                 | Estimate   |
| -------------------- | ---------- |
| Writes (New URLs)    | 40/s       |
| Reads (Redirection)  | 4K/s       |
| Bandwidth (Incoming) | 20 KB/s    |
| Bandwidth (Outgoing) | 2 MB/s     |
| Storage (10 years)   | 6 TB       |
| Memory (Caching)     | ~35 GB/day |

## Data model design

Next, we will focus on the data model design. Here is our database schema:

![url-shortener-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/url-shortener/url-shortener-datamodel.png)

Initially, we can get started with just two tables:

**users**

Stores user's details such as `name`, `email`, `createdAt`, etc.

**urls**

Contains the new short URL's properties such as `expiration`, `hash`, `originalURL`, and `userID` of the user who created the short URL. We can also use the `hash` column as an [index](https://karanpratapsingh.com/courses/system-design/indexes) to improve the query performance.

### What kind of database should we use?

Since the data is not strongly relational, NoSQL databases such as [Amazon DynamoDB](https://aws.amazon.com/dynamodb), [Apache Cassandra](https://cassandra.apache.org/_/index.html), or [MongoDB](https://www.mongodb.com) will be a better choice here, if we do decide to use an SQL database then we can use something like [Azure SQL Database](https://azure.microsoft.com/en-in/products/azure-sql/database) or [Amazon RDS](https://aws.amazon.com/rds).

_For more details, refer to [SQL vs NoSQL](https://karanpratapsingh.com/courses/system-design/sql-vs-nosql-databases)._

## API design

Let us do a basic API design for our services:

### Create URL

This API should create a new short URL in our system given an original URL.

```tsx
createURL(apiKey: string, originalURL: string, expiration?: Date): string
```

**Parameters**

API Key (`string`): API key provided by the user.

Original URL (`string`): Original URL to be shortened.

Expiration (`Date`): Expiration date of the new URL _(optional)_.

**Returns**

Short URL (`string`): New shortened URL.

### Get URL

This API should retrieve the original URL from a given short URL.

```tsx
getURL(apiKey: string, shortURL: string): string
```

**Parameters**

API Key (`string`): API key provided by the user.

Short URL (`string`): Short URL mapped to the original URL.

**Returns**

Original URL (`string`): Original URL to be retrieved.

### Delete URL

This API should delete a given shortURL from our system.

```tsx
deleteURL(apiKey: string, shortURL: string): boolean
```

**Parameters**

API Key (`string`): API key provided by the user.

Short URL (`string`): Short URL to be deleted.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Why do we need an API key?

As you must've noticed, we're using an API key to prevent abuse of our services. Using this API key we can limit the users to a certain number of requests per second or minute. This is quite a standard practice for developer APIs and should cover our extended requirement.

## High-level design

Now let us do a high-level design of our system.

### URL Encoding

Our system's primary goal is to shorten a given URL, let's look at different approaches:

**Base62 Approach**

In this approach, we can encode the original URL using [Base62](https://en.wikipedia.org/wiki/Base62) which consists of the capital letters A-Z, the lower case letters a-z, and the numbers 0-9.

$$
Number \space of \space URLs = 62^N
$$

Where,

`N`: Number of characters in the generated URL.

So, if we want to generate a URL that is 7 characters long, we will generate ~3.5 trillion different URLs.

$$
\begin{gather*}
62^5 = \sim 916 \space million \space URLs \\
62^6 = \sim 56.8 \space billion \space URLs \\
62^7 = \sim 3.5 \space trillion \space URLs
\end{gather*}
$$

This is the simplest solution here, but it does not guarantee non-duplicate or collision-resistant keys.

**MD5 Approach**

The [MD5 message-digest algorithm](https://en.wikipedia.org/wiki/MD5) is a widely used hash function producing a 128-bit hash value (or 32 hexadecimal digits). We can use these 32 hexadecimal digits for generating 7 characters long URL.

$$
MD5(original\_url) \rightarrow base62encode \rightarrow hash
$$

However, this creates a new issue for us, which is duplication and collision. We can try to re-compute the hash until we find a unique one but that will increase the overhead of our systems. It's better to look for more scalable approaches.

**Counter Approach**

In this approach, we will start with a single server which will maintain the count of the keys generated. Once our service receives a request, it can reach out to the counter which returns a unique number and increments the counter. When the next request comes the counter again returns the unique number and this goes on.

$$
Counter(0-3.5 \space trillion) \rightarrow base62encode \rightarrow hash
$$

The problem with this approach is that it can quickly become a single point for failure. And if we run multiple instances of the counter we can have collision as it's essentially a distributed system.

To solve this issue we can use a distributed system manager such as [Zookeeper](https://zookeeper.apache.org) which can provide distributed synchronization. Zookeeper can maintain multiple ranges for our servers.

$$
\begin{align*}
& Range \space 1: \space 1 \rightarrow 1,000,000 \\
& Range \space 2: \space 1,000,001 \rightarrow 2,000,000 \\
& Range \space 3: \space 2,000,001 \rightarrow 3,000,000 \\
& ...
\end{align*}
$$

Once a server reaches its maximum range Zookeeper will assign an unused counter range to the new server. This approach can guarantee non-duplicate and collision-resistant URLs. Also, we can run multiple instances of Zookeeper to remove the single point of failure.

### Key Generation Service (KGS)

As we discussed, generating a unique key at scale without duplication and collisions can be a bit of a challenge. To solve this problem, we can create a standalone Key Generation Service (KGS) that generates a unique key ahead of time and stores it in a separate database for later use. This approach can make things simple for us.

**How to handle concurrent access?**

Once the key is used, we can mark it in the database to make sure we don't reuse it, however, if there are multiple server instances reading data concurrently, two or more servers might try to use the same key.

The easiest way to solve this would be to store keys in two tables. As soon as a key is used, we move it to a separate table with appropriate locking in place. Also, to improve reads, we can keep some of the keys in memory.

**KGS database estimations**

As per our discussion, we can generate up to ~56.8 billion unique 6 character long keys which will result in us having to store 300 GB of keys.

$$
6 \space characters \times 56.8 \space billion = \sim 390 \space GB
$$

While 390 GB seems like a lot for this simple use case, it is important to remember this is for the entirety of our service lifetime and the size of the keys database would not increase like our main database.

### Caching

Now, let's talk about [caching](https://karanpratapsingh.com/courses/system-design/caching). As per our estimations, we will require around ~35 GB of memory per day to cache 20% of the incoming requests to our services. For this use case, we can use [Redis](https://redis.io) or [Memcached](https://memcached.org) servers alongside our API server.

_For more details, refer to [caching](https://karanpratapsingh.com/courses/system-design/caching)._

### Design

Now that we have identified some core components, let's do the first draft of our system design.

![url-shortener-basic-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/url-shortener/url-shortener-basic-design.png)

Here's how it works:

**Creating a new URL**

1. When a user creates a new URL, our API server requests a new unique key from the Key Generation Service (KGS).
2. Key Generation Service provides a unique key to the API server and marks the key as used.
3. API server writes the new URL entry to the database and cache.
4. Our service returns an HTTP 201 (Created) response to the user.

**Accessing a URL**

1. When a client navigates to a certain short URL, the request is sent to the API servers.
2. The request first hits the cache, and if the entry is not found there then it is retrieved from the database and an HTTP 301 (Redirect) is issued to the original URL.
3. If the key is still not found in the database, an HTTP 404 (Not found) error is sent to the user.

## Detailed design

It's time to discuss the finer details of our design.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

- Hash-Based Partitioning
- List-Based Partitioning
- Range Based Partitioning
- Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Database cleanup

This is more of a maintenance step for our services and depends on whether we keep the expired entries or remove them. If we do decide to remove expired entries, we can approach this in two different ways:

**Active cleanup**

In active cleanup, we will run a separate cleanup service which will periodically remove expired links from our storage and cache. This will be a very lightweight service like a [cron job](https://en.wikipedia.org/wiki/Cron).

**Passive cleanup**

For passive cleanup, we can remove the entry when a user tries to access an expired link. This can ensure a lazy cleanup of our database and cache.

### Cache

Now let us talk about [caching](https://karanpratapsingh.com/courses/system-design/caching).

**Which cache eviction policy to use?**

As we discussed before, we can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) and cache 20% of the daily traffic but what kind of cache eviction policy would best fit our needs?

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can store and update metadata like visitor's country, platform, the number of views, etc alongside the URL entry in our database.

### Security

For security, we can introduce private URLs and authorization. A separate table can be used to store user ids that have permission to access a specific URL. If a user does not have proper permissions, we can return an HTTP 401 (Unauthorized) error.

We can also use an [API Gateway](https://karanpratapsingh.com/courses/system-design/api-gateway) as they can support capabilities like authorization, rate limiting, and load balancing out of the box.

## Identify and resolve bottlenecks

![url-shortener-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/url-shortener/url-shortener-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if the API service or Key Generation Service crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "What if the key database used by KGS fails?"
- "How to improve the availability of our cache?"

To make our system more resilient we can do the following:

- Running multiple instances of our Servers and Key Generation Service.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our database as it's a read-heavy system.
- Standby replica for our key database in case it fails.
- Multiple instances and replicas for our distributed cache.

# WhatsApp

Let's design a [WhatsApp](https://whatsapp.com) like instant messaging service, similar to services like [Facebook Messenger](https://www.messenger.com), and [WeChat](https://www.wechat.com).

## What is WhatsApp?

WhatsApp is a chat application that provides instant messaging services to its users. It is one of the most used mobile applications on the planet, connecting over 2 billion users in 180+ countries. WhatsApp is also available on the web.

## Requirements

Our system should meet the following requirements:

### Functional requirements

- Should support one-on-one chat.
- Group chats (max 100 people).
- Should support file sharing (image, video, etc.).

### Non-functional requirements

- High availability with minimal latency.
- The system should be scalable and efficient.

### Extended requirements

- Sent, Delivered, and Read receipts of the messages.
- Show the last seen time of users.
- Push notifications.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

Let us assume we have 50 million daily active users (DAU) and on average each user sends at least 10 messages to 2 different people every day. This gives us 2 billion messages per day.

$$
50 \space million \times 20 \space messages = 2 \space billion/day
$$

Messages can also contain media such as images, videos, or other files. We can assume that 5 percent of messages are media files shared by the users, which gives us additional 200 million files we would need to store.

$$
5 \space percent \times 2 \space billion = 200 \space million/day
$$

**What would be Requests Per Second (RPS) for our system?**

2 billion requests per day translate into 24K requests per second.

$$
\frac{2 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 24K \space requests/second
$$

### Storage

If we assume each message on average is 100 bytes, we will require about 200 GB of database storage every day.

$$
2 \space billion \times 100 \space bytes = \sim 200 \space GB/day
$$

As per our requirements, we also know that around 5 percent of our daily messages (100 million) are media files. If we assume each file is 50 KB on average, we will require 10 TB of storage every day.

$$
100 \space million \times 100 \space KB = 10 \space TB/day
$$

And for 10 years, we will require about 38 PB of storage.

$$
(10 \space TB + 0.2 \space TB) \times 10 \space years \times 365 \space days = \sim 38 \space PB
$$

### Bandwidth

As our system is handling 10.2 TB of ingress every day, we will require a minimum bandwidth of around 120 MB per second.

$$
\frac{10.2 \space TB}{(24 \space hrs \times 3600 \space seconds)} = \sim 120 \space MB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate   |
| ------------------------- | ---------- |
| Daily active users (DAU)  | 50 million |
| Requests per second (RPS) | 24K/s      |
| Storage (per day)         | ~10.2 TB   |
| Storage (10 years)        | ~38 PB     |
| Bandwidth                 | ~120 MB/s  |

## Data model design

This is the general data model which reflects our requirements.

![whatsapp-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-datamodel.png)

We have the following tables:

**users**

This table will contain a user's information such as `name`, `phoneNumber`, and other details.

**messages**

As the name suggests, this table will store messages with properties such as `type` (text, image, video, etc.), `content`, and timestamps for message delivery. The message will also have a corresponding `chatID` or `groupID`.

**chats**

This table basically represents a private chat between two users and can contain multiple messages.

**users_chats**

This table maps users and chats as multiple users can have multiple chats (N:M relationship) and vice versa.

**groups**

This table represents a group made up of multiple users.

**users_groups**

This table maps users and groups as multiple users can be a part of multiple groups (N:M relationship) and vice versa.

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Get all chats or groups

This API will get all chats or groups for a given `userID`.

```tsx
getAll(userID: UUID): Chat[] | Group[]
```

**Parameters**

User ID (`UUID`): ID of the current user.

**Returns**

Result (`Chat[] | Group[]`): All the chats and groups the user is a part of.

### Get messages

Get all messages for a user given the `channelID` (chat or group id).

```tsx
getMessages(userID: UUID, channelID: UUID): Message[]
```

**Parameters**

User ID (`UUID`): ID of the current user.

Channel ID (`UUID`): ID of the channel (chat or group) from which messages need to be retrieved.

**Returns**

Messages (`Message[]`): All the messages in a given chat or group.

### Send message

Send a message from a user to a channel (chat or group).

```tsx
sendMessage(userID: UUID, channelID: UUID, message: Message): boolean
```

**Parameters**

User ID (`UUID`): ID of the current user.

Channel ID (`UUID`): ID of the channel (chat or group) user wants to send a message to.

Message (`Message`): The message (text, image, video, etc.) that the user wants to send.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Join or leave a group

Send a message from a user to a channel (chat or group).

```tsx
joinGroup(userID: UUID, channelID: UUID): boolean
leaveGroup(userID: UUID, channelID: UUID): boolean
```

**Parameters**

User ID (`UUID`): ID of the current user.

Channel ID (`UUID`): ID of the channel (chat or group) the user wants to join or leave.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**User Service**

This is an HTTP-based service that handles user-related concerns such as authentication and user information.

**Chat Service**

The chat service will use WebSockets and establish connections with the client to handle chat and group message-related functionality. We can also use cache to keep track of all the active connections sort of like sessions which will help us determine if the user is online or not.

**Notification Service**

This service will simply send push notifications to the users. It will be discussed in detail separately.

**Presence Service**

The presence service will keep track of the _last seen_ status of all users. It will be discussed in detail separately.

**Media service**

This service will handle the media (images, videos, files, etc.) uploads. It will be discussed in detail separately.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### Real-time messaging

How do we efficiently send and receive messages? We have two different options:

**Pull model**

The client can periodically send an HTTP request to servers to check if there are any new messages. This can be achieved via something like [Long polling](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#long-polling).

**Push model**

The client opens a long-lived connection with the server and once new data is available it will be pushed to the client. We can use [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) or [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) for this.

The pull model approach is not scalable as it will create unnecessary request overhead on our servers and most of the time the response will be empty, thus wasting our resources. To minimize latency, using the push model with [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) is a better choice because then we can push data to the client once it's available without any delay, given the connection is open with the client. Also, WebSockets provide full-duplex communication, unlike [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) which are only unidirectional.

_Note: Learn more about [Long polling, WebSockets, Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events)._

### Last seen

To implement the last seen functionality, we can use a [heartbeat](<https://en.wikipedia.org/wiki/Heartbeat_(computing)>) mechanism, where the client can periodically ping the servers indicating its liveness. Since this needs to be as low overhead as possible, we can store the last active timestamp in the cache as follows:

| Key    | Value               |
| ------ | ------------------- |
| User A | 2022-07-01T14:32:50 |
| User B | 2022-07-05T05:10:35 |
| User C | 2022-07-10T04:33:25 |

This will give us the last time the user was active. This functionality will be handled by the presence service combined with [Redis](https://redis.io) or [Memcached](https://memcached.org) as our cache.

Another way to implement this is to track the latest action of the user, once the last activity crosses a certain threshold, such as _"user hasn't performed any action in the last 30 seconds"_, we can show the user as offline and last seen with the last recorded timestamp. This will be more of a lazy update approach and might benefit us over heartbeat in certain cases.

### Notifications

Once a message is sent in a chat or a group, we will first check if the recipient is active or not, we can get this information by taking the user's active connection and last seen into consideration.

If the recipient is not active, the chat service will add an event to a [message queue](https://karanpratapsingh.com/courses/system-design/message-queues) with additional metadata such as the client's device platform which will be used to route the notification to the correct platform later on.

The notification service will then consume the event from the message queue and forward the request to [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) or [Apple Push Notification Service (APNS)](https://developer.apple.com/documentation/usernotifications) based on the client's device platform (Android, iOS, web, etc). We can also add support for email and SMS.

**Why are we using a message queue?**

Since most message queues provide best-effort ordering which ensures that messages are generally delivered in the same order as they're sent and that a message is delivered at least once which is an important part of our service functionality.

While this seems like a classic [publish-subscribe](https://karanpratapsingh.com/courses/system-design/publish-subscribe) use case, it is actually not as mobile devices and browsers each have their own way of handling push notifications. Usually, notifications are handled externally via Firebase Cloud Messaging (FCM) or Apple Push Notification Service (APNS) unlike message fan-out which we commonly see in backend services. We can use something like [Amazon SQS](https://aws.amazon.com/sqs) or [RabbitMQ](https://www.rabbitmq.com) to support this functionality.

### Read receipts

Handling read receipts can be tricky, for this use case we can wait for some sort of [Acknowledgment (ACK)](<https://en.wikipedia.org/wiki/Acknowledgement_(data_networks)>) from the client to determine if the message was delivered and update the corresponding `deliveredAt` field. Similarly, we will mark the message as seen once the user opens the chat and update the corresponding `seenAt` timestamp field.

### Design

Now that we have identified some core components, let's do the first draft of our system design.

![whatsapp-basic-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-basic-design.png)

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

- Hash-Based Partitioning
- List-Based Partitioning
- Range Based Partitioning
- Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Caching

In a messaging application, we have to be careful about using cache as our users expect the latest data, but many users will be requesting the same messages, especially in a group chat. So, to prevent usage spikes from our resources we can cache older messages.

Some group chats can have thousands of messages and sending that over the network will be really inefficient, to improve efficiency we can add pagination to our system APIs. This decision will be helpful for users with limited network bandwidth as they won't have to retrieve old messages unless requested.

**Which cache eviction policy to use?**

We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) and cache 20% of the daily traffic but what kind of cache eviction policy would best fit our needs?

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

### Media access and storage

As we know, most of our storage space will be used for storing media files such as images, videos, or other files. Our media service will be handling both access and storage of the user media files.

But where can we store files at scale? Well, [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) is what we're looking for. Object stores break data files up into pieces called objects. It then stores those objects in a single repository, which can be spread out across multiple networked systems. We can also use distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs) or [GlusterFS](https://www.gluster.org).

_Fun fact: WhatsApp deletes media on its servers once it has been downloaded by the user._

We can use object stores like [Amazon S3](https://aws.amazon.com/s3), [Azure Blob Storage](https://azure.microsoft.com/en-in/services/storage/blobs), or [Google Cloud Storage](https://cloud.google.com/storage) for this use case.

### Content Delivery Network (CDN)

[Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) increases content availability and redundancy while reducing bandwidth costs. Generally, static files such as images, and videos are served from CDN. We can use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) or [Cloudflare CDN](https://www.cloudflare.com/cdn) for this use case.

### API gateway

Since we will be using multiple protocols like HTTP, WebSocket, TCP/IP, deploying multiple L4 (transport layer) or L7 (application layer) type load balancers separately for each protocol will be expensive. Instead, we can use an [API Gateway](https://karanpratapsingh.com/courses/system-design/api-gateway) that supports multiple protocols without any issues.

API Gateway can also offer other features such as authentication, authorization, rate limiting, throttling, and API versioning which will improve the quality of our services.

We can use services like [Amazon API Gateway](https://aws.amazon.com/api-gateway) or [Azure API Gateway](https://azure.microsoft.com/en-in/services/api-management) for this use case.

## Identify and resolve bottlenecks

![whatsapp-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/whatsapp/whatsapp-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if one of our services crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "How to improve the availability of our cache?"
- "Wouldn't API Gateway be a single point of failure?"
- "How can we make our notification system more robust?"
- "How can we reduce media storage costs"?
- "Does chat service has too much responsibility?"

To make our system more resilient we can do the following:

- Running multiple instances of each of our services.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our databases.
- Multiple instances and replicas for our distributed cache.
- We can have a standby replica of our API Gateway.
- Exactly once delivery and message ordering is challenging in a distributed system, we can use a dedicated [message broker](https://karanpratapsingh.com/courses/system-design/message-brokers) such as [Apache Kafka](https://kafka.apache.org) or [NATS](https://nats.io) to make our notification system more robust.
- We can add media processing and compression capabilities to the media service to compress large files similar to WhatsApp which will save a lot of storage space and reduce cost.
- We can create a group service separate from the chat service to further decouple our services.

# Twitter

Let's design a [Twitter](https://twitter.com) like social media service, similar to services like [Facebook](https://facebook.com), [Instagram](https://instagram.com), etc.

## What is Twitter?

Twitter is a social media service where users can read or post short messages (up to 280 characters) called tweets. It is available on the web and mobile platforms such as Android and iOS.

## Requirements

Our system should meet the following requirements:

### Functional requirements

- Should be able to post new tweets (can be text, image, video, etc.).
- Should be able to follow other users.
- Should have a newsfeed feature consisting of tweets from the people the user is following.
- Should be able to search tweets.

### Non-Functional requirements

- High availability with minimal latency.
- The system should be scalable and efficient.

### Extended requirements

- Metrics and analytics.
- Retweet functionality.
- Favorite tweets.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

This will be a read-heavy system, let us assume we have 1 billion total users with 200 million daily active users (DAU), and on average each user tweets 5 times a day. This gives us 1 billion tweets per day.

$$
200 \space million \times 5 \space tweets = 1 \space billion/day
$$

Tweets can also contain media such as images, or videos. We can assume that 10 percent of tweets are media files shared by the users, which gives us additional 100 million files we would need to store.

$$
10 \space percent \times 1 \space billion = 100 \space million/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each message on average is 100 bytes, we will require about 100 GB of database storage every day.

$$
1 \space billion \times 100 \space bytes = \sim 100 \space GB/day
$$

We also know that around 10 percent of our daily messages (100 million) are media files per our requirements. If we assume each file is 50 KB on average, we will require 5 TB of storage every day.

$$
100 \space million \times 100 \space KB = 5 \space TB/day
$$

And for 10 years, we will require about 19 PB of storage.

$$
(5 \space TB + 0.1 \space TB) \times 365 \space days \times 10 \space years = \sim 19 \space PB
$$

### Bandwidth

As our system is handling 5.1 TB of ingress every day, we will require a minimum bandwidth of around 60 MB per second.

$$
\frac{5.1 \space TB}{(24 \space hrs \times 3600 \space seconds)} = \sim 60 \space MB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 100 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~5.1 TB     |
| Storage (10 years)        | ~19 PB      |
| Bandwidth                 | ~60 MB/s    |

## Data model design

This is the general data model which reflects our requirements.

![twitter-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/twitter/twitter-datamodel.png)

We have the following tables:

**users**

This table will contain a user's information such as `name`, `email`, `dob`, and other details.

**tweets**

As the name suggests, this table will store tweets and their properties such as `type` (text, image, video, etc.), `content`, etc. We will also store the corresponding `userID`.

**favorites**

This table maps tweets with users for the favorite tweets functionality in our application.

**followers**

This table maps the followers and [followees](https://en.wiktionary.org/wiki/followee) as users can follow each other (N:M relationship).

**feeds**

This table stores feed properties with the corresponding `userID`.

**feeds_tweets**

This table maps tweets and feed (N:M relationship).

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Post a tweet

This API will allow the user to post a tweet on the platform.

```tsx
postTweet(userID: UUID, content: string, mediaURL?: string): boolean
```

**Parameters**

User ID (`UUID`): ID of the user.

Content (`string`): Contents of the tweet.

Media URL (`string`): URL of the attached media _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Follow or unfollow a user

This API will allow the user to follow or unfollow another user.

```tsx
follow(followerID: UUID, followeeID: UUID): boolean
unfollow(followerID: UUID, followeeID: UUID): boolean
```

**Parameters**

Follower ID (`UUID`): ID of the current user.

Followee ID (`UUID`): ID of the user we want to follow or unfollow.

Media URL (`string`): URL of the attached media _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Get newsfeed

This API will return all the tweets to be shown within a given newsfeed.

```tsx
getNewsfeed(userID: UUID): Tweet[]
```

**Parameters**

User ID (`UUID`): ID of the user.

**Returns**

Tweets (`Tweet[]`): All the tweets to be shown within a given newsfeed.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**User Service**

This service handles user-related concerns such as authentication and user information.

**Newsfeed Service**

This service will handle the generation and publishing of user newsfeeds. It will be discussed in detail separately.

**Tweet Service**

The tweet service will handle tweet-related use cases such as posting a tweet, favorites, etc.

**Search Service**

The service is responsible for handling search-related functionality. It will be discussed in detail separately.

**Media service**

This service will handle the media (images, videos, files, etc.) uploads. It will be discussed in detail separately.

**Notification Service**

This service will simply send push notifications to the users.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### Newsfeed

When it comes to the newsfeed, it seems easy enough to implement, but there are a lot of things that can make or break this feature. So, let's divide our problem into two parts:

**Generation**

Let's assume we want to generate the feed for user A, we will perform the following steps:

1. Retrieve the IDs of all the users and entities (hashtags, topics, etc.) user A follows.
2. Fetch the relevant tweets for each of the retrieved IDs.
3. Use a ranking algorithm to rank the tweets based on parameters such as relevance, time, engagement, etc.
4. Return the ranked tweets data to the client in a paginated manner.

Feed generation is an intensive process and can take quite a lot of time, especially for users following a lot of people. To improve the performance, the feed can be pre-generated and stored in the cache, then we can have a mechanism to periodically update the feed and apply our ranking algorithm to the new tweets.

**Publishing**

Publishing is the step where the feed data is pushed according to each specific user. This can be a quite heavy operation, as a user may have millions of friends or followers. To deal with this, we have three different approaches:

- Pull Model (or Fan-out on load)

![newsfeed-pull-model](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/twitter/newsfeed-pull-model.png)

When a user creates a tweet, and a follower reloads their newsfeed, the feed is created and stored in memory. The most recent feed is only loaded when the user requests it. This approach reduces the number of write operations on our database.

The downside of this approach is that the users will not be able to view recent feeds unless they "pull" the data from the server, which will increase the number of read operations on the server.

- Push Model (or Fan-out on write)

![newsfeed-push-model](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/twitter/newsfeed-push-model.png)

In this model, once a user creates a tweet, it is "pushed" to all the follower's feeds immediately. This prevents the system from having to go through a user's entire followers list to check for updates.

However, the downside of this approach is that it would increase the number of write operations on the database.

- Hybrid Model

A third approach is a hybrid model between the pull and push model. It combines the beneficial features of the above two models and tries to provide a balanced approach between the two.

The hybrid model allows only users with a lesser number of followers to use the push model. For users with a higher number of followers such as celebrities, the pull model is used.

### Ranking Algorithm

As we discussed, we will need a ranking algorithm to rank each tweet according to its relevance to each specific user.

For example, Facebook used to utilize an [EdgeRank](https://en.wikipedia.org/wiki/EdgeRank) algorithm. Here, the rank of each feed item is described by:

$$
Rank = Affinity \times Weight \times Decay
$$

Where,

`Affinity`: is the "closeness" of the user to the creator of the edge. If a user frequently likes, comments, or messages the edge creator, then the value of affinity will be higher, resulting in a higher rank for the post.

`Weight`: is the value assigned according to each edge. A comment can have a higher weightage than likes, and thus a post with more comments is more likely to get a higher rank.

`Decay`: is the measure of the creation of the edge. The older the edge, the lesser will be the value of decay and eventually the rank.

Nowadays, algorithms are much more complex and ranking is done using machine learning models which can take thousands of factors into consideration.

### Retweets

Retweets are one of our extended requirements. To implement this feature, we can simply create a new tweet with the user id of the user retweeting the original tweet and then modify the `type` enum and `content` property of the new tweet to link it with the original tweet.

For example, the `type` enum property can be of type tweet, similar to text, video, etc and `content` can be the id of the original tweet. Here the first row indicates the original tweet while the second row is how we can represent a retweet.

| id                  | userID              | type  | content                      | createdAt     |
| ------------------- | ------------------- | ----- | ---------------------------- | ------------- |
| ad34-291a-45f6-b36c | 7a2c-62c4-4dc8-b1bb | text  | Hey, this is my first tweet… | 1658905644054 |
| f064-49ad-9aa2-84a6 | 6aa2-2bc9-4331-879f | tweet | ad34-291a-45f6-b36c          | 1658906165427 |

This is a very basic implementation. To improve this we can create a separate table itself to store retweets.

### Search

Sometimes traditional DBMS are not performant enough, we need something which allows us to store, search, and analyze huge volumes of data quickly and in near real-time and give results within milliseconds. [Elasticsearch](https://www.elastic.co) can help us with this use case.

[Elasticsearch](https://www.elastic.co) is a distributed, free and open search and analytics engine for all types of data, including textual, numerical, geospatial, structured, and unstructured. It is built on top of [Apache Lucene](https://lucene.apache.org).

**How do we identify trending topics?**

Trending functionality will be based on top of the search functionality. We can cache the most frequently searched queries, hashtags, and topics in the last `N` seconds and update them every `M` seconds using some sort of batch job mechanism. Our ranking algorithm can also be applied to the trending topics to give them more weight and personalize them for the user.

### Notifications

Push notifications are an integral part of any social media platform. We can use a message queue or a message broker such as [Apache Kafka](https://kafka.apache.org) with the notification service to dispatch requests to [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) or [Apple Push Notification Service (APNS)](https://developer.apple.com/documentation/usernotifications) which will handle the delivery of the push notifications to user devices.

_For more details, refer to the [WhatsApp](https://karanpratapsingh.com/courses/system-design/whatsapp#notifications) system design where we discuss push notifications in detail._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

- Hash-Based Partitioning
- List-Based Partitioning
- Range Based Partitioning
- Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Mutual friends

For mutual friends, we can build a social graph for every user. Each node in the graph will represent a user and a directional edge will represent followers and followees. After that, we can traverse the followers of a user to find and suggest a mutual friend. This would require a graph database such as [Neo4j](https://neo4j.com) and [ArangoDB](https://www.arangodb.com).

This is a pretty simple algorithm, to improve our suggestion accuracy, we will need to incorporate a recommendation model which uses machine learning as part of our algorithm.

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. As we will be using [Apache Kafka](https://kafka.apache.org) to publish all sorts of events, we can process these events and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing.

### Caching

In a social media application, we have to be careful about using cache as our users expect the latest data. So, to prevent usage spikes from our resources we can cache the top 20% of the tweets.

To further improve efficiency we can add pagination to our system APIs. This decision will be helpful for users with limited network bandwidth as they won't have to retrieve old messages unless requested.

**Which cache eviction policy to use?**

We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) and cache 20% of the daily traffic but what kind of cache eviction policy would best fit our needs?

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

### Media access and storage

As we know, most of our storage space will be used for storing media files such as images, videos, or other files. Our media service will be handling both access and storage of the user media files.

But where can we store files at scale? Well, [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) is what we're looking for. Object stores break data files up into pieces called objects. It then stores those objects in a single repository, which can be spread out across multiple networked systems. We can also use distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs) or [GlusterFS](https://www.gluster.org).

### Content Delivery Network (CDN)

[Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) increases content availability and redundancy while reducing bandwidth costs. Generally, static files such as images, and videos are served from CDN. We can use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) or [Cloudflare CDN](https://www.cloudflare.com/cdn) for this use case.

## Identify and resolve bottlenecks

![twitter-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/twitter/twitter-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if one of our services crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "How to improve the availability of our cache?"
- "How can we make our notification system more robust?"
- "How can we reduce media storage costs"?

To make our system more resilient we can do the following:

- Running multiple instances of each of our services.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our databases.
- Multiple instances and replicas for our distributed cache.
- Exactly once delivery and message ordering is challenging in a distributed system, we can use a dedicated [message broker](https://karanpratapsingh.com/courses/system-design/message-brokers) such as [Apache Kafka](https://kafka.apache.org) or [NATS](https://nats.io) to make our notification system more robust.
- We can add media processing and compression capabilities to the media service to compress large files which will save a lot of storage space and reduce cost.

# Netflix

Let's design a [Netflix](https://netflix.com) like video streaming service, similar to services like [Amazon Prime Video](https://www.primevideo.com), [Disney Plus](https://www.disneyplus.com), [Hulu](https://www.hulu.com), [Youtube](https://youtube.com), [Vimeo](https://vimeo.com), etc.

## What is Netflix?

Netflix is a subscription-based streaming service that allows its members to watch TV shows and movies on an internet-connected device. It is available on platforms such as the Web, iOS, Android, TV, etc.

## Requirements

Our system should meet the following requirements:

### Functional requirements

- Users should be able to stream and share videos.
- The content team (or users in YouTube's case) should be able to upload new videos (movies, tv shows episodes, and other content).
- Users should be able to search for videos using titles or tags.
- Users should be able to comment on a video similar to YouTube.

### Non-Functional requirements

- High availability with minimal latency.
- High reliability, no uploads should be lost.
- The system should be scalable and efficient.

### Extended requirements

- Certain content should be [geo-blocked](https://en.wikipedia.org/wiki/Geo-blocking).
- Resume video playback from the point user left off.
- Record metrics and analytics of videos.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

This will be a read-heavy system, let us assume we have 1 billion total users with 200 million daily active users (DAU), and on average each user watches 5 videos a day. This gives us 1 billion videos watched per day.

$$
200 \space million \times 5 \space videos = 1 \space billion/day
$$

Assuming a `200:1` read/write ratio, about 50 million videos will be uploaded every day.

$$
\frac{1}{200} \times 1 \space billion = 50 \space million/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each video is 100 MB on average, we will require about 5 PB of storage every day.

$$
50 \space million \times 100 \space MB = 5 \space PB/day
$$

And for 10 years, we will require an astounding 18,250 PB of storage.

$$
5 \space PB \times 365 \space days \times 10 \space years = \sim 18,250 \space PB
$$

### Bandwidth

As our system is handling 5 PB of ingress every day, we will require a minimum bandwidth of around 58 GB per second.

$$
\frac{5 \space PB}{(24 \space hrs \times 3600 \space seconds)} = \sim 58 \space GB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 200 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~5 PB       |
| Storage (10 years)        | ~18,250 PB  |
| Bandwidth                 | ~58 GB/s    |

## Data model design

This is the general data model which reflects our requirements.

![netflix-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/netflix-datamodel.png)

We have the following tables:

**users**

This table will contain a user's information such as `name`, `email`, `dob`, and other details.

**videos**

As the name suggests, this table will store videos and their properties such as `title`, `streamURL`, `tags`, etc. We will also store the corresponding `userID`.

**tags**

This table will simply store tags associated with a video.

**views**

This table helps us to store all the views received on a video.

**comments**

This table stores all the comments received on a video (like YouTube).

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Upload a video

Given a byte stream, this API enables video to be uploaded to our service.

```tsx
uploadVideo(title: string, description: string, data: Stream<byte>, tags?: string[]): boolean
```

**Parameters**

Title (`string`): Title of the new video.

Description (`string`): Description of the new video.

Data (`Byte[]`): Byte stream of the video data.

Tags (`string[]`): Tags for the video _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Streaming a video

This API allows our users to stream a video with the preferred codec and resolution.

```tsx
streamVideo(videoID: UUID, codec: Enum<string>, resolution: Tuple<int>, offset?: int): VideoStream
```

**Parameters**

Video ID (`UUID`): ID of the video that needs to be streamed.

Codec (`Enum<string>`): Required [codec](https://en.wikipedia.org/wiki/Video_codec) of the requested video, such as `h.265`, `h.264`, `VP9`, etc.

Resolution (`Tuple<int>`): [Resolution](https://en.wikipedia.org/wiki/Display_resolution) of the requested video.

Offset (`int`): Offset of the video stream in seconds to stream data from any point in the video _(optional)_.

**Returns**

Stream (`VideoStream`): Data stream of the requested video.

### Search for a video

This API will enable our users to search for a video based on its title or tags.

```tsx
searchVideo(query: string, nextPage?: string): Video[]
```

**Parameters**

Query (`string`): Search query from the user.

Next Page (`string`): Token for the next page, this can be used for pagination _(optional)_.

**Returns**

Videos (`Video[]`): All the videos available for a particular search query.

### Add a comment

This API will allow our users to post a comment on a video (like YouTube).

```tsx
comment(videoID: UUID, comment: string): boolean
```

**Parameters**

VideoID (`UUID`): ID of the video user wants to comment on.

Comment (`string`): The text content of the comment.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**User Service**

This service handles user-related concerns such as authentication and user information.

**Stream Service**

The tweet service will handle video streaming-related functionality.

**Search Service**

The service is responsible for handling search-related functionality. It will be discussed in detail separately.

**Media service**

This service will handle the video uploads and processing. It will be discussed in detail separately.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### Video processing

![video-processing-pipeline](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/video-processing-pipeline.png)

There are so many variables in play when it comes to processing a video. For example, an average data size of two-hour raw 8K footage from a high-end camera can easily be up to 4 TB, thus we need to have some kind of processing to reduce both storage and delivery costs.

Here's how we can process videos once they're uploaded by the content team (or users in YouTube's case) and are queued for processing in our [message queue](https://karanpratapsingh.com/courses/system-design/message-queues).

Let's discuss how this works:

- **File Chunker**

![file-chunking](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/file-chunking.png)

This is the first step of our processing pipeline. File chunking is the process of splitting a file into smaller pieces called chunks. It can help us eliminate duplicate copies of repeating data on storage, and reduces the amount of data sent over the network by only selecting changed chunks.

Usually, a video file can be split into equal size chunks based on timestamps but Netflix instead splits chunks based on scenes. This slight variation becomes a huge factor for a better user experience since whenever the client requests a chunk from the server, there is a lower chance of interruption as a complete scene will be retrieved.

- **Content Filter**

This step checks if the video adheres to the content policy of the platform. This can be pre-approved as in the case of Netflix according to [content rating](https://en.wikipedia.org/wiki/Motion_picture_content_rating_system) of the media or can be strictly enforced like by YouTube.

This entire process is done by a machine learning model which performs copyright, piracy, and NSFW checks. If issues are found, we can push the task to a [dead-letter queue (DLQ)](https://karanpratapsingh.com/courses/system-design/message-queues#dead-letter-queues) and someone from the moderation team can do further inspection.

- **Transcoder**

[Transcoding](https://en.wikipedia.org/wiki/Transcoding) is a process in which the original data is decoded to an intermediate uncompressed format, which is then encoded into the target format. This process uses different [codecs](https://en.wikipedia.org/wiki/Video_codec) to perform bitrate adjustment, image downsampling, or re-encoding the media.

This results in a smaller size file and a much more optimized format for the target devices. Standalone solutions such as [FFmpeg](https://ffmpeg.org) or cloud-based solutions like [AWS Elemental MediaConvert](https://aws.amazon.com/mediaconvert) can be used to implement this step of the pipeline.

- **Quality Conversion**

This is the last step of the processing pipeline and as the name suggests, this step handles the conversion of the transcoded media from the previous step into different resolutions such as 4K, 1440p, 1080p, 720p, etc.

It allows us to fetch the desired quality of the video as per the user's request, and once the media file finishes processing, it gets uploaded to a distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs), [GlusterFS](https://www.gluster.org), or an [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) such as [Amazon S3](https://aws.amazon.com/s3) for later retrieval during streaming.

_Note: We can add additional steps such as subtitles and thumbnails generation as part of our pipeline._

**Why are we using a message queue?**

Processing videos as a long-running task and using a [message queue](https://karanpratapsingh.com/courses/system-design/message-queues) makes much more sense. It also decouples our video processing pipeline from the upload functionality. We can use something like [Amazon SQS](https://aws.amazon.com/sqs) or [RabbitMQ](https://www.rabbitmq.com) to support this.

### Video streaming

Video streaming is a challenging task from both the client and server perspectives. Moreover, internet connection speeds vary quite a lot between different users. To make sure users don't re-fetch the same content, we can use a [Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network).

Netflix takes this a step further with its [Open Connect](https://openconnect.netflix.com) program. In this approach, they partner with thousands of Internet Service Providers (ISPs) to localize their traffic and deliver their content more efficiently.

**What is the difference between Netflix's Open Connect and a traditional Content Delivery Network (CDN)?**

Netflix Open Connect is a purpose-built [Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) responsible for serving Netflix's video traffic. Around 95% of the traffic globally is delivered via direct connections between Open Connect and the ISPs their customers use to access the internet.

Currently, they have Open Connect Appliances (OCAs) in over 1000 separate locations around the world. In case of issues, Open Connect Appliances (OCAs) can failover, and the traffic can be re-routed to Netflix servers.

Additionally, we can use [Adaptive bitrate streaming](https://en.wikipedia.org/wiki/Adaptive_bitrate_streaming) protocols such as [HTTP Live Streaming (HLS)](https://en.wikipedia.org/wiki/HTTP_Live_Streaming) which is designed for reliability and it dynamically adapts to network conditions by optimizing playback for the available speed of the connections.

Lastly, for playing the video from where the user left off (part of our extended requirements), we can simply use the `offset` property we stored in the `views` table to retrieve the scene chunk at that particular timestamp and resume the playback for the user.

### Searching

Sometimes traditional DBMS are not performant enough, we need something which allows us to store, search, and analyze huge volumes of data quickly and in near real-time and give results within milliseconds. [Elasticsearch](https://www.elastic.co) can help us with this use case.

[Elasticsearch](https://www.elastic.co) is a distributed, free and open search and analytics engine for all types of data, including textual, numerical, geospatial, structured, and unstructured. It is built on top of [Apache Lucene](https://lucene.apache.org).

**How do we identify trending content?**

Trending functionality will be based on top of the search functionality. We can cache the most frequently searched queries in the last `N` seconds and update them every `M` seconds using some sort of batch job mechanism.

### Sharing

Sharing content is an important part of any platform, for this, we can have some sort of URL shortener service in place that can generate short URLs for the users to share.

_For more details, refer to the [URL Shortener](https://karanpratapsingh.com/courses/system-design/url-shortener) system design._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can use partitions schemes such as:

- Hash-Based Partitioning
- List-Based Partitioning
- Range Based Partitioning
- Composite Partitioning

The above approaches can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Geo-blocking

Platforms like Netflix and YouTube use [Geo-blocking](https://en.wikipedia.org/wiki/Geo-blocking) to restrict content in certain geographical areas or countries. This is primarily done due to legal distribution laws that Netflix has to adhere to when they make a deal with the production and distribution companies. In the case of YouTube, this will be controlled by the user during the publishing of the content.

We can determine the user's location either using their [IP](https://karanpratapsingh.com/courses/system-design/ip) or region settings in their profile then use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) which supports a geographic restrictions feature or a [geolocation routing policy](https://docs.aws.amazon.com/Route53/latest/DeveloperGuide/routing-policy-geo.html) with [Amazon Route53](https://aws.amazon.com/route53) to restrict the content and re-route the user to an error page if the content is not available in that particular region or country.

### Recommendations

Netflix uses a machine learning model which uses the user's viewing history to predict what the user might like to watch next, an algorithm like [Collaborative Filtering](https://en.wikipedia.org/wiki/Collaborative_filtering) can be used.

However, Netflix (like YouTube) uses its own algorithm called Netflix Recommendation Engine which can track several data points such as:

- User profile information like age, gender, and location.
- Browsing and scrolling behavior of the user.
- Time and date a user watched a title.
- The device which was used to stream the content.
- The number of searches and what terms were searched.

_For more detail, refer to [Netflix recommendation research](https://research.netflix.com/research-area/recommendations)._

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can capture the data from different services and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing. Additionally, we can store critical metadata in the views table to increase data points within our data.

### Caching

In a streaming platform, caching is important. We have to be able to cache as much static media content as possible to improve user experience. We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) but what kind of cache eviction policy would best fit our needs?

**Which cache eviction policy to use?**

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

### Media streaming and storage

As most of our storage space will be used for storing media files such as thumbnails and videos. Per our discussion earlier, the media service will be handling both the upload and processing of media files.

We will use distributed file storage such as [HDFS](https://karanpratapsingh.com/courses/system-design/storage#hdfs), [GlusterFS](https://www.gluster.org), or an [object storage](https://karanpratapsingh.com/courses/system-design/storage#object-storage) such as [Amazon S3](https://aws.amazon.com/s3) for storage and streaming of the content.

### Content Delivery Network (CDN)

[Content Delivery Network (CDN)](https://karanpratapsingh.com/courses/system-design/content-delivery-network) increases content availability and redundancy while reducing bandwidth costs. Generally, static files such as images, and videos are served from CDN. We can use services like [Amazon CloudFront](https://aws.amazon.com/cloudfront) or [Cloudflare CDN](https://www.cloudflare.com/cdn) for this use case.

## Identify and resolve bottlenecks

![netflix-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/netflix/netflix-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if one of our services crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "How to improve the availability of our cache?"

To make our system more resilient we can do the following:

- Running multiple instances of each of our services.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our databases.
- Multiple instances and replicas for our distributed cache.

# Uber

Let's design an [Uber](https://uber.com) like ride-hailing service, similar to services like [Lyft](https://www.lyft.com), [OLA Cabs](https://www.olacabs.com), etc.

## What is Uber?

Uber is a mobility service provider, allowing users to book rides and a driver to transport them in a way similar to a taxi. It is available on the web and mobile platforms such as Android and iOS.

## Requirements

Our system should meet the following requirements:

### Functional requirements

We will design our system for two types of users: Customers and Drivers.

**Customers**

- Customers should be able to see all the cabs in the vicinity with an ETA and pricing information.
- Customers should be able to book a cab to a destination.
- Customers should be able to see the location of the driver.

**Drivers**

- Drivers should be able to accept or deny the customer-requested ride.
- Once a driver accepts the ride, they should see the pickup location of the customer.
- Drivers should be able to mark the trip as complete on reaching the destination.

### Non-Functional requirements

- High reliability.
- High availability with minimal latency.
- The system should be scalable and efficient.

### Extended requirements

- Customers can rate the trip after it's completed.
- Payment processing.
- Metrics and analytics.

## Estimation and Constraints

Let's start with the estimation and constraints.

_Note: Make sure to check any scale or traffic-related assumptions with your interviewer._

### Traffic

Let us assume we have 100 million daily active users (DAU) with 1 million drivers and on average our platform enables 10 million rides daily.

If on average each user performs 10 actions (such as request a check available rides, fares, book rides, etc.) we will have to handle 1 billion requests daily.

$$
100 \space million \times 10 \space actions = 1 \space billion/day
$$

**What would be Requests Per Second (RPS) for our system?**

1 billion requests per day translate into 12K requests per second.

$$
\frac{1 \space billion}{(24 \space hrs \times 3600 \space seconds)} = \sim 12K \space requests/second
$$

### Storage

If we assume each message on average is 400 bytes, we will require about 400 GB of database storage every day.

$$
1 \space billion \times 400 \space bytes = \sim 400 \space GB/day
$$

And for 10 years, we will require about 1.4 PB of storage.

$$
400 \space GB \times 10 \space years \times 365 \space days = \sim 1.4 \space PB
$$

### Bandwidth

As our system is handling 400 GB of ingress every day, we will require a minimum bandwidth of around 4 MB per second.

$$
\frac{400 \space GB}{(24 \space hrs \times 3600 \space seconds)} = \sim 5 \space MB/second
$$

### High-level estimate

Here is our high-level estimate:

| Type                      | Estimate    |
| ------------------------- | ----------- |
| Daily active users (DAU)  | 100 million |
| Requests per second (RPS) | 12K/s       |
| Storage (per day)         | ~400 GB     |
| Storage (10 years)        | ~1.4 PB     |
| Bandwidth                 | ~5 MB/s     |

## Data model design

This is the general data model which reflects our requirements.

![uber-datamodel](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-datamodel.png)

We have the following tables:

**customers**

This table will contain a customer's information such as `name`, `email`, and other details.

**drivers**

This table will contain a driver's information such as `name`, `email`, `dob` and other details.

**trips**

This table represents the trip taken by the customer and stores data such as `source`, `destination`, and `status` of the trip.

**cabs**

This table stores data such as the registration number, and type (like Uber Go, Uber XL, etc.) of the cab that the driver will be driving.

**ratings**

As the name suggests, this table stores the `rating` and `feedback` for the trip.

**payments**

The payments table contains the payment-related data with the corresponding `tripID`.

### What kind of database should we use?

While our data model seems quite relational, we don't necessarily need to store everything in a single database, as this can limit our scalability and quickly become a bottleneck.

We will split the data between different services each having ownership over a particular table. Then we can use a relational database such as [PostgreSQL](https://www.postgresql.org) or a distributed NoSQL database such as [Apache Cassandra](https://cassandra.apache.org/_/index.html) for our use case.

## API design

Let us do a basic API design for our services:

### Request a Ride

Through this API, customers will be able to request a ride.

```tsx
requestRide(customerID: UUID, source: Tuple<float>, destination: Tuple<float>, cabType: Enum<string>, paymentMethod: Enum<string>): Ride
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Source (`Tuple<float>`): Tuple containing the latitude and longitude of the trip's starting location.

Destination (`Tuple<float>`): Tuple containing the latitude and longitude of the trip's destination.

**Returns**

Result (`Ride`): Associated ride information of the trip.

### Cancel the Ride

This API will allow customers to cancel the ride.

```tsx
cancelRide(customerID: UUID, reason?: string): boolean
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Reason (`UUID`): Reason for canceling the ride _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Accept or Deny the Ride

This API will allow the driver to accept or deny the trip.

```tsx
acceptRide(driverID: UUID, rideID: UUID): boolean
denyRide(driverID: UUID, rideID: UUID): boolean
```

**Parameters**

Driver ID (`UUID`): ID of the driver.

Ride ID (`UUID`): ID of the customer requested ride.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Start or End the Trip

Using this API, a driver will be able to start and end the trip.

```tsx
startTrip(driverID: UUID, tripID: UUID): boolean
endTrip(driverID: UUID, tripID: UUID): boolean
```

**Parameters**

Driver ID (`UUID`): ID of the driver.

Trip ID (`UUID`): ID of the requested trip.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

### Rate the Trip

This API will enable customers to rate the trip.

```tsx
rateTrip(customerID: UUID, tripID: UUID, rating: int, feedback?: string): boolean
```

**Parameters**

Customer ID (`UUID`): ID of the customer.

Trip ID (`UUID`): ID of the completed trip.

Rating (`int`): Rating of the trip.

Feedback (`string`): Feedback about the trip by the customer _(optional)_.

**Returns**

Result (`boolean`): Represents whether the operation was successful or not.

## High-level design

Now let us do a high-level design of our system.

### Architecture

We will be using [microservices architecture](https://karanpratapsingh.com/courses/system-design/monoliths-microservices#microservices) since it will make it easier to horizontally scale and decouple our services. Each service will have ownership of its own data model. Let's try to divide our system into some core services.

**Customer Service**

This service handles customer-related concerns such as authentication and customer information.

**Driver Service**

This service handles driver-related concerns such as authentication and driver information.

**Ride Service**

This service will be responsible for ride matching and quadtree aggregation. It will be discussed in detail separately.

**Trip Service**

This service handles trip-related functionality in our system.

**Payment Service**

This service will be responsible for handling payments in our system.

**Notification Service**

This service will simply send push notifications to the users. It will be discussed in detail separately.

**Analytics Service**

This service will be used for metrics and analytics use cases.

**What about inter-service communication and service discovery?**

Since our architecture is microservices-based, services will be communicating with each other as well. Generally, REST or HTTP performs well but we can further improve the performance using [gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc#grpc) which is more lightweight and efficient.

[Service discovery](https://karanpratapsingh.com/courses/system-design/service-discovery) is another thing we will have to take into account. We can also use a service mesh that enables managed, observable, and secure communication between individual services.

_Note: Learn more about [REST, GraphQL, gRPC](https://karanpratapsingh.com/courses/system-design/rest-graphql-grpc) and how they compare with each other._

### How is the service expected to work?

Here's how our service is expected to work:

![uber-working](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-working.png)

1. Customer requests a ride by specifying the source, destination, cab type, payment method, etc.
2. Ride service registers this request, finds nearby drivers, and calculates the estimated time of arrival (ETA).
3. The request is then broadcasted to the nearby drivers for them to accept or deny.
4. If the driver accepts, the customer is notified about the live location of the driver with the estimated time of arrival (ETA) while they wait for pickup.
5. The customer is picked up and the driver can start the trip.
6. Once the destination is reached, the driver will mark the ride as complete and collect payment.
7. After the payment is complete, the customer can leave a rating and feedback for the trip if they like.

### Location Tracking

How do we efficiently send and receive live location data from the client (customers and drivers) to our backend? We have two different options:

**Pull model**

The client can periodically send an HTTP request to servers to report its current location and receive ETA and pricing information. This can be achieved via something like [Long polling](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#long-polling).

**Push model**

The client opens a long-lived connection with the server and once new data is available it will be pushed to the client. We can use [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) or [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) for this.

The pull model approach is not scalable as it will create unnecessary request overhead on our servers and most of the time the response will be empty, thus wasting our resources. To minimize latency, using the push model with [WebSockets](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#websockets) is a better choice because then we can push data to the client once it's available without any delay, given the connection is open with the client. Also, WebSockets provide full-duplex communication, unlike [Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events#server-sent-events-sse) which are only unidirectional.

Additionally, the client application should have some sort of background job mechanism to ping GPS location while the application is in the background.

_Note: Learn more about [Long polling, WebSockets, Server-Sent Events (SSE)](https://karanpratapsingh.com/courses/system-design/long-polling-websockets-server-sent-events)._

### Ride Matching

We need a way to efficiently store and query nearby drivers. Let's explore different solutions we can incorporate into our design.

**SQL**

We already have access to the latitude and longitude of our customers, and with databases like [PostgreSQL](https://www.postgresql.org) and [MySQL](https://www.mysql.com) we can perform a query to find nearby driver locations given a latitude and longitude (X, Y) within a radius (R).

```sql
SELECT * FROM locations WHERE lat BETWEEN X-R AND X+R AND long BETWEEN Y-R AND Y+R
```

However, this is not scalable, and performing this query on large datasets will be quite slow.

**Geohashing**

[Geohashing](/courses/sytem-design/geohashing-and-quadtrees#geohashing) is a [geocoding](https://en.wikipedia.org/wiki/Address_geocoding) method used to encode geographic coordinates such as latitude and longitude into short alphanumeric strings. It was created by [Gustavo Niemeyer](https://twitter.com/gniemeyer) in 2008.

Geohash is a hierarchical spatial index that uses Base-32 alphabet encoding, the first character in a geohash identifies the initial location as one of the 32 cells. This cell will also contain 32 cells. This means that to represent a point, the world is recursively divided into smaller and smaller cells with each additional bit until the desired precision is attained. The precision factor also determines the size of the cell.

![geohashing](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/geohashing.png)

For example, San Francisco with coordinates `37.7564, -122.4016` can be represented in geohash as `9q8yy9mf`.

Now, using the customer's geohash we can determine the nearest available driver by simply comparing it with the driver's geohash. For better performance, we will index and store the geohash of the driver in memory for faster retrieval.

**Quadtrees**

A [Quadtree](/courses/sytem-design/geohashing-and-quadtrees#quadtrees) is a tree data structure in which each internal node has exactly four children. They are often used to partition a two-dimensional space by recursively subdividing it into four quadrants or regions. Each child or leaf node stores spatial information. Quadtrees are the two-dimensional analog of [Octrees](https://en.wikipedia.org/wiki/Octree) which are used to partition three-dimensional space.

![quadtree](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree.png)

Quadtrees enable us to search points within a two-dimensional range efficiently, where those points are defined as latitude/longitude coordinates or as cartesian (x, y) coordinates.

We can save further computation by only subdividing a node after a certain threshold.

![quadtree-subdivision](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-IV/geohashing-and-quadtrees/quadtree-subdivision.png)

[Quadtree](/courses/sytem-design/geohashing-and-quadtrees#quadtrees) seems perfect for our use case, we can update the Quadtree every time we receive a new location update from the driver. To reduce the load on the quadtree servers we can use an in-memory datastore such as [Redis](https://redis.io) to cache the latest updates. And with the application of mapping algorithms such as the [Hilbert curve](https://en.wikipedia.org/wiki/Hilbert_curve), we can perform efficient range queries to find nearby drivers for the customer.

**What about race conditions?**

Race conditions can easily occur when a large number of customers will be requesting rides simultaneously. To avoid this, we can wrap our ride matching logic in a [Mutex](<https://en.wikipedia.org/wiki/Lock_(computer_science)>) to avoid any race conditions. Furthermore, every action should be transactional in nature.

_For more details, refer to [Transactions](https://karanpratapsingh.com/courses/system-design/transactions) and [Distributed Transactions](https://karanpratapsingh.com/courses/system-design/distributed-transactions)._

**How to find the best drivers nearby?**

Once we have a list of nearby drivers from the Quadtree servers, we can perform some sort of ranking based on parameters like average ratings, relevance, past customer feedback, etc. This will allow us to broadcast notifications to the best available drivers first.

**Dealing with high demand**

In cases of high demand, we can use the concept of Surge Pricing. Surge pricing is a dynamic pricing method where prices are temporarily increased as a reaction to increased demand and mostly limited supply. This surge price can be added to the base price of the trip.

_For more details, learn how [surge pricing works](https://www.uber.com/us/en/drive/driver-app/how-surge-works) with Uber._

### Payments

Handling payments at scale is challenging, to simplify our system we can use a third-party payment processor like [Stripe](https://stripe.com) or [PayPal](https://www.paypal.com). Once the payment is complete, the payment processor will redirect the user back to our application and we can set up a [webhook](https://en.wikipedia.org/wiki/Webhook) to capture all the payment-related data.

### Notifications

Push notifications will be an integral part of our platform. We can use a message queue or a message broker such as [Apache Kafka](https://kafka.apache.org) with the notification service to dispatch requests to [Firebase Cloud Messaging (FCM)](https://firebase.google.com/docs/cloud-messaging) or [Apple Push Notification Service (APNS)](https://developer.apple.com/documentation/usernotifications) which will handle the delivery of the push notifications to user devices.

_For more details, refer to the [WhatsApp](https://karanpratapsingh.com/courses/system-design/whatsapp#notifications) system design where we discuss push notifications in detail._

## Detailed design

It's time to discuss our design decisions in detail.

### Data Partitioning

To scale out our databases we will need to partition our data. Horizontal partitioning (aka [Sharding](https://karanpratapsingh.com/courses/system-design/sharding)) can be a good first step. We can shard our database either based on existing [partition schemes](https://karanpratapsingh.com/courses/system-design/sharding#partitioning-criteria) or regions. If we divide the locations into regions using let's say zip codes, we can effectively store all the data in a given region on a fixed node. But this can still cause uneven data and load distribution, we can solve this using [Consistent hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing).

_For more details, refer to [Sharding](https://karanpratapsingh.com/courses/system-design/sharding) and [Consistent Hashing](https://karanpratapsingh.com/courses/system-design/consistent-hashing)._

### Metrics and Analytics

Recording analytics and metrics is one of our extended requirements. We can capture the data from different services and run analytics on the data using [Apache Spark](https://spark.apache.org) which is an open-source unified analytics engine for large-scale data processing. Additionally, we can store critical metadata in the views table to increase data points within our data.

### Caching

In a location services-based platform, caching is important. We have to be able to cache the recent locations of the customers and drivers for fast retrieval. We can use solutions like [Redis](https://redis.io) or [Memcached](https://memcached.org) but what kind of cache eviction policy would best fit our needs?

**Which cache eviction policy to use?**

[Least Recently Used (LRU)](<https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU)>) can be a good policy for our system. In this policy, we discard the least recently used key first.

**How to handle cache miss?**

Whenever there is a cache miss, our servers can hit the database directly and update the cache with the new entries.

_For more details, refer to [Caching](https://karanpratapsingh.com/courses/system-design/caching)._

## Identify and resolve bottlenecks

![uber-advanced-design](https://raw.githubusercontent.com/karanpratapsingh/portfolio/master/public/static/courses/system-design/chapter-V/uber/uber-advanced-design.png)

Let us identify and resolve bottlenecks such as single points of failure in our design:

- "What if one of our services crashes?"
- "How will we distribute our traffic between our components?"
- "How can we reduce the load on our database?"
- "How to improve the availability of our cache?"
- "How can we make our notification system more robust?"

To make our system more resilient we can do the following:

- Running multiple instances of each of our services.
- Introducing [load balancers](https://karanpratapsingh.com/courses/system-design/load-balancing) between clients, servers, databases, and cache servers.
- Using multiple read replicas for our databases.
- Multiple instances and replicas for our distributed cache.
- Exactly once delivery and message ordering is challenging in a distributed system, we can use a dedicated [message broker](https://karanpratapsingh.com/courses/system-design/message-brokers) such as [Apache Kafka](https://kafka.apache.org) or [NATS](https://nats.io) to make our notification system more robust.

# Next Steps

Congratulations, you've finished the course!

Now that you know the fundamentals of System Design, here are some additional resources:

- [Distributed Systems](https://www.youtube.com/watch?v=UEAMfLPZZhE&list=PLeKd45zvjcDFUEv_ohr_HdUFe97RItdiB) (by Dr. Martin Kleppmann)
- [System Design Interview: An Insider's Guide](https://www.amazon.in/System-Design-Interview-insiders-Second/dp/B08CMF2CQF)
- [Microservices](https://microservices.io) (by Chris Richardson)
- [Serverless computing](https://en.wikipedia.org/wiki/Serverless_computing)
- [Kubernetes](https://kubernetes.io)

It is also recommended to actively follow engineering blogs of companies putting what we learned in the course into practice at scale:

- [Microsoft Engineering](https://engineering.microsoft.com)
- [Google Research Blog](http://googleresearch.blogspot.com)
- [Netflix Tech Blog](http://techblog.netflix.com)
- [AWS Blog](https://aws.amazon.com/blogs/aws)
- [Facebook Engineering](https://www.facebook.com/Engineering)
- [Uber Engineering Blog](http://eng.uber.com)
- [Airbnb Engineering](http://nerds.airbnb.com)
- [GitHub Engineering Blog](https://github.blog/category/engineering)
- [Intel Software Blog](https://software.intel.com/en-us/blogs)
- [LinkedIn Engineering](http://engineering.linkedin.com/blog)
- [Paypal Developer Blog](https://medium.com/paypal-engineering)
- [Twitter Engineering](https://blog.twitter.com/engineering)

Last but not least, volunteer for new projects at your company, and learn from senior engineers and architects to further improve your system design skills.

I hope this course was a great learning experience. I would love to hear feedback from you.

Wishing you all the best for further learning!

# References

Here are the resources that were referenced while creating this course.

- [Cloudflare learning center](https://www.cloudflare.com/learning)
- [IBM Blogs](https://www.ibm.com/blogs)
- [Fastly Blogs](https://www.fastly.com/blog)
- [NS1 Blogs](https://ns1.com/blog)
- [Grokking the System Design Interview](https://www.educative.io/courses/grokking-the-system-design-interview)
- [System Design Primer](https://github.com/donnemartin/system-design-primer)
- [AWS Blogs](https://aws.amazon.com/blogs)
- [Martin Fowler](https://martinfowler.com)
- [PagerDuty resources](https://www.pagerduty.com/resources)
- [VMWare Blogs](https://blogs.vmware.com/learning)

_All the diagrams were made using [Excalidraw](https://excalidraw.com) and are available [here](https://github.com/karanpratapsingh/system-design/tree/main/diagrams)._
