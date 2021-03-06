# PPP
通常用在两节点间建立直接的连接，并可以提供连接认证、传输加密（使用ECP，RFC 1968）以及压缩。被用在许多类型的物理网络中，包括串口线、电话线、中继链接、移动电话、特殊无线电链路以及光纤链路。PPP的两个衍生物PPPoE和PPPoA被ISP广泛用来与用户建立数字用户线路（DSL）Internet服务连接

PPP协议包含

1. 一个将IP数据报封装到串行链路的方法。PPP既支持异步也支持同步链路。
2. 一个用来建立、配置和测试数据链路连接的 LCP
3. 一套 NCP ，其中的每一个协议支持不同的网络层协议，如IP、OSI的网络层、DECnet以及AppleTalk等。

## PPP工作流程
1. PPP链路建立
LCP 负责创建链路，对基本的通讯方式进行选择，如最长帧、鉴别协议，不使用ppp帧中地址和控制字段
链路一端设备通过 LCP 向对方发送配置请求帧，另一端可发送配置确认帧、配置否认帧（理解但不接受）和配置拒绝帧（无法理解或不能接受）
2. 用户鉴别
客户端将自己的身份发送给远端的接入服务器。在这一阶段，只允许传送 LCP、鉴别协议和链路质量监测协议的分组。如果认证失败，转入链路终止阶段
3. 调用网络层协议
NCP根据网络层的不同协议互相交换网络层特定的网络控制分组。网络配置完成后，进入可进行数据通信的“链路打开”状态。在该阶段IP控制协议（IPCP）可以向拨入用户分配动态地址