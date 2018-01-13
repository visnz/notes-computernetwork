# 三层基础服务

![](http://www.ruanyifeng.com/blogimg/asset/2017/bg2017072301.jpg)
![](http://www.ruanyifeng.com/blogimg/asset/2017/bg2017072307.jpg)

## IaaS
[基础设施服务](https://www.wikiwand.com/zh-hans/%E5%9F%BA%E7%A4%8E%E8%A8%AD%E6%96%BD%E5%8D%B3%E6%9C%8D%E5%8B%99)，Infrastructure-as-a-service

> 是消费者使用处理、储存、网路以及各种基础运算资源，部署与执行作业系统或应用程式等各种软体。客户端无须购买伺服器、软体等网路设备，即可任意部署和运行处理、存储、网络和其它基本的计算资源，不能控管或控制底层的基础设施，但是可以控制作业系统、储存装置、已部署的应用程式，有时也可以有限度地控制特定的网路元件，像是主机端防火墙

IaaS 是云服务的最底层，主要提供一些基础资源。它与 PaaS 的区别是，用户需要自己控制底层，实现基础设施的使用逻辑。如Amazon EC2、Digital Ocean、阿里云等，通常为云服务基础设施提供商

## PaaS
[平台服务](https://www.wikiwand.com/zh-hans/%E5%B9%B3%E5%8F%B0%E5%8D%B3%E6%9C%8D%E5%8A%A1)，Platform-as-a-service

> 提供使用者将云端基础设施部署与建立至用户端，或者借此获得使用程式语言、程式库与服务。使用者不需要管理与控制云端基础设施（包含网络、伺服器、作业系统或储存），但需要控制上层的应用程式部署与应用代管的环境

PaaS 提供软件部署平台（runtime），抽象掉了硬件和操作系统细节，可以无缝地扩展（scaling）。开发者只需要关注自己的业务逻辑，不需要关注底层。即**应用快速生成、测试和部署的工具**，如Heroku、Google App Engine、OpenShift（红帽）、Docker（应用场景）

## SaaS
[软件服务](https://www.wikiwand.com/zh-hans/%E8%BD%AF%E4%BB%B6%E5%8D%B3%E6%9C%8D%E5%8A%A1)，Software-as-a-service

> 一种软件交付模式。在这种交付模式中云端集中式托管软件及其相关的数据，软件仅需透过网际网路，而不须透过安装即可使用。用户通常使用精简客户端经由一个网页浏览器来访问软件即服务

SaaS 是软件的开发、管理、部署都交给第三方，不需要关心技术问题，可以拿来即用。普通用户接触到的互联网服务，几乎都是 SaaS

- 储存服务 Dropbox / BaiduDisk
- 社交服务 Facebook / Twitter / Instagram
- 团队协同服务 Teambition
- 游戏服务 Steam / Uplay

---
部分内容引用自：[阮一峰的网络日志 IaaS，PaaS，SaaS 的区别](http://www.ruanyifeng.com/blog/2017/07/iaas-paas-saas.html)