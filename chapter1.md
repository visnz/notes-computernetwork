# 互联网简介
![](/.src/pic/网络.png)

网络：由若干 结点 和连接这些结点的 链路 组成

互联网：是網路與網路之間所串連成的龐大網路，這些網路以一組標準的網路TCP/IP協議族相連，連接全世界幾十億個設備，形成邏輯上的單一巨大國際網絡。即互联网是 网络的网络。连接在因特网上的计算机都称为主机

## 网络划分
1. 作用范围
    - WAN ：国家、洲际网络
    - MAN ：城市网
    - LAN ：校园、企业网络、个人家庭 ->[WLAN](#无线局域网wlan)
    - PAN ：同一系统的计算网络
2. 网络的使用者
    - 公用网(public network)
    - 专用网(private network) -> VPN
3. 接入方式
    - AN：本地接入网或居民接入网，ISP提供一个接入网供用户能够进入英特网
    ![](/.src/pic/接入网.png)

## ISP
互联网服务提供商，指提供互聯網存取服務的公司。通常大型的電訊公司都會兼任互联网服务供应商

![](/.src/pic/ISP结构.png)
从上图来看因特网的工作方式，有 边缘部分 和 核心部分 两大块，基于此衍生出C/S模型（即主从式架构）

### 边缘部分
由所有连接在因特网上的主机组成。这部分是用户直接使用的，用来进行通信（传送数据、音频或视频）和资源共享。

### 核心部分
由大量网络和连接这些网络的路由器组成。这部分是为边缘部分提供服务的（提供连通性和交换）。

### [主从式架构](https://www.wikiwand.com/zh-hant/%E4%B8%BB%E5%BE%9E%E5%BC%8F%E6%9E%B6%E6%A7%8B)
把客戶端 (Client)（通常是一個採用圖形用戶界面的程序）與服務器 (Server) 區分開來。每一個客戶端軟件的實例都可以向一個服務器或應用程序服務器發出請求。

## 常见的计算机网路连接方式

1. 点对点连接（最简单）
2. 总线网（最常见）
3. 星形/树形网络
4. 环形网

## <exampoint>互联网的基石</exampoint>
- ARPANET 其研究奠定了ARPA设计 **分组交换** 网络的基础，**分组交换是网络核心部分最重要的功能**
- [TCPIP协议](#tcpip协议栈)
- [HTTP](#http)与浏览器、WWW服务器、HTML四者组成万维网的基础
- 因特网的核心部分是由 **路由器** 连接的网络



















