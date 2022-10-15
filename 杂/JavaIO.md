![image-20221002165842254](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002165842254.png)

![image-20221002165856781](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002165856781.png)

```java
package com.java.util;

import org.junit.jupiter.api.Test;

import java.io.File;
import java.io.IOException;

public class FileCreate {
    public static void main(String[] args) {

    }
    @Test
    public void create01(){
        String filePath="C:\\Users\\mikumifa\\Downloads\\news1.txt";//根据路径构建一个File对象
        File file=new File(filePath);
        try {
            file.createNewFile();
            System.out.println("Create successfully");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    @Test
    public void create02(){
        String fatherFilePath="C:\\Users\\mikumifa\\Downloads";//根据父文件加上子目录
        String childFilePath="new2.txt";
        File file=new File(fatherFilePath);
        try {
            File file2=new File(file,childFilePath);
            file2.createNewFile();
            System.out.println("Create successfully");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
    @Test
    public void create03(){
        String fatherFilePath="C:\\Users\\mikumifa\\Downloads";//根据父文件加上子目录
        String childFilePath="new3.txt";
        File file=new File(fatherFilePath,childFilePath);
        try {
            file.createNewFile();
            System.out.println("Create successfully");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

}

```

![image-20221002172006081](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002172006081.png)

创建file对象没有创建在内存之中，file对象只是在java程序中，只是一个java程序，只有执行createNewFile（）才可以创造新的。

![image-20221002172439017](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002172439017.png)

常用的方法

java中所有的目录都是当文件使用的

![image-20221002173121593](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002173121593.png)

## IO流

![image-20221002173142536](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002173142536.png)

·

```java
 public void  create04(){
        String inputAddress="c:\\Users\\mikumifa\\Downloads\\coa22-programming01.pdf";
        String outputAddress="c:\\Users\\mikumifa\\OneDrive\\桌面\\coa22-programming01.pdf";
        FileInputStream fileInputStream =null;
        FileOutputStream fileOutputStream =null;
        try {
            fileInputStream = new FileInputStream(inputAddress);
            fileOutputStream = new FileOutputStream(outputAddress);
            int val=0;
            byte[] valByte=new byte[1024];
//            while (true){
//                try {
//                    if (((val=fileInputStream.read())==-1)) break;
//                } catch (IOException e) {
//                    e.printStackTrace();
//                }
//                try {
//                    fileOutputStream.write(val);
//                } catch (IOException e) {
//                    e.printStackTrace();
//                }
//            }
            while ((val=fileInputStream.read(valByte))!=-1)
            {
                fileOutputStream.write(valByte,0,val);//文件读取的时候记得确定数组格式
            }
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                fileInputStream.close();
                fileOutputStream.close();
            } catch (IOException e) {
                e.printStackTrace();
            }

        }


    }
```

![image-20221002193956974](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002193956974.png)

关闭和刷新后才到文件里面

![image-20221002194439730](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002194439730.png)

### BufferedReader节点

流封装一个Reader，相当于封装的一个其他的

> 操作里面可以写一个readFile的抽象类，然后再具体实现类

```
readLine();//没有换行符
//关闭bufferReader会自动关闭fileReader
```

### BufferedReader

```
.newLine()换行符
```

节点流加true，表示是追加的方式，没有true是覆盖的方式

![image-20221002195716484](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002195716484.png)

![image-20221002200010974](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002200010974.png)

如果需要序列化需要实现序列化接口，不需要任何实现

![image-20221002200206910](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002200206910.png)

必须要顺序一致才可以

## 标准的输入输出

![image-20221002200625377](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002200625377.png)

```
Scanner sc=new Scanner(System.in);//他们就是标准输入输出流
```

# 乱码问题

没有制定文件的编码方式

> 转换流可以让字节流变成为字符流
>
> ANSI是国标码，相当于gdk，默认是UDF-8

用inputStringReader和outputStreamReader(这个是字节流)

![image-20221002201314312](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002201314312.png)

![image-20221002201346326](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002201346326.png)

### 打印流

PrintStream默认是打印到显示器，他是调用write的

### Propertis类

![image-20221002201722463](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002201722463.png)

![image-20221002201746846](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002201746846.png)

![image-20221002201847883](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221002201847883.png)