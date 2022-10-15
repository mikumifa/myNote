# weak_3

java任意模板类，Object指向任意的对象。

> 标准的包裹类，支持基本类型的包裹类
>
> java 5之前，抽象取出是object类，要用强制类型转化

java 5之后的类型c++模板的实现。放进什么类型，返回什么类型，原理是用引用。c++是编译出不同的代码

java实际是限制类型。`Class<Type>`,type不可以是基本类型。

##### java库里的泛型

comparable类型，接口对应的对象是可以比较大小的。

```
Comparable findMax(Comparable []a)
{
	Comparable maxValue=a[0];
	for(int i=1;i<a.length;i++)
	{
	if(maxValue.lessThan(a[i]))
		maxValue=a[i];
	}
	return maxValue;
}
```

# 算法分析

空间复杂度

- 组成

  - 指令空间

    - 指令会占用内存空间，大概就是编译成二进制码所占的内存空间。

    - > 一般不会分析，现代计算机不会一下子全部载入，会分段载入，占用量不会太大。

  - 数据空间

    - 

  - 环境栈空间(针对内存分析)

    - （递归的占空间）

  2部分

- 固定部分

- 变化部分

  - 空间复杂度关注变化部分，不关注固定部分。-+

  ```java
  publci static int SequentialSearch（int[] a,int x)
  {
  	int i;
  	for(int i=;i<a.length&&a[i]!=x;i++);//结尾i==a.length
  	if(i==a.length) return -1;//0和-1是否在栈内存未知。
  	return i;
  }
  //x,a,i,a.length是一样的。32位系统上限内存是4g，受限于地址不够
  //如果数据不算在当前的栈内存里面，数组a的空间没有算进去。
  S(n）=0；2
  ```

  

时间复杂度

- 编译时间
  - 往往是忽略的
- 运行时间
  - 数一下key operation的数目。
  - key operation，占大头的操作。