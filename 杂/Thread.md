# 线程

#### 创建线程的方法

继承Thread，重写runable

```java
public class Thread01 extends Thread {
    public void run (){
        int time=0;
        while (time!=10) {
            try {
                System.out.println("hello word"+(++time)+Thread.currentThread().getName());
                sleep(1000);

            } catch (Exception e) {
                e.printStackTrace();
            }
        }

    }
}
/*************
public class Thread01Test {
    public static void main(String[] args) throws InterruptedException {
        Thread01 t=new Thread01();
        System.out.println(Thread.currentThread().getName());
        t.start();//启动线程,会以启动线程的方式启动t.run()
        //main线程启动子程序，主线程不会阻塞，会继续执行
        for(int i=0;i<10;i++){
            System.out.println("主线程i="+i);
            Thread.sleep(1100);
        }
    }
}

```



```java
public class Thread02 {

    public static void main(String[] args) {
        Dog dog=new Dog();
        Thread thread=new Thread(dog);
        thread.start();
    }
}
class Dog implements Runnable{
    int count=0;

    @Override
    public void run() {
        int time=0;
        while (time!=10) {
            try {
                System.out.println("hello word"+(++time)+Thread.currentThread().getName());
                Thread.sleep(1000);

            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }
}

```

### 线程终止

T1线程中可以控制T2线程的变量。

### 线程常用的方法

![image-20220928200906426](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928200906426.png)

> 

run方法只是普通的方法，多线程要靠start

interrupt用于中断sleep

### 线程插队

![image-20220928202702507](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928202702507.png)

yield（可能礼让成功,取决有系统的CPU数目）

在线程A中使用B.join（）则B做完了之后A线程才开始..

### 线程守护

![image-20220928203833474](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928203833474.png)

Deamon（守护）

```java
A.setDeamon(true)//设置守护线程，这条语句在哪里，就表示是哪里的守护线程
        T1.setDaemon(true);
        T1.start();//要先设置再启动
```

### 线程状态

![image-20220928210125018](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928210125018.png)

Runable状态是可运行状态，是否运行要看机器

![image-20220928210558424](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928210558424.png)

# Synchronized

线程同步机制，保证数据在同一个时刻只可以被一个线程访问。

![image-20220928211524776](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928211524776.png)

进去拿锁，出去放回去，同步的代码就是只能有一个同时访问的代码

```
public synchronized void run(){
在同一个时刻只有一种方法可以使用
}
```

### 互斥锁

![image-20220928212343135](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20220928212343135.png)

```java
synchronize（锁）{
}//非静态是this，静态的是 ClassName.class,同一把锁
```

