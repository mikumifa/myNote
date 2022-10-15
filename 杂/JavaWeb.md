# JAVA

html和数据库

## 数据库相关概念

MySQL数据库管理系统

![image-20221002143140081](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002143140081.png)

### SQL语法

```
show databases;//展示数据库
-- 或者#或者/**/作为注释
```

![image-20221002144237608](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002144237608.png)

![image-20221002144321217](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002144321217.png)

## DDL

![image-20221002144356689](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002144356689.png)

```
show databases;//
//information_schema信息表
//mysql数据库
//performance性能信息
//sys系统信息
create database name;//创建数据库
create database if not exists namel//
drop database if exisis name;//
use names//使用数据库
select database();
```

### 操作表

```
use databaseName;//
show tables;//
desc tableName;//查询表的名称
mysql> create table tb_user(
    -> id int,
    -> username varchar(20),
    -> password varchar(32)
    -> );//基本语法
  
```

![image-20221002145729728](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002145729728.png)

### 数据类型

| 类型         | 大小                                     | 范围（有符号）                                               | 范围（无符号）                                               | 用途            |
| :----------- | :--------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- | :-------------- |
| TINYINT      | 1 Bytes                                  | (-128，127)                                                  | (0，255)                                                     | 小整数值        |
| SMALLINT     | 2 Bytes                                  | (-32 768，32 767)                                            | (0，65 535)                                                  | 大整数值        |
| MEDIUMINT    | 3 Bytes                                  | (-8 388 608，8 388 607)                                      | (0，16 777 215)                                              | 大整数值        |
| INT或INTEGER | 4 Bytes                                  | (-2 147 483 648，2 147 483 647)                              | (0，4 294 967 295)                                           | 大整数值        |
| BIGINT       | 8 Bytes                                  | (-9,223,372,036,854,775,808，9 223 372 036 854 775 807)      | (0，18 446 744 073 709 551 615)                              | 极大整数值      |
| FLOAT        | 4 Bytes                                  | (-3.402 823 466 E+38，-1.175 494 351 E-38)，0，(1.175 494 351 E-38，3.402 823 466 351 E+38) | 0，(1.175 494 351 E-38，3.402 823 466 E+38)                  | 单精度 浮点数值 |
| DOUBLE       | 8 Bytes                                  | (-1.797 693 134 862 315 7 E+308，-2.225 073 858 507 201 4 E-308)，0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 0，(2.225 073 858 507 201 4 E-308，1.797 693 134 862 315 7 E+308) | 双精度 浮点数值 |
| DECIMAL      | 对DECIMAL(M,D) ，如果M>D，为M+2否则为D+2 | 依赖于M和D的值                                               | 依赖于M和D的值                                               | 小数值          |



| 类型      | 大小 ( bytes) | 范围                                                         | 格式                | 用途                     |
| :-------- | :------------ | :----------------------------------------------------------- | :------------------ | :----------------------- |
| DATE      | 3             | 1000-01-01/9999-12-31                                        | YYYY-MM-DD          | 日期值                   |
| TIME      | 3             | '-838:59:59'/'838:59:59'                                     | HH:MM:SS            | 时间值或持续时间         |
| YEAR      | 1             | 1901/2155                                                    | YYYY                | 年份值                   |
| DATETIME  | 8             | '1000-01-01 00:00:00' 到 '9999-12-31 23:59:59'               | YYYY-MM-DD hh:mm:ss | 混合日期和时间值         |
| TIMESTAMP | 4             | '1970-01-01 00:00:01' UTC 到 '2038-01-19 03:14:07' UTC结束时间是第 **2147483647** 秒，北京时间 **2038-1-19 11:14:07**，格林尼治时间 2038年1月19日 凌晨 03:14:07 | YYYY-MM-DD hh:mm:ss | 混合日期和时间值，时间戳 |



| 类型       | 大小                  | 用途                            |
| :--------- | :-------------------- | :------------------------------ |
| CHAR       | 0-255 bytes           | 定长字符串                      |
| VARCHAR    | 0-65535 bytes         | 变长字符串                      |
| TINYBLOB   | 0-255 bytes           | 不超过 255 个字符的二进制字符串 |
| TINYTEXT   | 0-255 bytes           | 短文本字符串                    |
| BLOB       | 0-65 535 bytes        | 二进制形式的长文本数据          |
| TEXT       | 0-65 535 bytes        | 长文本数据                      |
| MEDIUMBLOB | 0-16 777 215 bytes    | 二进制形式的中等长度文本数据    |
| MEDIUMTEXT | 0-16 777 215 bytes    | 中等长度文本数据                |
| LONGBLOB   | 0-4 294 967 295 bytes | 二进制形式的极大文本数据        |
| LONGTEXT   | 0-4 294 967 295 bytes | 极大文本数据                    |

```
double的用法，相当于score double(总长度，小数点后面保留的位数)
name char(10),存储性能高，永远都是10字符，浪费空间
name varchar(10),储存性能低，节省空间
drop table if exists tb_user//删除表
```

![image-20221002151102495](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002151102495.png)

```
ADD,MODIFY,CHANGE,DROP
```

## DML数据操作

![image-20221002155141155](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002155141155.png)

查询数据

select  * from stu;

```
INSERT INTO `user`(ID,`name`) VALUES(1,'张三');
```

![image-20221002160934624](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002160934624.png)

![image-20221002161419407](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002161419407.png)

### DQL

![image-20221002161709912](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002161709912.png)

```
SELLECT NAME1,NAME2,NAME3 FROM TABLENAME;
SELLECT ADDTESS FROM STU;
SELECT DISTINCT ADDRESS FROM STU;/distinct关键字消除重复
SELECT MATH AS 别名，ENGLISH 别名 FROM STU;
```

![image-20221002162537702](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002162537702.png)

查询数值大小

```
=
!=
and
or
between and
in(value1,value2,value3)
null值只能用is null is not null
```

![image-20221002162833647](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002162833647.png)

### 模糊查询

```
select * from stu where name like '马%';
```

![image-20221002163125780](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002163125780.png)

```
select *from stu order by age;//order by是按照其他的排序，可以有好几个字段。
```

### 聚合函数

![image-20221002163730510](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002163730510.png)

![image-20221002163832085](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002163832085.png)

```
group by分组
```

![image-20221002164012262](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002164012262.png)

# IP

![image-20221002202527745](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002202527745.png)

网络的一些东西

![image-20221002202832677](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002202832677.png)

 用于表示计算机上的一个网络程序

域名是ip地址的一个映射

![image-20221002202954100](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002202954100.png)

用端口区分不同的服务

0-1024的端口用不了

## TCP和UDP协议

![image-20221002203211252](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002203211252.png)

TCP,用三次握手之后开始发送大量的数据，适合传输大量的数据，但是效率比较低

UDP不需要建立链接，数据比较小，速度快单数不适合大量的数据

## InetAddress类

```java
package com.test.java;

import javax.sound.midi.Soundbank;
import java.net.InetAddress;
import java.net.UnknownHostException;

public class Test {
    public static void main(String[] args) throws UnknownHostException {
        InetAddress localHost=InetAddress.getLocalHost();
        System.out.println(localHost);
        InetAddress host1=InetAddress.getByName("DESKTOP-9ARHU10");
        System.out.println(host1);
        System.out.println(host1.getHostName());
        System.out.println(host1.getAddress());
        System.out.println(host1.getHostAddress());//得到IP地址
        System.out.println(host2.getHostName());//主机名字或者域名
    }
}
```

## Socket编程

![image-20221002205114562](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002205114562.png)

![image-20221002211836351](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002211836351.png)![img](https://img2020.cnblogs.com/blog/1424293/202107/1424293-20210727163602973-649082407.png)

#### 对于网络编程的Socket的文件的传输

使用Socket.getInputStream()来构造BufferedInpurStream()

![image-20221002223417110](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002223417110.png)

文件必须要关闭，不然不会保存到文件里面

### netstat指令



![image-20221002224004256](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002224004256.png)

### UPD网络编程，

![image-20221003154655227](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221003154655227.png)

#### 项目开发流程

需求分析：该项目的功能，客户的要求

设计阶段：设计，UML类图，流程图，模块设计，数据库，架构，原型的开发，组建团队

实现阶段：1.程序员，完成架构师的模块功能，测试自己的模块

测试阶段：测试工程师，单元测试，测试用例，白盒测试，黑盒测试，集成测试

实施阶段：部署到客户的平台

维护阶段：发现bug解决/项目升级

### 实施细节

1. 用户交流对象而不是简单的字符串
2. Nio思想，socket是在线程里面
3. 线程会很多，要有一个管理线程的集合

![image-20221003162038085](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221003162038085.png)

1. Message和user是共有的类，在一个common的包里面实现。要实现Serializable序列化接口才可以变化

private static final long serialVersionUID=1L//最好配上这个才可以成功

2.在接口里面定义常量，messageType，（）接口中的常量，默认有public static final

枚举值一般都是

![image-20221003163614559](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221003163614559.png)

枚举相当于public static final

![image-20221003163949038](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221003163949038.png)

1. 命令行的登录界面，实现一个loop当loop是true是，显示菜单，当loopfalse时候退出循环。处理各种输入输出
2. p364Java
3. 工具类，提高开发效率，调用相关工具
   1. 输入用户和密码，然后发到服务器去验证，验证正确进入二级菜单，

4. 设置一个用户UserClientServer类，用于用户登录，验证用户注册的功能，由于这个方法类的很多方法需要user的操作，所以就写了一个user的成员对象，Socket在其他地方也会用到，所以也是一个属性