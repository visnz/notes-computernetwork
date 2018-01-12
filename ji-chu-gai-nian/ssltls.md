# SSL/TLS
前任者SSL(Secure Sockets Layer 安全套接层),及其继任者TLS（Transport Layer Security，传输层安全）是为网络通信提供安全及数据完整性的一种安全协议。SSL在传输层对网络连接进行加密。

- 地位：从一个应用层到传输层的中间件，变成与应用层融合升级的一部分
- SSL协议包括：
  - SSL记录协议：建立在可靠TCP上，提供数据封装、压缩、加密等方法
  - SSL握手协议：非对称加密的秘钥交换、加密算法、身份认证的工作
- 常用的支持SSL/TLS的服务器：Tomcat/Nginx/IIS/Apache2等
- 基于SSL/TLS的新传输协议https：基于该系列建立TCP后建立的HTTP连接。
