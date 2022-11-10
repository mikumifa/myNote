# UDP

 用户数据报协议（User Datagram Protocol）

- 没有建立连接
  - 没有复杂的控制，头部简单
    - UDP发送方，接收方之间没有HandShake，包括进程等信息）
    - 每个UDP段是独立的
- 简单：发送方，接受方无连接状态
- 小段标题
- 没有拥塞控制，UDP可以按照期望的速度传输

应用：

​	RIP:定期发送路由消息(periodially)

​	 DNS避免延迟建立TCP连接（DNS要求快速找到）

​	SNMP:

​	TFTP，DHCP

## 数据帧格式

- 源端口，目的端口，长度，校验data，Data
- 前4个每一个占用2个字节，是端口号（不是ip，ip地址在数据报的部分）

区别

TCP

1. 不是立即交给上层校验，而是需要先和对方沟通
2. 缓存满了才统一交付。

UDP

1. 直接转发报文，保留报文边界
2. IP进行划分
3. 应用程序会发送比较合适的UDP报文大小进行发送

共同点

1. 校验是相同的。

## NAT和PAT

什么是NAT？Network Address Translation

![img](https://spricoder.oss-cn-shanghai.aliyuncs.com/2020-Internet-computing/img/lec05/24.png)

port=socket

### NAT address types

inside Local address

内部本地地址，内网ip地址

inside Global address（内部全局地址）

Outside Global address（外部全局地址），由主机所有者分配IP地址，通常是注册地址

动态的

优点

由于并非每个内部主机都需要同时进行外部访问，因此您可以使用少量的全局唯一地址池来服务相对大量的私有寻址主机。

缺点

一一映射，并没有从根本上解决地址短缺的问题。（同时上网人数有上限）

# 会话层

1. TCP 控制传输，如果用户想要完成一定的数据控制，就会对应在会话层完成。

1. 基于令牌进行交互发言，通过数据同步保证数据完整性(应用逻辑)
2. 进行数据分段、拼接，保证传输的有效。
3. 同步技术，保证故障恢复。

two-way simultaneous communication双工

 two-way alternate control?半双工