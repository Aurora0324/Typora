1、构造函数：
string str:空串，string s(str)复制str到s，string s(num,c)生成由num个c字符构成的字符串。

2、插入函数：
有两种push_back()和insert()，后者比较常用。
push_back()：尾部插入一个字符，例如s.push_back(‘p’);
insert()：例如s=“abcddss”，执行s.insert(s.begin(),‘i’)后在位置0前插入’i’变成"iabcddss"。

3、遍历：
借助迭代器或者下标，下标比较常用。迭代器分两种：正向和反向。
正向：string::iterator it=s.begin();it!=s.end();it++;
反向：string::reverse_iterator it=s.rebegin();it!=s.rend();it++;
其中*it表示该位置的字符。下标与字符数组一样，不再赘述。

4、查找：
1）、查找一个字符串：s.find(ss)，找到返回ss在s中的起始位置，否则返回-1；
2）、从某一个位置开始查找某个字符：s.find(‘t’,6)，从s的位置6开始查找字符’t’，找到则返回位置，否则返回-1；注意1）和2）都是返回第一次找到的位置;
3）、从末尾开始查找某个字符：s.rfind(‘t’);
4）、从某个位置开始查找第一个不属于s1的字符位置，例如s=“cdcdscds”,s1=“cdcdfff”，s.find_first_not_of(s1)=4，s的位置4字符不属于s1，类似的还有查找第一个属于s1的字符的位置,去掉not就好。

5、排序：
sort(s.bgein(),s.end());

6、分割截取：
有两个函数：substr()与strtok()。
s.substr(2,5)为s从2位置开始的5个字符组成的子串。
strtok()函数原型：char *strtok(char *s,const char *delim)
函数功能：分解字符串为一组字符串，s为要分解的字符串，delim为分隔字符串。
------------------------------------------------
```c++
const char *split=",;!";
char *p=strtok(str,split);　
 while(p!=NULL) { 　　
    cout<<p<<'\n'; 　　
    p=strtok(NULL, split); 　　
 } 
//按照分隔符",:!"来分割字符串str　　
 return 0; 　　
 
```

7、删除：
erase()函数，例如s=“12345678”，s.erase(s.begin()+3)后变为"1235678"，即把位置3的字符删掉。

8、替换：
repalce()函数：s.replace(pos,len,ss)，将s从pos开始的len个字符替换成ss，
s.replace(pos,n1,n2,c)，将s从pos开始的n1个字符替换成n2个字符c。

9、大小写转换：
tolower()和toupper()。循环遍历字符串的每一个位置s[i]=tolower(s[i])，大写转小写，或者s[i]=toupper(s[i])，小写转大写。
这里其实推荐用STL中的transform()函数，具体用法如下：
transform(s.begin(),s.end(),s.begin(),::tolower)大写转小写，小写转大写类似。

10、比较函数：
string支持<,>,<=, >=, ==, != 等操作。
compare()函数专门用做string的比较函数，s.compare(ss)=0说明ss == s,返回1表明s>ss，返回-1表明s<ss。

11、拼接函数：
c++的string支持直接相加，“cdd”+“sss”=“cddsss”。另外s.append(ss)表示在s最后加上ss，等同于s+=ss。
