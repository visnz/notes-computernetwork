# DNS
DNS是计算机域名系统 (Domain Name System) 的缩写，功能是将域名转换为计算机可识别的IP地址。
DNS报文使用UDP，分为**询问报文**和**答应报文**

DNS报文（UDP报文）中13个跟服务器信息，原因是DNS报文最大限制为512byte，跟最低MTU有关（X.25协议（Dial Up/Modem）：576字节，DNS报文 + UDP+ IP= 512+8+20=540Byte），即DNS报文查询无需IP分片

## DNS服务器
DNS服务器：域名服务器(Domain Name Server)。在Internet上域名与IP地址之间是一一对应的，域名和ip的转换工作即域名解析，域名解析需要由专门的域名解析服务器来完成，DNS就是进行域名解析的服务器。

![](/.src/pic/DNS.png)

### 记录分类
#### A记录
A (Address) 记录是用来指定主机名（或域名）对应的IP地址记录，即服务器的IP。域名绑定A记录在人们输入一个网址（域名）的时候，负责解析的DNS,会把你引导向设置在DNS的A记录所对应的服务器。
#### CNAME记录
CNAME ( Canonical Name )别名记录。当 DNS 系统在查询 CNAME 左面的名称的时候，都会转向 CNAME 右面的名称再进行查询，一直追踪到最后的 PTR 或 A 名称，成功查询后才会做出回应，否则失败。例如,一个 IP 通常(当然也有例外)只会对应一个 A 记录，但我们可以使用CNAME在A名称之上赋予该 IP 更多的名称。

Cname记录允许将多个名字映射到同一台计算机。通常用于同时提供WWW和MAIL服务的计算机。例如，有一台计算机名为 ``host.mydomain.com``（A记录）。 它同时提供WWW和MAIL服务，为了便于用户访问服务。可以为该计算机设置两个别名（CNAME）：WWW和MAIL。 这两个别名的全称就``http://www.mydomain.com``和``mail.mydomain.com``。实际上他们都指向 ``host.mydomain.com``。

### NS记录
NS（Name Server）记录是域名服务器记录，用来指定该域名由哪个DNS服务器来进行解析。您注册域名时，会有默认的DNS服务器，每个注册的域名都是由一个 DNS域名服务器来进行解析的，DNS服务器NS记录地址一般以以下的形式出现：``ns1.domain.com``,``ns2.domain.com``等。比如云盾``dns:ns1.seccdn.com``,``ns2.seccdn.com``。

## 域名服务器分类

1. 根域名服务器(root name server) 	
2. 顶级域名服务器（TLD 服务器）
3. 权限域名服务器(authoritative name server)
4. 本地域名服务器(local name server)（默认域名服务器）

## 根域名服务器
- 世界上一共提供十三个根域名服务器（13个域名地址），共同指向“根域名解析服务”。并不是真的只有13台机器。而是由接近几百台服务器构成的一个“根域名解析服务提供商”，每台机器都有若干根服务器镜像组成，用于就近解决根域名解析服务。

## DNS报文查询
查询的方法在DNS报文中进行指定
- 递归查询：向上一级提出查询申请，由上一级代理查询，再依次返回。这种方法经过根域名服务器，交通计算量较大。
![](/assets/sp180113_013107.png)

- 迭代查询：向上一级提出查询申请，请求上一级告知应该去哪里查询。这种方法由本地域名服务器承载计算。
![](/assets/sp180113_013114.png)



## DNS高速缓存
![](/.src/pic/DNS2.png)

