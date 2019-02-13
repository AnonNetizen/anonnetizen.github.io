# C++代码风格

具体的代码风格每个人都有不一样的理解，这里只放一些约定俗成的之类的东西

## 命名

不加前缀时：

eg.

```cpp
int whatTheFuck;    //变量，驼峰式命名法
int WhatTheHell();  //函数，第一个单词就大写（帕斯卡命名法）
```

加前缀用匈牙利式：

eg.

```cpp
int iWillMoYou;       //i是int的缩写
```

### 前缀
```cpp
1.整型的前缀 
short sValue;     //s为short的前缀 
int iAge;         //i为int的前缀 
unsigned int uiAge;   //ui为unsigned int的前缀（两个单词的首字母） //也有用u做前缀的 
long lValue;      //l为long的前缀 

2.浮点型的前缀 
float fScore;    //f为float的前缀 
double dValue;   //d为double的前缀 

3.字符型的前缀 
char cChar;      //c为char的前缀
TCHAR tcChar;    //多字节字符和Unicode字符兼容类型的前缀tc wchar_t  wcChar   //宽字符前缀wc 

4.字符串的前缀 
char szName[30];  //sz为C语言字符串的前缀 string strName;   
//str为C++字符串变量的前缀 CString strInfo;  
//str为MFC字符串变量的前缀 

5.布尔型的前缀 
bool bPass;      //b为bool的前缀 

6.指针型的前缀  
int *pValue;    //p为指针的前缀,p后是否再加变量类型自己决定

7.数组的前缀   
int arrNum[10];  //arr为数组的前缀，同上，arr后是否再加数组元素的数据类型前缀自己决定。

8.枚举变量的前缀  
enum  emWeek;    //em为枚举变量的前缀 

9.结构变量的前缀 
T_NODE  tNode;    //结构名称以T_开头 10.字节变量的前缀：by BYTE  byInfo;  

10.字符指针的前缀 
LPCTSTR  ptszInfo;     //ptsz表示前缀，t表示TCHAR类型 LPCSTR  pszInfo; LPSTR  pszInfo; 

11.STL容器类型前缀 
vector<int>  vecValue;   //vec表示vector容器的前缀
```
### 缩写

[牛津英语缩写](https://public.oed.com/how-to-use-the-oed/abbreviations/)

[韦氏词典中的缩写](https://en.wiktionary.org/wiki/Wiktionary:Abbreviations_in_Webster)

## 注释

### 块注释

`/* */`不能嵌套

```cpp
/*这样写
也
可以*/

/*
 *但是一般在每一行前加"*"，并且"*"对齐
 *第一行和最后一行不写东西
 */
```

---

***下面的有争议***

## using namespace std

STD里东西太多，直接用`using namespace std`有一定风险，可能会导致命名冲突，如STD里有`search()`函数。

可以通过把STD要用的东西分别写出来的方法，显式声明，降低风险

eg.

```cpp
using std::cin;
using std::cout;
using std::ios_base;
using std::max;
using std::memset;
using std::min;
using std::sort;
using std::sqrt;
using std::string;
using std::vector;
...
```