# C++代码风格

## 命名

C++命名遵循驼峰法则

## using namespace std

此语句有一定风险，可能会导致命名冲突，如STD里有`search()`函数。

可以通过把STD要用的东西分别写出来的方法，显示声明，降低风险

```cpp
eg.
using std::cerr;
using std::cin;
using std::clock;
using std::clog;
using std::cout;
using std::ios_base;
using std::max;
using std::memset;
using std::min;
using std::sort;
using std::sqrt;
using std::stable_sort;
using std::string;
using std::vector;
...
```