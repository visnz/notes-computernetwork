# 交换机
交换机最基本的功能：[分组交换](#https://www.wikiwand.com/zh-hant/%E5%88%86%E7%BB%84%E4%BA%A4%E6%8D%A2)

交换机特征：
- 交换式集线器
- 多端口网桥
- 第二层交换机

![](/.src/pic/交换机.png)

交换表的自学习功能：每当有一个新设备加入，设备将自动完善MAC地址到接口号的映射情况

由分组交换机构成一个去中心化网络，对网络中的数据进行转发。好处是当部分结点或链路被摧毁时，分组交换仍可保持网络畅通。

## 虚拟局域网
当网络中广播域内节点数量增多时，网络中广播包将严重影响网络通信的效率，循环广播引起广播风暴，使网络性能下降。此时使用虚拟局域网Vlan对lan进行划分，同一个vlan中属于一个广播域，不同vlan不能直接通信，划分子域，使得广播不至于影响到多有的交换对象。

![](/.src/pic/vlan.png)

虚拟局域网的作用
- 广播控制：限制了接收广播信息的工作站数，使得网络不会因广播风暴而引起性能恶化
- 增加了网络的安全性
- 提高网络性能
- 易于网络管理