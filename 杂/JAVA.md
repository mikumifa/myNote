# JAVA

## Java的程序结构

- 源文件（.java):,名字要和类名字一样
- 类：类中有方法，方法必须在类中声明
- 方法：花括号里面的语句，方法代码是由一堆的语句构成的。

## 剖析类

java会执行

```java
pubilc static void main (String[] args){ }
```

程序至少有一个类，只有一个main函数

main 必须要有static，public修饰

java的所有东西都属于类，建立源文件.java,然后编译成为新的类文件（.class)。真正的被执行的是类.执行程序就是要命令java虚拟机去加载hello这个类，开始执行main,直到代码结束。

```
javac main.java
java main
```



## 和c++的不同

- ```java
  String[] pets={" a"," b"," c"};//数组
  int x=pets.length;//数组的长度用length
  pets =new Dog[7];创造对象数组的方式不太一样。
  System.out.println("  ")//调用System.out的println方法。
  //print无换行符号，print有换行符
  ```

## 创建对象

- 需要两个类：一个是要被操控的类，一个是用来测试的类（带有main）
- 真正的java程序只会让对象和对象之间交互（互相调用方法)main()用来测试正在的类，启动你的java程序。

> 猜数游戏
>
> GuessGame.class
>
> Player.class
>
> GameLauncher.class
>
> 一开始GameLauncher,class会创建GuessGame的类，然后启动GuessGame.startGame（）；
>
> 然后创建3个Player对象，每一个对象进行随机生成数，并且游戏是否胜利。
>
> 

## Java的命名规则

名字必须字母或者_或者$开头.b避开java的关键字（public，static，void， char,boolean byte float,double long)等

## Primitive数据类型

- 4种整型，2种浮点，char,boolen.
- int long short,byte,,float,double
- boolean位数由JVM决定true或者false（和c++不一样）类似bool，
- char 类型在实践中少用。
- byte，一比特是8字节

## 对象的引用

（无法理解）

# 声明

声明和定义不区分（c++区分）

```c++
extern int i；//声明：告诉编译器名称和类型，可以重复
extern int i=10;//定义：编译器为变量或者对象分配到一块内存空间上，并取名字；
extern 是声明关键词
```

- 常量，java用final关键词（命名规范尽量大写）

# 枚举类型

```java
enum Size {S,M，L}；
SIze s=Size.M;可以这种方式声明
//枚举变量的值可能是上面的或者null
```

# 数学函数

Math类里面的

```
Math.sin,cos,tan,atan,atan2
Math.exp,log,log10
Math.PI,E
import static java.lang.Math.*;

```

# 类型转换

隐式类型转换和强制类型转换和c艹一样

double->int是截取，double+int或者double+float是全都变成double

# 操作符

++，--,=+,都和c++一样，并且也沿用了c++的短路求值||前面的对了的话就不用运算后面了。

|和&的位运算没有

```
>>和<<,为位运算是左移和右移，>>是用符号位补齐
```

# 字符串操作，，可以稍稍对比一下c++里面的string

#### 子串

```java
String greating="Hello"
String s=greating.substring(a,b);//第二个参数时不想复制的第一个字母,
子串的长度是b-a，好计算长度，[a,b),可以这样理解
```

#### 拼接

直接用加法，字符串后面加上非字符串，后面的会类型转换为字符串。（放在前面也可以）

String静态函数join

```java
String s=String.join(":","s","s","s")//s:s:s
String as=s.repeat(3);//repeat三次的函数
```

检查是否相等

```c++
String s="asd";
s.equals("asd");
"gre".equals("asd");//可以对字符串常量使用
//也可以用comparaTo函数，类似c语言里面的strcmp
```

#### 码点

码点：一个编码表中某个字符所对应的代码值（16进制书写，前面加上U+），Unicode码点有17个代码平面

char数据类型是采用16进制Unicode码点的代码单元。UTF-16采用不同长度的编码表示所有的Unicode码点，如果出现比较复杂的字符，是由连续的代码单元构成的。char太底层了，尽量不用char，

检查是否是空串

```java
s.equals("");s.length()==0；
```

s也有可能是null什么都没有。

StringAPI

API是application programming interface(应用接口)

构建字符串。普通的+的方式效率低。可以用`StringBuilder` 

```java
StringBuilder builder =new StringBuilder ();
builder.append("a");
builder.append("b");
String s=builder.toString();
```

## 输入和输出

```java
import java.util.*;//不是java.lang包中的话要import相应的包
Scanner in=new Scanner(System.in);//System.in是标准输入流
int a=in.nextInt();//读取下一个int
String a=in.nextLine();//读取下一行，空格不停止
String a=in.next();//读取下一个单词
//******************************************************************************
import java.util.Scanner;

public class In_my {
    public static void main(String[] args)
    {
        Scanner in=new Scanner(System.in);//System.in是输入流对象
        String name=in.nextLine();
        String password=in.nextLine();
        System.out.println(String.join("+",name,password));

    }
}

```

> 对于密码的输入使用Console类
>
> ```java
> import java.io.Console;
> public class Test
> {
>     public static void main(String[] args)
>     {
>         Console cons=System.console();//console(),静态方法返回,工厂方法	
>         String name=cons.readLine("Use Name is:");
>         char[] passWord=cons.readPassword("Password is:");
>         System.out.println(name);
>         System.out.println(passWord);
> 
>     }
> }
> ```
>
> 格式化输出和c语言一样
>
> %8.2f，8是指字段宽度，包括小数点，小数点前面和后面。

#### 参数索引和>标志

Systema.out.printf("%1$,%1$,%1$",s);//%1直接就是全部

或者Systema.out.printf("%1$,%$,%1$",s);

# 流程控制

和c语言一样，多了break带标签

```java
labels：
{

	break lebels；
}//直接跳到末尾

```

## 大数

```java
BigInteger a=BI
import java.lang.Math;
import java.math.BigInteger;
public class In_my {
    public static void main(String[] args)
    {
        BigInteger a=new BigInteger("100");//直接构造
        BigInteger b=BigInteger.valueOf(100);//valueOf是把long变成大数
        BigInteger c=a.add(b);
        BigInteger d=a.multiply(a.add(BigInteger.valueOf(2)));
        System.out.println(d+","+c);
    }
    
```

## 创建数组

```java
int[] maths={1,2,3,4,5,6};
int[] a=new int[100];
//初始化中int为0，boolen为false，对象数组为null，例如String就是null
//特殊的遍历（c++也有）
for(int eachElement: a)
{
System.out.printLn(eachElement);
}
```

# 拷贝数组

Arrays的静方法copyOf

```java
import java.lang.reflect.Array;
import java.util.Arrays;

public class In_my {
    public static void main(String[] args)
    {
        int[] a={1,2,3,4,5};
        a=Arrays.copyOf(a,a.length*2);//length居然是长度
        for(int element:a)
        {
            System.out.println(element);

        }
        System.out.println(Arrays.toString(a));//toString,而把数组以[ , , , ]输出
    }
}

```

## 排序

Arrays.sort();

二维数组

c语言动态创建，先创建x个int*指针数组a[x],在创建`a[i]=new int[y];`

而java直接`int [][]a=new int[10][6]`;并且可以有未知数在里面



## 方法的重写规则

- 参数列表与被重写方法的参数列表必须完全相同。
- 返回类型与被重写方法的返回类型可以不相同，但是必须是父类返回值的派生类（java5 及更早版本返回类型要一样，java7 及更高版本可以不同）。
- 访问权限不能比父类中被重写的方法的访问权限更低。例如：如果父类的一个方法被声明为 public，那么在子类中重写该方法就不能声明为 protected。
- 父类的成员方法只能被它的子类重写。
- 声明为 final 的方法不能被重写。
- 声明为 static 的方法不能被重写，但是能够被再次声明。
- 子类和父类在同一个包中，那么子类可以重写父类所有方法，除了声明为 private 和 final 的方法。
- 子类和父类不在同一个包中，那么子类只能够重写父类的声明为 public 和 protected 的非 final 方法。
- 重写的方法能够抛出任何非强制异常，无论被重写的方法是否抛出异常。但是，重写的方法不能抛出新的强制性异常，或者比被重写方法声明的更广泛的强制性异常，反之则可以。
- 构造方法不能被重写。
- 如果不能继承一个类，则不能重写该类的方法。

# Java 抽象类

------

在面向对象的概念中，所有的对象都是通过类来描绘的，但是反过来，并不是所有的类都是用来描绘对象的，如果一个类中没有包含足够的信息来描绘一个具体的对象，这样的类就是抽象类。

抽象类除了不能实例化对象之外，类的其它功能依然存在，成员变量、成员方法和构造方法的访问方式和普通类一样。

由于抽象类不能实例化对象，所以抽象类必须被继承，才能被使用。

父类包含了子类集合的常见的方法，但是由于父类本身是抽象的，所以不能使用这些方法。

在 Java 中抽象类表示的是一种继承关系，一个类只能继承一个抽象类，而一个类却可以实现多个接口。

------

## 抽象方法

如果你想设计这样一个类，该类包含一个特别的成员方法，该方法的具体实现由它的子类确定，那么你可以在父类中声明该方法为抽象方法。

Abstract 关键字同样可以用来声明抽象方法，抽象方法只包含一个方法名，而没有方法体。

抽象方法没有定义，方法名后面直接跟一个分号，而不是花括号。

声明抽象方法会造成以下两个结果：

- 如果一个类包含抽象方法，那么该类必须是抽象类。
- 任何子类必须重写父类的抽象方法，或者声明自身为抽象类。

继承抽象方法的子类必须重写该方法。否则，该子类也必须声明为抽象类。最终，必须有子类实现该抽象方法，否则，从最初的父类到最终的子类都不能用来实例化对象。

## 抽象类总结规定

- \1. 抽象类不能被实例化(初学者很容易犯的错)，如果被实例化，就会报错，编译无法通过。只有抽象类的非抽象子类可以创建对象。
- \2. 抽象类中不一定包含抽象方法，但是有抽象方法的类必定是抽象类。
  - 假设其子类都有一些相同的方法，有不想使用父类，可以是抽象类
  - 父类有方法的实现情况随子类来定，可以用抽象方法。
- \3. 抽象类中的抽象方法只是声明，不包含方法体，就是不给出方法的具体实现也就是方法的具体功能。
- \4. 构造方法，类方法（用 static 修饰的方法）不能声明为抽象方法。
- \5. 抽象类的子类必须给出抽象类中的抽象方法的具体实现，除非该子类也是抽象类。

# Java 接口

接口（英文：Interface），在JAVA编程语言中是一个抽象类型，是抽象方法的集合，接口通常以interface来声明。一个类通过继承接口的方式，从而来继承接口的抽象方法。

接口并不是类，编写接口的方式和类很相似，但是它们属于不同的概念。类描述对象的属性和方法。接口则包含类要实现的方法。

除非实现接口的类是抽象类，否则该类要定义接口中的所有方法。

接口无法被实例化，但是可以被实现。一个实现接口的类，必须实现接口内所描述的所有方法，否则就必须声明为抽象类。另外，在 Java 中，接口类型可用来声明一个变量，他们可以成为一个空指针，或是被绑定在一个以此接口实现的对象。

### 接口与类相似点：

- 一个接口可以有多个方法。
- 接口文件保存在 .java 结尾的文件中，文件名使用接口名。
- 接口的字节码文件保存在 .class 结尾的文件中。
- 接口相应的字节码文件必须在与包名称相匹配的目录结构中。

### 接口与类的区别：

- 接口不能用于实例化对象。
- 接口没有构造方法。
- 接口中所有的方法必须是抽象方法，Java 8 之后 接口中可以使用 default 关键字修饰的非抽象方法。
- 接口不能包含成员变量，除了 static 和 final 变量。
- 接口不是被类继承了，而是要被类实现。
- 接口支持多继承。

### 接口特性

- 接口中每一个方法也是隐式抽象的,接口中的方法会被隐式的指定为 **public abstract**（只能是 public abstract，其他修饰符都会报错）。
- 接口中可以含有变量，但是接口中的变量会被隐式的指定为 **public static final** 变量（并且只能是 public，用 private 修饰会报编译错误）。
- 接口中的方法是不能在接口中实现的，只能由实现接口的类来实现接口中的方法。

### 抽象类和接口的区别

- \1. 抽象类中的方法可以有方法体，就是能实现方法的具体功能，但是接口中的方法不行。

- \2. 抽象类中的成员变量可以是各种类型的，而接口中的成员变量只能是 **public static final** 类型的。

- \3. 接口中不能含有静态代码块以及静态方法(用 static 修饰的方法)，而抽象类是可以有静态代码块和静态方法。

- \4. 一个类只能继承一个抽象类，而一个类却可以实现多个接口。、

- ```java
  public interface In_my {
      public abstract  void move();
      public abstract void jump();
  }
  class People implements In_my{
      private int pos;
      People()
      {
          pos=1;
      }
      public void move()
      {
          pos++;
      }
      public void jump()
      {
          pos+=10;
      }
      public int getPos()
      {
          return pos;
      }
  }
  /* ************************/
  
  public class Test
  {
      public static void main(String[] args)
      {
        People pep=new People();
        pep.jump();
        System.out.println(pep.getPos());
        pep.move();
        System.out.println(pep.getPos());
  
      }
  }
  ```

  #### 枚举值的使用

  ```java
  
  enum Color
  {
      Red,White,Black;
      private Color()//构造函数必须是private
      {
          System.out.println("create a color called:"+this.toString());
      }
      public void senTence()//可以在里面构造函数
      {
          System.out.println("Color function is operated"+this.toString());
      }
  
  
  }
      public class Test
  {
      public static void main(String[] args)
      {
          Color[] a=Color.values();
          System.out.println(a[2].toString());
          System.out.println(Color.valueOf("Black"));
          System.out.println(a[2].ordinal());
          System.out.println(a[0]);
          //valueof,values,ordinal三种方式
      }
  }
  ```

  

super(),调用父类的构造函数

捕获异常的finally是用来关闭输入流的

assert断言

```
assert condition :expression
查看条件，如果条件是false就把expression传入进去。
断言用来测试阶段判断错误
```

 

##     JAVA类

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
>  public static void main(String[] args)
>  {
>      People ma=new People();
>      Date r_a=ma.getA();
>      r_a.setTime(1);//通过应用把值给改了。相当于c++返回指针，把值给改了。把引用理解为指针
>      System.out.println(r_a);
>  }
> }
> class People
> {
>  private Date a;
>  public People()
>  {
>      a=new Date(12123);
>  }
>  public Date getA()
>  {
>      return a;
>  }
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



//java

```java
Collections.sort(students, new Comparator<Student>() {
    public int compare(Student o1, Student o2) {
        if(null == o1.getAge()) {
            return 1;
        }
        if(null == o2.getAge()) {
            return -1;
        }
        return o2.getAge().compareTo(o1.getAge());
    }
});
```

java sort

函数
