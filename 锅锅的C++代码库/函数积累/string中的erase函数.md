### string函数用法

> string.erase(pos,n)      //删除从pos开始的n个字符   string.erase(0,1);  删除第一个字符

```c++
#include <string>
#include <iostream>
 
using namespace std;
 
int main()
{
   string::iterator i;
   string s;
   cin>>s;
   s.erase(1,2);
   cout<<s;
    return 0;
}
```

> string.erase(pos)      //删除pos处的一个字符（pos是string类型的迭代器）

```c++
#include <string>
#include <iostream>
 
using namespace std;
 
int main()
{
   string::iterator i;
   string s;
   cin>>s;
   i = s.begin()+3;
   s.erase(i);
   cout<<s;
    return 0;
}
```

> string.erase(first,last)   //删除从first到last中间的字符（first和last都是string类型的迭代器）

```c++
#include <string>
#include <iostream>
 
using namespace std;
 
int main()
{
   string::iterator i;
   string s;
   cin>>s;
   s.erase(s.begin()+1,s.end()-1);
   cout<<s;
    return 0;
}
```

### 例题

> **编写函数去除字符串中包含的非字母字符(不包括空格)，并将小写字母转换成大写字母。**
> **注意，不在函数中输出。**
>
> 输入输出应在主函数中进行。
>  【输入格式】
>  待转换的字符串，字符串间会包含空格，长度不超过200。
>  【输出格式】
>  转换后的字符串
>  【输入样例】
>  happy new year!
>  【输出样例】
>  HAPPY NEW YEAR
> 时间限制：500ms内存限制：32000kb

------------------------------------------------
```c++
/*
 * 用的string 的 erase函数
 */
#include "iostream"
#include "algorithm"
#include "string"
using namespace std;
int main() {
	string s;
	getline(cin, s);
	for (int i = 0; i<s.length(); ) {
		if ((!isalpha(s[i])) && (s[i] != ' ')) {
			 s.erase(i,1);
		}
		else {
			if (islower(s[i])) {
				s[i] = toupper(s[i]);
			}
			i++;
		}
	}
	cout << s << endl;
	return 0;
}
```

