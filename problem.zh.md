
# {{ 页面标题 }}

> 胜利是美丽,鲜艳的花朵. 运输是干,没有它,它永远不会开花. *-温斯顿·丘吉尔*

## 问题: 获取流程进行沟通

前三章描述了各种可用于连接计算机集合的技术,从简单的以太网和无线网络到全球规模的互联网络. 下一个问题是将此主机到主机数据包传送服务转变为进程间通信通道. 这是由...发挥的作用*运输*网络体系结构的级别,因为它支持在端节点中运行的应用程序之间的通信,有时称为*端至端*协议. 

两种力量塑造了端到端协议. 从上面看,使用其服务的应用程序级进程具有某些要求. 以下列表列出了传输协议可以提供的一些常见属性: 

-   保证邮件传递

-   按照发送的顺序发送消息

-   每条消息最多提供一份副本

-   支持任意大的消息

-   支持发送方和接收方之间的同步

-   允许接收方将流量控制应用于发送方

-   支持每个主机上的多个应用程序进程

请注意,此列表不包括应用程序进程可能希望从网络获得的所有功能. 例如,它不包括身份验证或加密等安全功能,这些功能通常由位于传输级别之上的协议提供. 

从下面看,传输协议运行的底层网络在其可以提供的服务级别上具有某些限制. 网络的一些更典型的限制是它可能

-   删除邮件

-   重新排序邮件

-   提供给定邮件的重复副本

-   将消息限制为某种有限大小

-   在任意长时间延迟后发送消息

据说这样的网络提供了一个*最大努力*服务水平,例如互联网. 

因此,挑战在于开发算法,将底层网络的不太理想的属性转换为应用程序所需的高级服务. 不同的传输协议采用这些算法的不同组合. 本章在四个代表性服务的背景下研究这些算法 - 一个简单的异步解复用服务,一个可靠的字节流服务,一个请求/回复服务,以及一个用于实时应用的服务. 

在解复用和字节流服务的情况下,我们分别使用因特网的用户数据报协议 (UDP) 和传输控制协议 (TCP) 来说明在实践中如何提供这些服务. 在请求/回复服务的情况下,我们将讨论它在远程过程调用 (RPC) 服务中扮演的角色以及所需的功能. 本讨论的主题是对两种广泛使用的RPC协议的描述: SunRPC和DCE-RPC. 

最后,实时应用程序对传输协议提出了特殊要求,例如需要携带允许在适当的时间点播放音频或视频样本的定时信息. 我们看一下应用程序对这种协议的要求以及最广泛使用的实例,即实时传输协议 (RTP) . 