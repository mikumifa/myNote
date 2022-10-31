## 内部储存器

由单元组成，

地址：单元的唯一标识符号

地址空间：可唯一识别的单元的总数

寻址能力：储存在每个单位中信息的位数。（**cpu最多可以在内存中寻找到的地址数量**）

层次化结构：CPU和存储器的速度可以匹配，能够兼容速度和成本



## 位元：memory cell

![image-20221020162540811](Memory.assets/image-20221020162540811.png)

半导体存储器的类型

![image-20221020162650578](Memory.assets/image-20221020162650578.png)

EPROM是一个芯片的全部删除，EEPROM是字节删除，Flash是块级别的。

## RAM

随机访问：Random Access Memory，对存储器的任意数据的访问所花费的时间与数据所在的位置无关

## SRAM

![image-20221020163958248](Memory.assets/image-20221020163958248.png)

先Q和Q‘给一个信号，撤销后，然后信号就锁住了。

## DRAM

不是双稳态的，不冲电的话电容会流逝。

![image-20221020165446978](Memory.assets/image-20221020165446978.png)

SRAM，快，贵，低集成，不需要刷新

DRAM，慢，便宜，高集成，要刷新（内存条）

## ROM

![image-20221020171518560](Memory.assets/image-20221020171518560.png)

![image-20221020171540951](Memory.assets/image-20221020171540951.png)

可编程的ROM

![image-20221020171813893](Memory.assets/image-20221020171813893.png)

![image-20221020171821383](Memory.assets/image-20221020171821383.png)![image-20221020171831700](Memory.assets/image-20221020171831700.png)

内存会使用EEPROM来存储内存的开发者信息，生产时间，内存信息，通信信息

![image-20221020173028545](Memory.assets/image-20221020173028545.png)

固态硬盘使用NAND Flash

> JavaScript 语言使用构造函数（constructor）作为对象的模板。

![image-20221020173609363](Memory.assets/image-20221020173609363.png)

位元到主存

![image-20221020174042377](Memory.assets/image-20221020174042377.png)

上面是DRAM，11条地址线。。

CPU获得总线的控制权，发送地址，然后控制器把地址分解为行地址和列地址，然后放送行地址，选择行，把行信号放大，选择行

![image-20221020174834968](Memory.assets/image-20221020174834968.png)

![image-20221020174849752](Memory.assets/image-20221020174849752.png)

集中式刷新，隔一段时间进行逐行的刷新，刷新的时候不可以操作内存

存取周期是对[内存](https://so.csdn.net/so/search?q=内存&spm=1001.2101.3001.7020)进行一次读/写操作从得到地址到完成读/写操作以及下一次读/写操作开始前的总时间；

![image-20221020175731787](Memory.assets/image-20221020175731787.png)

![image-20221020175927647](Memory.assets/image-20221020175927647.png)

DDR SDRAM

