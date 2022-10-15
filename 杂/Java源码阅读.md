## Java抽象类和C++抽象类的区别

![image-20221007164958673](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221007164958673.png)

C++的抽象函数

```
virtual int f()=0;
```

只要有虚函数，那个类就是抽象类

抽象类不可以实例化，只有继承之后把虚方法实现之后才可以实例化。抽象类里面可以有非抽象的函数。

Java的接口要求所有的方法都是虚函数，不过可以用default来写出默认的

### LinkedList分析

```java
public interface ListIterator<E> extends Iterator<E> {
	boolean hasNext();
	E next();
	boolean hasPrevious();
	E previous();
    int nextIndex();
    int previousIndex();
    void remove();
    void set(E e);
    void add(E e);
}
//接口继承接口
```

抽象类B实现接口A，其中抽象类A还加了几个抽象的方法，抽象类B继承抽象类A，实现了抽象类的方法后，又家里几个抽象方法

![image-20221007171746659](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221007171746659.png)

抽象类的已经实现的方法可以直接使用抽象的方法（没有实现的方法）