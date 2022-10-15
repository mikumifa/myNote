# Booth算法推导的理解



我觉得booth算法的推导可以理解为下面乘法的变形

```c++
   //这个是我用代码实现的手算乘法
int X=1234;
    vector<int>M={1,2,3,4};
    int n=4;
    int ans=0;
    for(int i=0;i<n;i++){
        ans=ans*10+M[i]*X;//乘10相当于左移，for循环中i++，相当于右移取低位
    }
```

这种在编程里面是比较常见的方法，c语言里面把字符串编程int时候就会使用

```c++
ans=ans*10+c[i]-'0';
```

但是补码的最高位是符号位，![image-20221004183806805](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221004183806805.png)

也就是说最高位是<img src="C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221004183835574.png" alt="image-20221004183835574" style="zoom: 80%;" />，。booth算法的处理，就是把最高位的-2^n-1变成正的2^n-1

![image-20221004184109220](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221004184109220.png)

可以看到，推导到上面时候相当于一个无符号数 $ S_n.....S_3S_2S_1$,然后S~n~=y~n-1~-y~n~.

然后就可以用上面的` ans=ans*10+M[i]*X;`,ans=ans*2+S~i~ *X;也就是

```
    int X=1010;
    vector<int>S={0,-1,0,1};
    int n=4;
    int ans=0;
    for(int i=n;i>=1;i--){
        ans=ans*10+S[i]*X;
    }
```

不过booth算法是从低位向高位算的，所以是-2；

```
    int X=1010;
    vector<int>S={0,-1,0,1};
    int n=4;
    int ans=0;
    for(int i=1;i<n;i--){
        ans=ans*0.5+S[i]*X;
    }
```

```
 ans=ans*0.5+S[i]*X这个式子就是booth公式的推导
```

![image-20221006190353388](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221006190353388.png)

老师好，感谢老师上课提起我的想法，我最后有几个错误，我现在已经全部理清，然后修改了，应该说是基本上掌握booth算法的思想了，

![image-20221006190618526](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221006190618526.png)

-2我应该是想说2的-1次方，但是打错了，然后那个循环是步骤是彻底的错了。

但ans=ans*0.5+S[i]*X这个步骤是对的，下面是10进制的验证。

![image-20221006190738921](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221006190738921.png)

然后，为什么这个公式的形式和书上的完全不一样。

![image-20221006191413693](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221006191413693.png)

我发现是因为我的ans不是Pi。

ans=ans*0.5+S[i]*X这个式子，相当于，右移之后加上[-X]c.

而booth算法上面的Pi是Pi-1加上[-X]c.后右移

![image-20221006191543284](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221006191543284.png)

所以我可以认为，我的ans右移之后的结果是Pi，也就是，0.5*ans=Pi。

```
ans=ans*0.5+S[i]*X
0.5*ans=0.5*(ans*0.5+S[i]*X)
0.5*ans=Pi
Pi1=0.5*(Pi+S[i]*X)
```

这就和ppt上的一样了。

更改一下代码

![image-20221006192220715](C:\Users\mikumifa\AppData\Roaming\Typora\typora-user-images\image-20221006192220715.png)
