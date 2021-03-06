# IP协议
为计算机网络相互连接进行通信而设计的协议，能使连接到网上的所有计算机网络实现相互通信的一套规则，规定了计算机在因特网上进行通信时应当遵守的规则

IP协议最大的作用是构建了一个虚拟的互联网络
**虚拟互连网络：互联网通常是由 异构网络系统 组成的，拥有不同的寻址方案、最大分组长度、网络接入机制、媒体访问控制机制、服务、路由选择、差错恢复方法等等，所以需要一个虚拟的互连网络，通过标准化协议来连接异构的网络，使得用户看起来网络是一个使用简单协议来统一控制的网络**

![](/.src/pic/异构网络.png)

与 IP 协议配套使用的还有四个协议：
  - 地址解析协议 ARP：向下连接链路层，由IP到MAC地址的映射
  - 逆地址解析协议 RARP：向下连接链路层，由MAC到IP地址的映射（DHCP协议已经包含了RARP协议的功能，现在已经没人再单独使用RARP协议）
  - 网际控制报文协议 ICMP：向上连接运输层
  - 网际组管理协议 IGMP：向上连接运输层

## ARP
ARP标准定义了两类基本的报文,都封装在帧中传送
- 请求报文：包含一个IP地址和对相应硬件地址的请求
- 响应报文：包含发来的IP地址和相应的硬件地址

ARP 是解决同一个局域网上的主机或路由器的 IP 地址和硬件地址的映射问题。如果所要找的主机和源主机不在同一个局域网上，要通过 ARP 找到一个位于本局域网上的某个路由器的硬件地址，然后把分组发送给这个路由器，让这个路由器把分组转发给下一个网络









## IP数据报格式
![](/.src/pic/ip数据报.png)


## IP地址与MAC地址

IP地址与MAC地址的区别

|区别|IP|MAC|
|-|-|-|
|位置|IP数据报的首部|MAC帧首部|
|体系|网络层以上使用IP地址|链路层以下使用硬件地址|
|实体|IP数据报，路由器根据目的站的IP地址进行选路|MAC帧，IP数据报被封装在MAC帧里面|
|可见性|IP层看不到的MAC地址的变换|MAC帧在不同的网络上传送，首部不同|
联系：每个路由器都有IP地址和硬件地址。IP层抽象的互连网却屏蔽了下层这些很复杂的细节，并使我们能够使用统一的、抽象的IP地址进行通信。

## 子网和超网
> IP地址设计不合理：IP地址空间的利用率有时很低、给每一个物理网络分配一个网络号会使路由表变得太大因而使网络性能变坏
在IP地址中增加“子网号字段”,使两级IP地址变成为三级的IP地址,称为“划分子网”

基本思路：一个拥有许多物理网络的单位，可将所属的物理网络划分为若干个子网（subnet)，对外仍表现为一个没有划分子网的网络

![](/.src/pic/子网.png)

## 子网掩码
> 从IP数据报首部无法判断源主机或目的主机所连接的网络是否进行了子网划分，使用子网掩码(subnet mask)可以找出 IP 地址中的子网部分

划分子网后采用 **子网掩码** 标识 **网络位** 和 **主机位**
![](/.src/pic/子网1.png)

> 141.14.72.24，子网掩码 255.255.192.0 的网络地址是141.14.64.0
141.14.72.24，子网掩码 255.255.224.0 的网络地址也是141.14.64.0
但两者代表了不同的网络


## IP地址分类
- 全0地址：0.0.0.0为本机位置，保留位
- 全1地址：广播地址


### A类地址
0开头，可填充位7位，主机为24位<exampointbig>（1.0.0.0~126.255.255.255）</exampointbig>
- 10.0.0.0~10.255.255.255通常作为局域网地址。
- 127网段位本地地址，从127.0.0.0\~127.255.255.255为环回地址，通常有172.16.0.0\~172.31.0.0作为局域网地址
- A类网络地址数量较少，可以用于主机数达1600多万台的大型网络。
- 补充：A类的126个网段地址，除了40多个分配给普通组织，大部分依然在IP管理组织。

### B类地址
10开头，可填充位14位，主机位为16位<exampointbig>（128.0.0.0~191.255.255.255）</exampointbig>
  - 适用于中等规模规模的网络，每个网络所能容纳的计算机数为6万多台。
  
### C类地址
110开头，可填充位21位，主机位为8位<exampointbig>（192.0.0.0~223.255.255.255,默认子网掩码/24,即255.255.255.0）</exampointbig>
  - 通常为内网分配地址
![](/.src/pic/子网3.png)

### D类地址
1110开头，后面为多播地址

### E类地址
1111开头，后面为保留使用


![](/.src/pic/ip.png)

IP地址与网络地址：由子网掩码计算出来的，用于识别网段的部分，为网络地址。
![](/.src/pic/ip1.png)

# IPv4与IPv6
## 双栈协议
- 双协议栈技术就是指在一台设备上同时启用IPv4协议栈和IPv6协议栈。可以是路由器或计算设备（双地址网卡、软路由等）

<exampointbig>4.5.5 路由器的构成 第四章231页 考试完补充</exampointbig>
<exampointbig>4.6  因特网组中的多播 第四章241页 考试完补充</exampointbig>
<exampointbig>4.7  VPN与NAT 第四章264页 考试完补充</exampointbig>