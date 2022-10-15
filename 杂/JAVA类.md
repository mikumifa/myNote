# JAVA类

- java 文件名字必须金额public类的名字相匹配。在一个文件夹中必须只有一个公共类，但是可以有任意数目的非公共类。
- 通配符*，假设文件夹中有` Employee.java`和`EmployeeTest.java`则可以使用` javac Employer*.java`用通配符的方式编译。或者直接`javac EmployerTest.java`,编译器会自动的搜索`Employee.java`.

#### constructer

- 只能通过new，不能通过`.`，必须跟上new
- 构造器和class同名
- 构造器可以有多个，参数的个数随意
- 构造器没有返回值

> 构造器中不要用和实例字段一样的，

##### var

var字段相当于auto变量，能从右边推断的就不需要写变量名字。

##### null问题的处理

> 调用null的方法会出错

问题解决：

- 先搞清楚那些可能是null；

- 使用“宽容型”方法

  ```java
  if(n==null) name="unknown"; else name=n;
  //Objects,类有简单的处理方法
  name=Objects.requireNonNullElse(n,"unknown");
  ```

- 使用严格型，直接拒绝访问null参数

```java
Objects.requireNonNull(n,"报错信息")；
```



#### this

和c++一样有this，不过java的this是用`.`c++用`->`

> 类中的返回对象不要是可变对象的应用的访问器方法，在**java中任何一个对象变量都是对堆区里面一个变量的引用**。除了基本数据类型，如果返回了一个可变对象的应用，那么就可以从外界更改这个可变对象的值
>
> ```java
> import java.security.Principal;
> import java.time.*;
> import java.sql.Date;
> public class test {
>     public static void main(String[] args)
>     {
>         People ma=new People();
>         Date r_a=ma.getA();
>         r_a.setTime(1);//通过应用把值给改了。相当于c++返回指针，把值给改了。把引用理解为指针
>         System.out.println(r_a);
>     }
> }
> class People
> {
>     private Date a;
>     public People()
>     {
>         a=new Date(12123);
>     }
>     public Date getA()
>     {
>         return a;
>     }
> }
> ```

##### final

相当于const，只有构造函数的时候可以初始化，但是当const是可变对象的时候，只是表示他不能更改引用了，其引用的对象是可以改变的。

> **在c++中返回的都是副本，是clone()后的值，但java默认返回的都是引用，类似c++的指针**

##### static

和c++一样，同一个static所有的类所公用。。。

##### 静态常量

使用的比较多类似于math里的pi是公共的静态的常量。

##### 静态方法

和c++一样，静态方法只可以访问静态的字段，不可以实例id，可以直接使用类名来调用

##### 工厂方法

- 静态方法的一个应用就是使用工厂方法来构造对象
  - 使用工厂方法的原因和用途
    - 构造器的名字无法命名，可以用静态方法来构造区分不同的类型
    - 工厂方法可以返回子类的。

#### 构造

- 会给一个初始化的值，但是尽量手动初始化。

- this（。。。。。。）

  ```java
  //java中可以使用this来在构造器里面调用其他的构造器
  this（参数1，参数2）；
  ```

##### 包(package)

- 主要是为了防止命冲突。

- `*`只能表示一个包，

- 访问包的2种方式

  - 一种是直接`java.time.LocalDate`
  - 另一种是在开头`import java.time.*;`,如果冲突了，就加上完整的包名。

- 静态导入

  - import可以导入静态的方法和静态的字段，这样在使用静态的方法的时候就不需要加上前缀了，例如

    ```java
    system.out.println("hello ");
    //有了
    import static java.lang.System.*;
    //就可以直接
    out.println("hello");
    ```

    

##### 在包中增加类

```java
package com.hostmnann.corejava;
public class Employee
{
}
//而在cmd操作里面，javac是用com/mycompany/...
//而java是用com/my/....来完成的。
```

```java

import java.util.Arrays;
import java.util.Comparator;
public class test {
    public static void main(String[] args)
    {
        People[] arr=new People[3];
        arr[0]=new People(9);
        arr[1]=new People(5);
        arr[2]=new People(3);
        Arrays.sort(arr);
        for(var v:arr)
        System.out.print(v.getA()+" ");
        Arrays.sort(arr,new Comparator<People>(){//一种是定义Comparator类
            public int compare(People a,People b)
            {
                return Integer.compare(b.getA(), a.getA());
            }
        });
        for(var v:arr)
        System.out.print(v.getA()+" ");
    }
}
class People implements Comparable<People>//一种是数组里面有comparable接口，然后定义compareTo
    //返回值
//如果指定的数与参数相等返回 0。

//如果指定的数小于参数返回 -1。

//如果指定的数大于参数返回 1。
{
    private int a;
    People(int v)
    {
        a=v;
    }
    public int getA()
    {
        return a;
    }
    public void setA(int o)
    {
        this.a=o;
    }
    public int compareTo(People o)
    {
        return Integer.compare(this.a, o.a);
    }
}

```

