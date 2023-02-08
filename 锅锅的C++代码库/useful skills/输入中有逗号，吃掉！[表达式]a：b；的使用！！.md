### 例题

`点和正方形的关系`	
`【描述】`
`有一个正方形，四个角的坐标（x,y)分别是（1，-1），（1，1），（-1，1），（-1，-1），x是横轴，y是纵轴。写一个程序，判断一个给定的点是否在这个正方形内。`
`【关于输入】`
`输入坐标x，y`
`【关于输出】`
`点在正方形内，输出yes；点在正方形外，输出no`
`【例子输入】`
`0.5,0.5`
`【例子输出】`
`yes`
`【提示】`
`要注意正方形四个角的坐标（x，y）的边界条件`

应该是和边界的坐标比大小

感觉挺简单

不知道当时为啥写不对。。。

这是当时代码。。。

```c++
#include<iostream>
using namespace std;
int main() {
	int x, y;
	cin >> x >> y;
	if (-1<x<1&& -1<x<1)//表示点在正方形内且不包含边界；
		cout << "yes";//满足条件的输出
	else
		cout << "no";
	return 0;
}
```

哦我知道了！！！

**1.x,y不一定是int 类型啊，读不进去！！！以后一定要注意变量！**

**2.输入有一个逗号，怎么吃掉呢**

**3.if的条件句要拆开写啊笨蛋！！！**

**不能直接if (-1<x<1 && -1<y<1)错的！**

**4.x,y都写错了！**

真的是，漏洞百出。。。

#### 一、解决吃逗号问题

##### 1.把逗号存在c这个字符里

```c++
char c;
cin >> x >>c>> y;//c应输入逗号
```
这是一种方法，把逗号存在c这个字符里

##### 2.用cin.get()

但是它好像会把逗号读进来？

“读取任何一个字符赋给变量”

但是我不要逗号啊。。。

算了算了，就用上面那个。。。

写一段get,getline的区别吧，以防自己忘记

> 是否需要使用cin.get()吃掉输入流中的回车要依据下一次读取的方式而定。如使用cin.getline()或类C输入scanf()或put()等的时候，就需要用cin.get()在下一次读取前清空残余缓存；若使用cin>>则不需要，因为cin是智能指针，它将跳过缓冲区的无效字符（如这里的回车），直到找到非空白字符为止，然后它将读取字符，直到再次遇到空白为止。

#### 二、解决if的条件

`if (-1<x<1 && -1<y<1)错的！错的！`

应该是

`if (-1<x&&x<1 && -1<y&&y<1)`

接下来订正一下

```cpp
#include<iostream>
using namespace std;
int main() {
	float x, y;
	char c;
	cin >> x >> c >> y;
	if (-1<x && x<1 && -1<y&&y<1)//表示点在正方形内且不包含边界；
		cout << "yes";//满足条件的输出
	else
		cout << "no";
	return 0;
}
```

不知道对不对，等会编程网格试一下。。。

下面放一段学习一下。。。

```cpp
#include<iostream>
using namespace std;
#define MIN -1
#define MAX 1
int main()
{
    float x, y;
    char c;
    cin >> x >>c>> y;//c应输入逗号
    if (x >= MIN && x <= MAX && y >= MIN && y <= MAX)
        cout << "yes";
    else
        cout << "no";
    return 0;
}
```

还有个高级的用了？：的

```c++
#include <iostream>
using namespace std;
int main()
{
    int x, y, flag=0;
    cin >> x >> y;
    
    if ((x>=-1&&y>=-1) && (x<=1&&y<=1)) 
    flag = 1;
    
    cout << (in?"yes":"no") << endl;
    return 0;
}
```

哦哦 如果 in=1就是真的，非零，表达式为真， 输出a

不满足条件的话，表达式就为0，假的，输出b

这个就是flag用法的好处

 积累起来！！！

### ？：用法

> C语言中常用的表示判断并赋值的方式是使用if语句，当然也可以使用另一种结构：
>
> [表达式]?a：b;
> **其含义就是：如果表达式为真，则返回a的值，反之如果表达式为假，则返回b的值**。

下面是其一个小应用，输出a和b中的最大值：

```c++
#include<iostream>
#include<stdio.h>
int main()
{
	int a,b,c;
	scanf("%d,%d",&a,&b);
	c=a>b?a:b;
	printf("%d\n",c);
	system("pause");
}
```

哦哦哦懂了懂了耶！！!
