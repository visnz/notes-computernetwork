# 网络安全
## 常见网络安全问题
### 被动式攻击
窃听
### 主动式攻击

中间人信息截获

恶意程序的攻击
  - 病毒：广义上的计算机恶意程序总称
  - 蠕虫：通过网络通信实现传播
  - 木马：隐藏攻击
  - 逻辑炸弹：由计算机逻辑漏洞或循环等手段，耗尽计算机资源或阻碍计算机工作的手段
  - 漏洞与后门：被动和主动的软件入口
  - 流氓软件：不言自明

拒绝服务的泛洪攻击

## 密码体制
对称秘钥密码体制DES：加密解密使用相同的密码体制。后升级为AES算法

公钥密码体制（非对称加密体制）
  - 拥有一个公钥和一个秘钥，公钥、加密解密算法全部公开。
  - 发送者A用公钥加密明文成密文。公钥可以用来加密，但不能用来解密。
  - 服务器B收到密文，用自己的秘钥做解密恢复明文。
  - 通常来说，公钥在计算上推理不出秘钥，但一个公钥可以匹配多个秘钥，构建一对多的连接。
  - 详见ssh的加密技术

## 安全通信思路
###  密码散列函数
- 算法：SHA-1、MD5
- 将密码计算成不可逆的散列值用于验证，但缺点依然是有可能使用不同的信息生成一样的散列值。
- 在散列值的基础上，双方用约定好的秘钥对散列值进行加密和解密。接收端收到散列值后，用秘钥解密，并计算一遍报文，进行验证。
  
###  IPsec协议族
一种开放标准的框架结构，确保IP在网络上的安全通讯

###  防火墙
访问控制策略

- 对单个服务系统或链路进行分组过滤，作为应用网关
- 大规模集群的防火墙：安全策略组
- 重点防护：阻止所有可以的通信。

### 入侵检测系统
对进入网络的分组进行检查，通常能检测多种网络攻击如端口映射、端口扫描、DOS攻击、系统攻击等。（只是检测）


接下去的加密发展方向：椭圆加密（QQ）、移动物联网安全、量子加密通信等
