## 第二层设备

### 网卡

### 网桥

基于mac地址制作mac table，mac表，分割冲突域

透明网桥：局域网的站点并不知道所发送的帧将经过几个网桥。网桥对其他各站是不知道的，

通过学习：根据MAC地址的source地址建立一个

![image-20221017103252123](weak_7.assets/image-20221017103252123.png)

该表会刷新，记录没有使用会被删掉。

不可以隔离广播域（目的地址111111111），网桥和switch还是会广播。

## 交换机

和网桥功能几乎一致，

降低交通量，真假带宽

隔离冲突域，。

网桥是基于软件的，性能比较差，交换机是基于硬件的，速度好

路由器的隔离冲突域![image-20221017104614803](weak_7.assets/image-20221017104614803.png)

每个网段，host全0，表示本网段，host全1表示广播地址、![image-20221020103830724](weak_7.assets/image-20221020103830724.png)

![image-20221020102609317](weak_7.assets/image-20221020102609317.png)

![image-20221020102623238](weak_7.assets/image-20221020102623238.png)

![image-20221020103147803](weak_7.assets/image-20221020103147803.png)

私有网段。这些网段属于局域网。

相同network ID才可以直接交流

ip地址耗尽的方法

NAT

CIDR

IPV6

## Subnet

![image-20221020103658240](weak_7.assets/image-20221020103658240.png)

从Host为里面借若干位上面组成子网。

广播域的范围变小，广播域的数量增加。

最小也要借2位，

如果借1位的话，0表示网络地址，1broadcast 地址

最大也要留2位，给host留2位

![image-20221020105127515](weak_7.assets/image-20221020105127515.png)

确定子网掩码

确定是那种类型的网，然后得到子网掩码

要13个subnets，所有要记得去掉2个

借4位

![image-20221020105428177](weak_7.assets/image-20221020105428177.png)

![image-20221020105446580](weak_7.assets/image-20221020105446580.png)计算新的子网掩码

有16个可能的subnets，去掉2个不可以使用的有14个可以使用的subnet

子网掩码和ip做 AND操作。

路由器基于Ip的network ID转发，不是同一个网段的不转发。

## Router function,路由功能

把报文放到帧里面

网关很重要：如果网络A中的主机发现数据包的目的主机不在本地网络中，就把数据包转发给它自己的网关，再由网关转发给网络B的网关，网络B的网关再转发给网络B的某个主机(如附图所示)。网络B向网络A转发数据包的过程。

![image-20221020113112122](weak_7.assets/image-20221020113112122.png)

![image-20221020113422382](weak_7.assets/image-20221020113422382-1666236863500-1.png)

每个S口的IP地址不一样，要有不同的网段。

路由器如何配置地址

![image-20221020113627984](weak_7.assets/image-20221020113627984.png)

静态：
给每一个主机一个IP地址，不能使用重复的IP地址

配置pc的ip地址，配置路由器的ip地址，保证ip地址不会冲突

## ARP，根据主机来获得ip地址

RAM，Randrom access  Memory断电之久借没有数据了

![image-20221020115220339](weak_7.assets/image-20221020115220339.png)

放送一个广播地址（包含自己的ip和接收端的ip）

![image-20221020115331685](weak_7.assets/image-20221020115331685.png)

接收端的ip进行 ARP reply，有自己的mac

![image-20221020115417021](weak_7.assets/image-20221020115417021.png)

ARP返回地址

## Connection oriented network services,

面向连接的网络服务

在数据传输直接，连接是必须的

## Circuit switched

所有的的parket通过相同的信道，通过相同的虚拟电路。

## Connectionless network services

分别对待包

IP是一个无线的系统

## Packet switched

选择不同的路径，

没有顺序的到达，

设备为每一个packet做路径选择，每个packet的标准不同

（虚电路和数据报服务的区别，看书上）

## Routed protocol



![image-20221024104417604](weak_7.assets/image-20221024104417604.png)

Routing路由表

![image-20221024104619731](weak_7.assets/image-20221024104619731.png)

（（地址解析协议）ARP是ip得到mac地址的方法）

![image-20221024105308890](weak_7.assets/image-20221024105308890.png)

![image-20221024105340750](weak_7.assets/image-20221024105340750.png)

## IGP，EGP

EGP不学（EGP不同的自治系统之间 交流）

IGP是内部网关协议

![image-20221024105752635](weak_7.assets/image-20221024105752635.png)

IGP的2个分类：![image-20221024105844373](weak_7.assets/image-20221024105844373.png)

![image-20221024111631972](weak_7.assets/image-20221024111631972.png)

一开始A只可以看到w和x。

RIP，和相邻的路由器交换信息

（目的网段，距离，下一条的路由器，）



会定期更新

Link state routing

交换Topological Datebase

SFP,最短路径算法，

每个网络获得网络的视野，

生成一个树，根据树生成一个路由表，

value是带款

![image-20221024113441872](weak_7.assets/image-20221024113441872.png)

![image-20221024113544509](weak_7.assets/image-20221024113544509.png)

![image-20221024113632180](weak_7.assets/image-20221024113632180.png)

![image-20221024113703497](weak_7.assets/image-20221024113703497.png)
