# 数据链路层

第二层是node到node之间，只是一段介质

![image-20221006102446706](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006102446706.png)

- LLC子层获取网络协议数据（通常是IPV4数据包）并加入控制信息，帮助数据包传送到目的节点。第二层通过LLC和上层通信

  ？？？？？parket的包装属于LLC

  LLC在软件中实现，可以把LLC视为NICs的驱动程序软件。网卡趋同程序是直接和网卡中的硬件交互，以在介质与介质访问控制子层之间传送数据的程序

- 主要任务
  
  - 错误检测
  - 网络拓扑
  - 流控制
  
- 第二层和第一层的不同
  - 第一次不能和上层交流
  - 第二层可以逻辑链路控制（LLC）
  - 第二层有介质访问控制（MAC）
  - 第二层使用帧，第一次使用比特流（framing）
  - 第二层寻址和命名方式。
  
- ![image-20221006103341544](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006103341544.png)

逻辑链路控制提供了三种服务

无线连接服务，不需要确认接收

- 使用于，可靠的链路，实时的任务，大多数的局域网

无线的链接服务，需要确认接收

- 使用于，不可靠的链路,例如无线网

有限连接，需要确认接收

![image-20221006102957478](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006102957478.png)

![image-20221006103055924](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006103055924.png)

上面的是确定的MAC protocals，Token Ring和FDDI

![image-20221006104031454](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006104031454.png)

下面是不确定的MAC Protocols

Carrier Sense Multiple Acess with Collision Detection(CSMA/CD)

![image-20221006104348810](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006104348810.png)

局域网信号传输的3种分类

unicast单路传播，multicast多路传播，broadcast广播

## 局域网的标准

![image-20221006105308486](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006105308486.png)

IEEE是吧data link分2层MAC，LLC。TCP/IP把2个合成一层

![image-20221006110719033](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006110719033.png)

![image-20221006110806081](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006110806081.png)

物理层和数据链路层合在一起

![image-20221006110934327](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006110934327.png)

## 帧

不同的802.3的标准不同，

![image-20221006105551334](C:\Users\10550\AppData\Roaming\Typora\typora-user-images\image-20221006105551334.png)Socket用c类型写的大作业

- preamble，前脚码
- 目的地址
- 源地址
- length长度，length指定长度

> Data的长度不能太大，长度太大的话，会影响传输。
>
> Data的46-1500

Ethernet II 没有使用length使用了type，（发现length没什么用）。

- FCS使用的是循环取余校验，cyclic redundancy check.44444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444444