# C++代码风格

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
int iWhatThe;       //i是int的缩写
```

### 前缀

1.整型的前缀 
short sValue;     //s为short的前缀 int iAge;         //i为int的前缀 
unsigned int uiAge;   //ui为unsigned int的前缀（两个单词的首字母） //也有用u做前缀的 
long lValue;      //l为long的前缀 

2.浮点型的前缀 
float fScore;    //f为float的前缀 
double dValue;   //d为double的前缀 

3.字符型的前缀 
char cChar;      //c为char的前缀 //个人喜欢用a做前缀 
TCHAR tcChar      //多字节字符和Unicode字符兼容类型的前缀tc wchar_t  wcChar   //宽字符前缀wc 

4.字符串的前缀 
char szName[30];  //sz为C语言字符串的前缀 string strName;   //str为C++字符串变量的前缀 CString strInfo;  //str为MFC字符串变量的前缀 

5.布尔型的前缀 
bool bPass;      //b为bool的前缀 

6.指针型的前缀  
 int *pValue;    //p为指针的前缀 
说明：由于指针是指向一定数据类型的变量，因此p后面要不要再加一个前缀一直让我举棋不定。如果再加上前缀比如：      int * piKey;   
char * pszInfo; 
这样似乎意义更完整，但势必会增加变量的字符长度。因此，这里就不硬性规定了。但是，指针变量以p开头应该是雷也打不动的。 


7.数组的前缀   int arrNum[10];  //arr为数组的前缀 
 
说明：和指针变量一样，arr后是否再加数组元素的数据类型前缀取决于你自己。 string arrstrName[3];  //C++字符串数组，加上去似乎很别扭 

8.枚举变量的前缀  
 enum  emWeek;    //em为枚举变量的前缀 

9.结构变量的前缀：t 
T_NODE  tNode;    //结构名称以T_开头 10.字节变量的前缀：by BYTE  byInfo; 

10.字节变量的前缀：by BYTE  byInfo; 

11.字变量的前缀 
DWORD  dwInfo;    //双字 WORD    wInfo;    //单字 

12.字符指针的前缀 
LPCTSTR  ptszInfo;     //ptsz表示前缀，t表示TCHAR类型 LPCSTR  pszInfo; LPSTR  pszInfo; 

13.STL容器类型前缀 vector<int>  vecValue;   
说明：vec表示vector容器的前缀，为了简化变量，变量体后面不再使用前缀 list<double>  lstInfo; 

### 缩写

[牛津英语缩写](https://public.oed.com/how-to-use-the-oed/abbreviations/)

[韦氏词典中的缩写](https://en.wiktionary.org/wiki/Wiktionary:Abbreviations_in_Webster)

## using namespace std

STD里东西太多，直接用`using namespace std`有一定风险，可能会导致命名冲突，如STD里有`search()`函数。

可以通过把STD要用的东西分别写出来的方法，显示声明，降低风险

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