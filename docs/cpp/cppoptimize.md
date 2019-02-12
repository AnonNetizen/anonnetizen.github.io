# C++优化

## 输入输出

printf/scanf快于cout/cin，具体原因百度

不过后者可以通过在main开始时加下面两行代码实现优化，优化后效率和前者差不多。

```cpp
ios_base::sync_with_stdio(false);
cin.tie(0);
cout.tie(0);
```

## 位运算

参考-> [位运算](/.../other/bitwise)