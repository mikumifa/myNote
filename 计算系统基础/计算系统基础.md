

# 数据类型

| C类型     | 32位机器(字节) | 64位机器(字节) |
| --------- | -------------- | -------------- |
| char      | 1              | 1              |
| short     | 2              | 2              |
| int       | 4              | 4              |
| long int  | 4              | 8              |
| long long | 8              | 8              |
| char *    | 4              | 8              |
| float     | 4              | 4              |
| double    | 8              | 8              |

### long和指针的长度不同其他都一样

#### 大端法和小端法

![image-20220926221057155](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926221057155.png)

## ASCLL码

字母A 65，字母a 97，两者相差32

## 无符号整形

![image-20220926221623095](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926221623095.png)

## 有符号整数

- 正数开头是0

![image-20220926223816417](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926223816417.png)

![image-20220926224435374](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926224435374.png)

![image-20220926224519957](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926224519957.png)

符号扩展（SEXT，sign-extension,sext）

​	

![image-20220926224609405](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926224609405.png)

#### 检查溢出的方式，是

- 加法，就是相同符号运算后的结果和原来的符号位不一样

浮点数---定点小数

#### 二进制转化

二进制数转小数是采用乘2取整，正着看。除一次算一次位。

![image-20220926225408334](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926225408334.png)

阶码部分是无符号的整数，偏移127使得有负数的部分

阶码是0000001时候是-126，解码是0000000时候是-126,平稳过渡,但是尾码就没有0了

![image-20220926230148357](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926230148357.png)

![image-20220926230256645](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926230256645.png)

![image-20220926230318343](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926230318343.png)

#### 浮点数预算没有结合性

![image-20220926230401604](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926230401604.png)

![image-20220926230413422](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220926230413422.png)

补码反码原码，三者关系

原码的0重复所有上限和下限都是2^n-1-1,1000和0000重复

反码的0000和1111重复，所有所有上限和下限都是2^n-1-1，遇见符号位是1的，就取反，就是他的绝对值

补码使用取反加1来确定，这样负数会多出一个1000，这个就表示2^n-1-1