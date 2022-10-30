## 自动机编程

自动机程序在每个时刻有一个状态 s，每次经过一个行动 f，转移到下一个状态 s’

[(21条消息) 算法总结：DFA（自动机）算法是什么，怎么用_companion_zhang的博客-CSDN博客_dfa算法](https://blog.csdn.net/dauiwsbd/article/details/119278563)

**只需要建立一个覆盖所有情况的从 s 与 f 映射到 s’ 的转移规则即可解决问题。**

| 状态\字符 | 空格符0 | Alpha   | 换行符 |
| --------- | ------- | ------- | ------ |
| start     | start   | process | after  |
| process   | process | process | after  |
| after     | start   | process | after  |

先找出所有的阶段，还有可能得到的字符，建立一个映射表

```c++
		class Mycode {
		    string state = "start";
		    //使用hashmap存储状态转换表
		    unordered_map<string, vector<string>> table = {
		        {"start", {"start", "process", "after"}},
		        {"process", {"process", "process", "after"}},
		        {"after", {"start", "process", "after"}}
		    };
		    //定义状态转移规则
		    int ifc(char c) {
		        if (isspace(c)) return 0;
		        if (isalpha(c)) return 1;
		        if (c=='\n')) return 2;
		    }

			public:
				//定义一个flag初始化为true当进入新的一行后重新设置为true
				bool flag=true;
			    void get(char c) {
			        state = table[state][ifc(c)];//通过映射关系的得到应该的规则
			        if (state == "process") {
			            if(flag==true) cout<<c<<endl;
			            //当输出一个英文字母后设置flag为flase
			            flag=false;
			        }
			        else if (state == "after")
			        	//当进入新的一行后重新设置flag为true
			            flag=true;
			    }
		};
		//主循环
		int main{
			char c;
			while(c != EOF){
				c =getchar();
				Mycode mycode;
			       mycode.get(c);
			}
		    return 0;
		}

```

```c++
class Mycode {
    string state = "start";
    //使用hashmap存储状态转换表
    unordered_map<string, vector<string>> table = {
        {"start", {"start", "negative", "process", "end"}},
        {"negative", {"end", "end", "process", "end"}},
        {"process", {"end", "end", "process", "end"}},
        {"end", {"end", "end", "end", "end"}}
    };
	//定义状态转移规则
    int ifc(char c) {
        if (c==" ") return 0;
        if (c == '+' or c == '-') return 1;
        if (isdigit(c)) return 2;
        return 3;
    }
	public:
	    int sign = 1;
	    long long res = 0;
	
	    void get(char c) {
	        state = table[state][ifc(c)];
	        if (state == "process") {
	        	//减48实现char数字到int数字的转换
	            ans = ( ans * 10 + c ) - 48;
	            //判断是否越界,比较时需要将INT_MAX转换成long long类型
	            ans = ( sign == 1 ) ? min(ans, (long long)INT_MAX) : min(ans, -(long long)INT_MIN);
	        }
	        else if (state == "negative")
	            sign = c == '+' ? 1 : -1;
	    }
};

class Solution {
public:
    int myAtoi(string str) {
        Mycode mycode;
        for (char c : str)
            mycode.get(c);
        return mycode.sign * mycode.ans;
    }
};

```

