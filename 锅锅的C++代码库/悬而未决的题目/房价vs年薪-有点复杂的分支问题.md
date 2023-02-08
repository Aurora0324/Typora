# 有点复杂的分支问题

## New Trick-使用flag标记

新学到的！！！！

就是，如果flag=1，做什么事；

flag=0，做什么事

这样当if之上再有条件时，就可以对应了

## 题目

```c++
题目 - 房价 vs 年薪	
描述
小袁同学今年刚毕业，成为了一名光荣的程序员。他找了一份工作，年薪是X万元，并且公司保证每年给他固定加薪8%。 小袁同学很开心，他看上了一套房子，售价是M万元，于是下决心攒钱买下。假设房子的价格每年稳定上涨10%，再假设小袁不吃不喝，把所有的钱都存下来买房。
那么请你帮他算算，他多少年后可以买的起这套房子？
如果100年内(含100年) 都不可能的话，则输出“Forget it.”
关于输入
一共有2行。
第一行是一个整数X，表示小袁同学的初始年薪；
第二行是一个整数M，表示房子的售价。
关于输出
如果有解，输出一个整数N，表示第N年小袁可以攒够钱买房子；
如果解大于100或者无解，则输出“Forget it.”
例子输入
20
100
例子输出
7
提示
如果第一年的年薪是X万，那么第二年的年薪是1.08X万
```

## 错误代码

```c++
#include<iostream>
#include<cmath>
using namespace std;
int main() {
	int year = 1;//year表示可以攒够钱的年份
	double money_0 = 0;//money_0表示初始年薪  
	double G = 0;
	G = pow(1.08, year-1) * money_0;//price_0表示第N年的年薪
	double price_0 = 0;//M表示房子的初始售价
	double F = 0;
	F = pow(1.1, year-1) * price_0;//F表示第N年的房价
 
	cin >> money_0;
	cin >> price_0;
	
	int flag = 0;
	while (year <= 100)
	{
		if (G >= F)
		{
			cout << year << endl;
			flag = 1;
			break;
		}
		
		if (G < F)
			year++;
	}
	
	if(flag==0)
		cout << "forget it." << endl;
	return 0;
}
```

## 报错

![image-20230208130908233](../../../typora 笔记/assets/image-20230208130908233.png)

**为什么我觉得没有任何毛病！啊啊啊啊啊崩溃了**

## 正确代码

### 1

```c++
#include <iomanip>
using namespace std;
int main()
{
    int N, K, i;
    double house = 200;
    double money;
    cin >> N >> K;
    money = N;
for (i=1; i<=20; i++)
{
        if (money >= house) break;
        house *= (100+K)/100.0;
        money += N;
    }
    if (i == 21) cout << "Impossible" << endl;
    else cout << i << endl;
    return 0;
}
```

### 2

```c++
#include<iostream>
using namespace std;
int main()
{
   int N;
   double K;
   while(cin>>N>>K)
   {
      int i;
      double count2=200,count1=50;
       for(i=1;i<20;i++)
       {
         count1=count1+N;
         count2=count2*(1.0+K/100);
         if(count1>=count2)
            {
            int M=i+1;
            cout<<M<<endl;
              break;
            }
       }
       if(i==20)
        cout<<"Impossible"<<endl;
   }
 return 0;
}
```

### 3

```c++
#include<iostream>
using namespace std;
int main()
{
    int n,k;
    while(cin>>n>>k)
    {
        int t=1;
        int m=n;
        double h=200;
        while(t<=21)
        {
            if(m>=h){cout<<t<<endl;break;}
            m=m+n;
            h=h*(1+0.01*k);
            t++;
        }
        if(t>21)cout<<"Impossible"<<endl;
    }
    return 0;
}
```

