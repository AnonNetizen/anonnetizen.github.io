# KMP算法

issue:init()

KMP算法是一种线性时间的字符串匹配算法，相对朴素字符串匹配算法来说效率大大提高。它充分利用匹配后的已知信息，使匹配一次后能跳过尽可能多的字符继续搜索。

## 预处理

为了知道能跳过几个字符，需要先对模式（待搜索的字符，亦即pattern）进行预处理。要建立一个前缀表，用数组来存。它表示模式的各个前缀的真前缀和真后缀最大有多少个字符匹配。下面是预处理的代码：

```cpp
void Init()
{
    Next[1] = 0;                        //小写next和STD冲突
    int k = 0;

    for (int i = 1; i < palen; i++)     //为什么这么些就可以还没搞明白
    {
        while ((k > 0) and (pattern[k] != pattern[i]))
        {
            k = Next[k];
        }

        if (pattern[k] == pattern[i])
        {
            k++;
        }

        Next[i] = k;
    }
}
```

## 搜索

预处理完成后剩下的当然就是搜索了。搜索的代码只要在朴素算法基础上做些修改即可。以下是搜索函数的实现：

```cpp
void See()                                      //取名search()会和STD有冲突
{
    for (int i = 0; i < txtlen - palen + 1; i++)
    {
        p = 0;                                  //用来记录本次搜索中匹配的字符数

        for (int j = 0; j < palen; j++)
        {
            if (text[i + j] == pattern[j])
            {
                p++;
            }
            else
            {
                i = i + j - Next[j + 1]-1;
                break;
            }
        }

        if (p == palen)                         //完全匹配
        {
            cout << i + 1 << endl;              //输出
            i = i + palen - Next[palen]-1;
        }
    }
}
```

## 完整代码

以下是程序完整的代码：

```cpp
#include<iostream>
#include<string>
using namespace std;
string text, pattern;
int Next[10005];
int res[10005];
int palen, txtlen;
int p;
void Init()
{
    Next[1] = 0;
    int k = 0;

    for (int i = 1; i < palen; i++)
    {
        while ((k > 0) and (pattern[k] != pattern[i]))
        {
            k = Next[k];
        }

        if (pattern[k] == pattern[i])
        {
            k++;
        }

        Next[i] = k;
    }
}

void See()
{
    for (int i = 0; i < txtlen - palen + 1; i++)
    {
        p = 0;

        for (int j = 0; j < palen; j++)
        {
            if (text[i + j] == pattern[j])
            {
                p++;
            }
            else
            {
                i = i + j - Next[j + 1] - 1;
                break;
            }
        }

        if (p == palen)
        {
            cout << i + 1 << endl;          
            i = i + palen - Next[palen] - 1;
        }
    }
}

int main()
{
    cin >> text >> pattern;
    palen = pattern.size();
    txtlen = text.size();
    Init();
    See();
    return 0;
}
```