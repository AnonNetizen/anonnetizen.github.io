# `Sort()`函数

`sort()`为标准库自带排序函数，非常常用。可以让人省去很多时候写排序算法的麻烦。作为快排速度也很快，能满足大多数情况下的使用。

`sort()`能对数组、结构体、类等多种元素进行排序。

## 基本

### 形参表

`sort(beg,end,[cmp])`

其中`beg`和`end`分别是起始元素和结束元素的地址

```cpp
//eg.给数组排序
int a[10]={0};
for(int i=0;i<10;i++)
    cin>>a[i];
sort(a,a+10,compare);       //a是数组头地址，a+10是a[9]的地址
```

`cmp`没有的话默认升序排列（从小到大）。

如果要降序排列，需要写个cmp函数，如下：

```cpp
bool compare1(int a,int b)
{
return a>b;     //cmp为true时不交换
}
```

标准库中也有此类函数，在`<functional>`中，包括`equal_to<Type>`、`not_equal_to<Type>`、`greater<Type>`、`greater_equal<Type>`、`less<Type>`、`less_equal<Type>`等，上面写的`compare1`函数相当于`greater<int>`。

## 字符串

例子说明一切

```cpp
string hhh("jojo");
sort(hhh.begin(),hhh.end());//用迭代器，begin()表示起始地址，end()表示结束地址
```

结果：“jjoo”

## 结构体

```cpp
#include<iostream>
#include<algorithm>
using namespace std;

struct link
{
    int a,b;
};

bool cmp(link x,link y) //先比a，a一样再比b
{
    if(x.a==y.a)
        return x.b>y.b;
    return x.a>y.a;
}

int main()
{
    link x[4];
    for(int i=0;i<4;i++)
        cin>>x[i].a>>x[i].b;
    sort(x,x+4,cmp);
    for(int i=0;i<4;i++)
        cout<<x[i].a<<' '<<x[i].b<<endl;
    return 0;
 }
```