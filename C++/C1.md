##### language

syntax （语法）semantics（语义）,pragmatics(句型，句子)，语法图（规则）

Deduct&reduce

推导树，计算机根据推导树来推导，能构成推导树，就是合适的语句。包含递归

compiler来判断是否合乎语法。formal method。

##### Programming

我们要关注data flow。要有science，the art of computer programming

have the knowledge of a computer's machine language,,

作用域，局部化，复合语句，函数传递，递归，动态数组



# Simula 67

提出了ool的概念

支持自顶向下面设计 OO Pparadigm，体现了OO的概念。

#### 限制发展的原因

- 欧洲，
- 没有IDE
- 非常昂贵
- 写出来的程序特别的大

# C++诞生

史前1979

- 研究分布式系统的系统软件组织
  - 设计：隔离良好的模块组合为软件
  - 实验：细节繁杂的模拟器 IBM/360
- 实现
  - Simula 第一阶段
- 优点
  - 良好的可读性
  - co-routine(pseudo-parallel)
  - 类的层次结构

# 结构化编程

#### DATA TYPE

常量就写成常量，C++地址所处的相对位置。

- 值集，类型决定取值范围，int 16位的时候是-32768~32767（2^15），（必须要知道)

> typedef int INT16,便于移植到其他计算机，其他计算机如果是32位，就typedef short int16

- 计算，同类型的计算（不同类型的是通过类型转换来计算实现的）

> ADT抽象数据类型
>
> 类型系统
>
> 强类型/弱类型，c++是强的
>
> 静/动，c++是动静结合的
>
> 类型安全不能代替测试？？、

#### 表达式

- 赋值表达式

  - 左值=右值表达式
    - 左值：可以出现在赋值表达式左部的表达式，具有存放数据的确定地址
    - 类型不同时，先完成右值表达式的计算，然后转换成为左值，然后赋值

- 逗号表达式的值是最后面的表达式的值。

- 异或操作

  - 和全0的不变

  - 全1的取反

  - 本身的全0

  - 和同一个对象2次不变，还原

  - ```java
    a=a^b;
    b=a^b;
    a=a^b;//交换
    ```

  #### 语句

  表达式语句

  - for

  - switch

  - > ```c++
    > swtich(整形常量表达式)//整形常量表达式的意思是他在这个时候已经确定了值
    > 
    > {
    > case 1:   break;
    > 
    > case 2:   break;
    > 
    > case 3:  break;
    > 
    > }//减少1,2,3,4的存在，使用enum来代替（有时间实践一下），上面使用符号常量，使得跟容易读
    > switch使用集中处理捕捉行为。log记录
    > ```
    >
    > 修改resource资源来实现汉化。

  IO语句（cin,cout,>>,<<可以重载）

  控制流语句

