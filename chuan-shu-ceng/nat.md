# 网络地址转换技术
又称 网络掩蔽、IP掩蔽

是一种在IP封包通过路由器或防火墙时重写来源IP地址或目的IP地址的技术。这种技术普遍使用在有多台主机但只通过一个公有IP地址访问因特网的私有网络中。NAT也让主机之间的通信变得复杂，导致降低了通信效率。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b2/Nat1.svg/600px-Nat1.svg.png)

## 使用情况
1990年代中期，NAT是作为一种解决IPv4地址短缺以避免保留IP地址困难的方案而流行起来的。NAT成了家庭和小型办公室网络连接上的路由器的一个标准特征，因为对他们来说，申请独立的IP地址的代价要高于所带来的效益。

目前大多数家庭和小型办公室使用ISP动态（或静态）分配的公网IP进行出口分配实现NAT。可以帮助访问者在网络上隐藏真实主机的IP只暴露访问代理主机的IP，较好保护真实主机不受攻击以阻止外网的而已活动，比如靠拦截分析流量来识别病毒~~这也使窥探隐私成为可能~~。没有真正的公网IP地址，不能参与一些TCP等连接。（NAT中由代理主机完成TCP代理）

## 地址转换的改变
由于改变了IP源地址，在重新封装数据包时候必须重新计算校验和，网络层以上的只要涉及到IP地址的头部校验和都要重新计算。

## 基本网络地址转换（Basic NAT）

“静态NAT”，只支持从地址到地址的映射。即要求每个内网都要有一个对应的公网地址，因此得维护一个公网地址池。通常，接入路由器会允许一台主机来接管所有的外部连接，或本身就由这台路由（或软路由）完成管理工作，被称为**DMZ主机**。

|内网IP|	外网IP|
|-|-|
|192.168.1.55|219.152.168.222|
|192.168.1.59|219.152.168.223|
|192.168.1.155|219.152.168.224|

## 网络地址端口转换（NAPT）
端口映射，即允许多台主机以一台边界主机的身份访问互联网。当内部主机访问某一地址的端口时候，边界主机动态或静态提供一个端口作为映射，由主机代理进行TCP连接、端口访问。

通常会包含源地址转换和目的地址转换两种技术

|内网IP|	外网IP|
|-|-|
|192.168.1.55:41152|219.152.168.222:9200|
|192.168.1.59:80|219.152.168.222:9201|
|192.168.1.155:8080|219.152.168.222:9202|

## 不同类型的NAT

![](https://upload.wikimedia.org/wikipedia/commons/thumb/4/44/Full_Cone_NAT.svg/800px-Full_Cone_NAT.svg.png)
完全圆锥型NAT（Full cone NAT），即一对一（one-to-one）NAT
- 一旦一个内部地址（iAddr:port）映射到外部地址（eAddr:port），所有发自iAddr:port的包都经由eAddr:port向外发送。任意外部主机都能通过给eAddr:port发包到达iAddr:port（注：port不需要一样）

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3c/Restricted_Cone_NAT.svg/800px-Restricted_Cone_NAT.svg.png)
受限圆锥型NAT（Address-Restricted cone NAT）
- 内部客户端必须首先发送数据包到对方（IP=X.X.X.X），然后才能接收来自X.X.X.X的数据包。在限制方面，唯一的要求是数据包是来自X.X.X.X。
- 内部地址（iAddr:port1）映射到外部地址（eAddr:port2），所有发自iAddr:port1的包都经由eAddr:port2向外发送。外部主机（hostAddr:any）能通过给eAddr:port2发包到达iAddr:port1。（注：any指外部主机源端口不受限制，但是目的端口必须是port2。只有外部主机数据包的目的IP 为 内部客户端的ip，且目的端口为port2时数据包才被放行。）

![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/c2/Port_Restricted_Cone_NAT.svg/800px-Port_Restricted_Cone_NAT.svg.png)
端口受限圆锥型NAT（Port-Restricted cone NAT）
类似受限制锥形NAT（Restricted cone NAT），但是还有端口限制。
- 一旦一个内部地址（iAddr:port1）映射到外部地址（eAddr:port2），所有发自iAddr:port1的包都经由eAddr:port2向外发送。
- 在受限圆锥型NAT基础上增加了外部主机源端口必须是固定的。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/7/73/Symmetric_NAT.svg/800px-Symmetric_NAT.svg.png)
对称NAT（Symmetric NAT）
- 每一个来自相同内部IP与端口，到一个特定目的地地址和端口的请求，都映射到一个独特的外部IP地址和端口。
同一内部IP与端口发到不同的目的地和端口的信息包，都使用不同的映射
- 只有曾经收到过内部主机数据的外部主机，才能够把封包发回



## NAT用途实例
- 负载均衡：目的地址转换NAT可以重定向一些服务器的连接到其他随机选定的服务器。
- 失效终结：目的地址转换NAT可以用来提供高可靠性的服务。如果一个系统有一台通过路由器访问的关键服务器，一旦路由器检测到该服务器宕机，它可以使用目的地址转换NAT透明的把连接转移到一个备份服务器上。
- 透明代理：NAT可以把连接到因特网的HTTP连接重定向到一个指定的HTTP代理服务器以缓存数据和过滤请求。一些因特网服务提供商就使用这种技术来减少带宽的使用而不用让他们的客户配置他们的浏览器支持代理连接。

## 内网穿透（NAT穿透）
计算机是局域网内时，外网与内网的计算机节点需要连接通信，有时就会出现不支持内网穿透。会遇到这个问题的通常是那些客户端网络交互应用程序的开发人员，尤其是在对等网络和VoIP领域中。比如如何让外网的电脑能顺利访问到内网的电脑等。

技术人员提出了许多许解决方案，比较常用的是**UDP路由验证**和**STUN**

### UDP路由验证
让位于NAT后的两台主机都与处于公共地址空间的、众所周知的第三台服务器相连，然后，一旦NAT设备建立好UDP状态信息就转为直接通信，并寄希望于NAT设备会在分组其实是从另外一个主机传送过来的情况下仍然保持当前状态。

### IGD
基于UPnP的**互联网网关设备**标准设备控制协议，一种在网络地址转换（NAT）环境中映射端口的协议，受部分支持NAT的路由器支持。
![](https://upload.wikimedia.org/wikipedia/commons/3/36/UPnP_discovery_phase.jpg)

### [STUN](https://www.wikiwand.com/zh-hans/STUN)
NAT会话穿越应用程序，它允许位于NAT（或多重NAT）后的客户端找出自己的公网地址，查出自己位于哪种类型的NAT之后以及NAT为某一个本地端口所绑定的Internet端端口。这些信息被用来在两个同时处于NAT路由器之后的主机之间建立UDP通信

---
参考资料: [NAT维基百科](https://www.wikiwand.com/zh-hans/%E7%BD%91%E7%BB%9C%E5%9C%B0%E5%9D%80%E8%BD%AC%E6%8D%A2)