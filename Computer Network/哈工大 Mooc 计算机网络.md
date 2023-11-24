---
title: 哈工大 Mooc 计算机网络
category: /小书匠/日记/2023-11
grammar_cjkRuby: true
---
[toc!]

# 第 11 周： 局域网 LAN
## 5.4 ARP 协议（地址解析协议）
### MAC 地址（Media Access Control Address）/ LAN 地址 / 以太网地址 / 物理地址
MAC地址： 32位 IP 地址：
- 接口的网络层地址
- 用于标识网络层分组，支持分组转发。
MAC地址(或称LAN地址，物理地址，以太网地址)：
- 作用：用于局域网内标识一个帧 从 哪个接口 发出，到达哪个物理相连的其他接口
- 48 位 MAC地址（用于大部分 LANs），固化在网卡的ROM(只读存储器，Read Only Memory)中，有时也可以软件设置。
- e.g: 1A-2F-BB-76-09-AD

![唯一的MAC地址](./images/1700817884796.png)

MAC地址由 IEEE（电气与电子工程师协会，Institute of Electrical and Electronics Engineers） 统一管理与分配。
网卡生产商购买MAC地址空间（前24 bit）
类比：
- MAC Address: 身份证号
- IP address：邮政地址

MAC地址是"平面" 地址 -> 可"携带"
- 可以从一个LAN 移动另一个LAN
 
IP地址是层次地址： ->不可"携带"
- IP地址依赖于结点连接到哪个子网

### 地址解析协议(Address Resolution Protocol，ARP)
![问题：](./images/1700818610861.png)
![enter description here](./images/1700818983572.png)
ARP表：LAN中的每个IP结点(主机，路由器)维护一个表。
- 存储某些LAN结点的IP/MAC地址映射关系：
- <IP地址; MAC地址; TTL>
	- 其中TTL是 **存活时间(Time To Live)**。指一个数据包(Packet)在经过一个路由器(Router)时，可传递的最长距离。（跳步数）：每经过一Router，TTL = TTL - 1.
- TTL:经过这个时间以后该映射关系会被遗弃(典型值为20min)

### ARP协议：同一局域网内（一系列过程）
- A想要给同一局域网内的B发送数据报(Datagram)
	- B的MAC地址不在A的 **ARP 表** 中
- A <font color="red">广播</font> ARP 查询分组，其中包含B的IP地址。
	- 目的MAC地址 = FF-FF-FF-FF-FF-FF
	- LAN 中 所有结点都会接收 ARP查询
- B 接收 ARP查询 分组，IP地址匹配成功，向A应答B的MAC 地址。
	- 利用 单播帧 向 A 发送应答
- A 在其 ARP表 中，缓存 B的IP-MAC地址对，直至超时
	- 超时后，再次刷新
- ARP 是"即插即用"(Plug-To-Play) 协议：
	- 结点自主创建 ARP 表，无需干预

### 寻址：从 一个LAN路由 至 另一个LAN
通信过程：A 通过 路由器R 向 B 发送数据报(Datagram)
- 关注寻址：IP地址（数据报中）和MAC地址（帧中）
- 假设A知道B的IP地址(How?)
- 假设A知道第一跳路由器R(左)

## 5.5 以太网
## 5.6 PPP 协议
## 5.7 802.11无线局域网
