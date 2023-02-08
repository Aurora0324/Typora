# setprecision(n)的一些用法总结

 ==\#include <iomanip>  //不要忘了头文件==

` //第一种写法
    cout<<setiosflags(ios::fixed)<<setprecision(2);`

`   //第二种写法
    cout.setf(ios::fixed);
    cout<<setprecision(2);`

`   //第三种写法
    cout<<fixed<<setprecision(2);`

>  要保留几位小数setprecision(n)的括号里n就换成几。
> 前两种写法是一样的，第三种是简化写的。
> 上面的语句写一次就行了，对之后的数字都有效。

解释一下“语句**写一次就行了**，对之后的数字都有效”。在s之后设置保留两位小数之后，重新声明另一个数，输出依旧显示两位小数。所以设置精度语句只需写一次就可以了。

```cpp
1 #include <iostream>
2 #include <iomanip>　　　//设置必备的头文件
3 using namespace std;
4 int main()
5 {
6 	double s=12.345;
7 	cout<<setiosflags(ios::fixed)<<setprecision(2);
8 	cout<<s<<endl;　　　//输出12.35
9	
10	float pi=3.14159;
11	cout<<pi<<endl;　　　//输出3.14
12	
13	return 0;
14 }
```

### setprecision(n)

**功能：控制浮点数显示的有效数字个数。**

图中可以看出，只用setprecision(n)是控制保留几位有效数字的。

由8-9两行代码可以看出，也是只写一次就可以。
8-10行可以看出，只是四舍五入修改了数字的显示方法，并不是修改原数字。从常识我们可以知道，如果12.345数字本身改变，那就是两位有效数字变为 12，那从两位有效数字改为四位有效数字会变为 12.00，而不是12.34。
11-12行可以看出如果要保留的太多，是不会补上0的（往下看有补0的方法）。
13行中可以看出，如果小数点前的位数多于你要保留位数，则会使用科学计数法。

![img](https://img-blog.csdnimg.cn/556622fee33e492cbd84fc79db073740.png)

### **fixed**

setprecision(n)和fixed合用的话可以控制小数点后有几位。只要加上以下**任意一个**语句就可以。

`cout<<setiosflags(ios::fixed);
cout.setf(ios::fixed);
cout<<fixed;`

#### 例题1 配置生理盐水（p26)

```c++
#include <iostream>
#include <iomanip>  //不要忘了头文件
int main() 
{
    double answer_1=0;
    double answer_2=0;
    int i,n,t;//t为临时变量
    cin>>n;
    for(i=0;i<n;i++)
    {
        cin>>t;
        answer_1=0.09*t;
        amswer_2=0.91*t;
        cout<<	//第三种写法
	cout<<fixed<<setprecision(1);
    cout<<answer_1<<answer_2;
    }
return 0;
}
```

#### 例题2 计算分数的浮点数值 

> 【题目描述】
> 两个整数 a 和 b 分别作为分子和分母，既分数a/b，求它的浮点数值(双精度浮点数，保留小数点后9位)。
>
> 【输入】
> 输入仅一行，包括两个整数a和b。
>
> 【输出】
> 输出也仅一行，分数 a/b 的浮点数值（双精度浮点数，保留小数点后9位）。
>
> 【输入样例】
> 5 7
>
> 【输出样例】
> 0.714285714

```c++
#include <iostream>
#include <iomanip>
using namespace std;
int main()
{
    int a, b;
    double d;
    cin >> a >> b;
    d = (double)a/b;
    cout << fixed << setprecision(9) << d << endl;
    return 0;
}
```

或者

```c++
#include <iostream>
#include <iomanip>
using namespace std;
int main()
{
    int a, b;
    double d;
    cin >> a >> b;
    d = (double)a/b;
    cout << fixed << setprecision(9) << d << endl;
    return 0;
}
```

