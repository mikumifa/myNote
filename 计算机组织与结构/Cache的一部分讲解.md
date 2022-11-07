# Cacha

Cache主要是为了解决内存墙带来的CPU和主存协作问题

### 程序访问的局部性

![image-20221103171316185](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031713220.png)

### 平均访问时间

![image-20221103171347687](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031713718.png)

## 映射

### 直接映射

![image-20221103171611723](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031716762.png)、

M是块数，C是行数

上面定义了Cacha直接映射时候的地址的结构，有C行所有logC的值是Cacha的行号和块内的地址。

然后一次存储单元是8个字，所有有16个单元就是说，寻址能力是4，所有前2位是用来区分映射到不同行的不同的块

![image-20221103171619997](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031716043.png)

通过cache字块的地址来找到对应的行，如果标记一样就命中。

![image-20221103171629191](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031716235.png)

![](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031716548.png)

优点；

- 简单
- 快速映射
- 快速检查

缺点

- 抖动现象：如果程序需要重复访问两个来自同一行不同块的字，需要不断的交换cache中，cache的命中率将会降低，

适用于大容量的cache

- 行数变多，发生冲突失效的概率降低
- 硬件电路简单，增大容量对Tc的影响不明显

### 关联映射

一主存块可以装入cache的任意一行

![image-20221103163757442](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031637483.png)

取消行的编号，直接储存块的编号

优点

避免抖动

缺点

- 实现起来比较复杂
- cache搜索代价大，检测时候要访问cache的每一行

适合小容量cache

- cache更容易产生抖动
- cache的搜素时间短

### 组关联映射

K-路组映射

![image-20221103163949633](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031639665.png)

k，一组中有k行

主存的块可以被映射到固定组的任意一行

![image-20221103164332474](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031643520.png)

## 替换算法

替换算法通过硬件来实现，设计替换算法的目的是提高命中率

### LRU

![image-20221103165625492](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031656547.png)

标记最近使用的元素：

当一个元素使用的时候，自己1，傍边的0（表示自己比傍边的经常访问)

![IMG_20221103_170753](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031708270.jpeg)

简单点，使用了就归0，其他的加1，如果要加入新的，就把数最大的给踢了，加入最新的。

需要的位数，对于每一组，要k个logk来做标记

LRU的提高效果没有那么高

### FIFO

![image-20221103171924946](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031719984.png)

### LFU

![image-20221103172322225](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031723263.png)

### 随机替换算法

![image-20221103172449656](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031724694.png)

## 写策略

### 写直达

所有写操作都同时对cache和主存进行

优点

确保主存中的数据总是和cache中的数据一致，总是最新的（例如多CPU 同步的场景）

缺点

产生大量的主存访问，减慢写操作

### 写回法

优点

- 减少了访问主存的次数

缺点

- 部分主存的数据可能不是最新的
  - I/O模块存取时可能无法获得最新的数据，为解决该问题会使得电 路设计更加复杂且有可能带来性能瓶颈

![image-20221103174308449](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031743483.png)

![image-20221103174351848](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031743879.png)

![image-20221103174618992](https://blog-1314638240.cos.ap-nanjing.myqcloud.com/image%2F202211031746026.png)