#  STL- 常用算法

概述:

算法主要是由头文件<algorithm> <functional> <numeric>组成。

<algorithm>是所有STL头文件中最大的一个，范围涉及到比较、 交换、查找、遍历操作、复制、修改等等

<numeric>体积很小，只包括几个在序列上面进行简单数学运算的模板函数

<functional>定义了一些模板类,用以声明函数对象

### 遍历算法

#### 遍历容器

##### for_each

```c++
for_each (iterator beg,iterator end, _func);
```

遍历容器，每次都执行_func;

```c++
#include <iostream>
#include <vector>
#include<algorithm>
using namespace std;
int main(){   
    vector<int>a={1,2,3,15,1,2};
    for_each(a.begin(),a.end(),[](int val){
        cout<<val<<" ";
    });//lamada表达式
}
```

##### transform

```c++
transform(iterator beg1, iterator end1, iterator beg2, _func);//调用时候必须保证目标区域有足够的空间。
```

```c++
transform(source1Beg,source1End,source2Beg,destBeg,op)//针对第一源区间[source1Beg,source1End)以及“从source2Beg开始的第二源区间”的对应元素，调用:op(source1Elem,source2Elem) 并将结果写入以destBeg起始的目标区间内;要保证空间相同
op的返回值到目的数组
```

```c++
#include <iostream>
#include <vector>
#include<algorithm>
using namespace std;
int main(){   
    vector<int>a={1,2,3,15,1,2};
    vector<int>b=a;
    for_each(b.begin(),b.end(),[](int val){
        cout<<val<<" ";
    });
    cout<<endl;
    transform(a.begin(),a.end(),b.begin(),b.begin(),multiplies<int>());
        for_each(b.begin(),b.end(),[](int val){
        cout<<val<<" ";
    });
    cout<<endl;
    transform(b.begin(),b.end(),a.begin(),[](int x){
        return x+1;
    });
            for_each(a.begin(),a.end(),[](int val){
        cout<<val<<" ";
    });
        for_each(a.begin(),a.end(),[](int & val){//用for_each时候要记得加引用，如果想要改变某函数值。
        val+=1;
    });
}//将容器里面的元素转换，transform到另一个容器里面
```

#### 查找

##### find

```c++
#include <iostream>
#include <vector>
#include<algorithm>
using namespace std;
class BigThan2
{
public:
    bool operator() (int& val)
    {
        return val>2;
    }
};//仿函数的概念
bool bigThan2(int &val)
{
    return val>2;
}
int main(){   
    vector<int>a={1,2,3,15,1,2};
    vector<int>b=a;
    //find(iterator beg, iterator end, value);
    vector<int>::iterator it=find(a.begin(),a.begin(),1);
    cout<<*it<<endl;
    //find_if(iterator beg, iterator end, _Pred);
    //_Pred返回bool的仿函数。
    it=find_if(a.begin(),b.begin(),bigThan2);//可以传函数名字
    cout<<*it<<endl;
    it=find_if(a.begin(),b.begin(),[](int&val){//传lameda函数
        return val>2;
    });
    cout<<*it<<endl;
    it=find_if(a.begin(),b.begin(),BigThan2());//传仿函数，就是重载了operater();
    cout<<*it<<endl;
}
```

##### adjacent_find

查找相邻的重复元素，返回相邻元素的第一个位置的迭代器。

##### binary_search

查找元素是否存在

```c++
bool binary_search(iterator beg, iterator end, value);//顾名思义
```

##### count

```c++
count(iterator beg, iterator end, value);//统计元素个数
```

##### count_if

```c++
count_if(iterator beg, iterator end, _Pred);//count类似find
```

##### sort

```c++
sort(iterator beg, iterator end, _Pred);
```

_Pred是一个带有2个参数，返回为bool形的参数，最后会保证前后都满足true

```c++
#include <iostream>
#include <vector>
#include<algorithm>
using namespace std;
int main(){   
    vector<int>a={1,2,3,15,1,2};
    sort(a.begin(),a.end(),[](int x,int y){return x>y;});
    for_each(a.begin(),a.end(),[](int x){cout<<x<<" ";});
}

```

##### random_shuffle

洗牌 指定范围内的元素随机调整次序

```c++
random_shuffle(iterator beg, iterator end);
```

##### merge

两个容器元素合并，并存储到另一容器中,必须是有序的序列

```
merge(iterator beg1, iterator end1, iterator beg2, iterator end2, iterator dest);
```

##### reverse

将容器内元素进行反转

```c++
reverse(iterator beg, iterator end);
```

[(19条消息) C++基础学习之STL-常用算法_苏流瑾要努力变强的博客-CSDN博客_c++ stl常用算法](https://blog.csdn.net/qq_45812934/article/details/122664819)

## 拷贝函数![]()