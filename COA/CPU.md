# CPU

![image-20220915162354674](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915162354674.png)

**CPU**获取并执行指令的计算机组成部分，由一个ALU,一个控制单元和多个寄存器构成。在单处理单元系统，他通常被称为处理器

**处理器**含有一个或多个内核的物理硅片。处理器是计算机组件，用于解释和执行指令。如果一个处理器包含多个内核，则称其为多核处理器。

![image-20220915163006499](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915163006499.png)

##### 对衬底参入其他元素，形成n沟道，在加入氧化物，再加上金属。形成nmos的场效应管，电流会从漏极流向源极

PMOS同理。CMOS构建逻辑门电路，利用门电路实现逻辑运算，构建cpu

#### CPU的面积是无法任意增大的

面积增大意味着，互连延迟增大，一个时钟周期需要大于最长互连延迟。（互连延迟可以理解为，每一个晶体管都传递一次信号的）

#### 问题1：CPU的频率不能无限提高

理论限制，MOS管开关，脉冲通过电路需要时间

​					为了信号同步，每个脉冲信号需要持续一定的时间

制造限制，芯片面积越来越大，导致连线延迟越来越大，需要信号在制定的时钟周期内从芯片的一角到另一角

​					频率越高（MOS管的开关延迟频率也越高)会导致开关的损耗越高，CPU耗电和散热会增加

#### 解决1:改进CPU芯片结构

​	晶体管数量的增加为更先进，更复杂的体系结构提供了基础。

#### 问题2：内存墙问题

​	主存和CPU之间传输数据的速度跟不上CPU的速度

#### 解决2：cache（容量小但是速度快，缓存）

#### 问题3：CPU等待I/O传输数据

​	CPU在等待IO设备保持空闲。

#### 解决3：采用中断机制

![image-20220915172243336](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915172243336.png)

![image-20220915172254818](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915172254818.png)

# 存储器

主存储器，cacha,寄存器也是主存储器的范围

#### 问题4：兼顾存储容量，速度和成本

- 约束
  - 大容量：越大越好
  - 高速度：跟上存储器
  - 低成本：相对于其他组件合理
- 约束之间的关系
  - 更短的访问时间，更高的每比特成本

#### 解决4：层次式存储结构

- 需求
  - 大容量数据存储
  - 高速性能
- 解决方案
  - 使用存储器层次结构而不是依赖单个存储器组件。

#### 问题5：I/O设备传输速率差异大

- 问题
  - I/O性能跟不上CPU速度的提升

![image-20220915175444961](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915175444961.png)

##### 解决5：采用缓冲区和改进I/O操作技术

##### 总线的基本特征

- 共享：？
- 分时：？

![image-20220915175729192](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915175729192.png)

![image-20220915175821258](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915175821258.png)

![image-20220915175830905](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915175830905.png)

#### 问题6

##### 计算机部件互连复杂

![image-20220915175956253](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915175956253.png)

地址线和控制线公用一条线，控制线是必须单独分开了

总结：

由于各个组件的发展不均衡的问题，会产生一些挑战，对于这些问题有

![image-20220915180109634](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220915180109634.png)