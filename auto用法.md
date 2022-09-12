# c++11 auto

## auto基本用法

```c++
auto x = 5;                 // OK: x是int类型
auto pi = new auto(1);      // OK: pi被推导为int*
const auto *v = &x, u = 6;  // OK: v是const int*类型，u是const int类型
static auto y = 0.0;        // OK: y是double类型
auto int r;                 // error: auto不再表示存储类型指示符
auto s;                     // error: auto无法推导出s的类型
```

## auto遍历

### 遍历字符串

```c++
std::string str = “hello, world”;  
for(auto ch : str) {  
     std::cout << ch << std::endl;  
}  
```

### 遍历数组

```c++
int arr[] = {1, 2, 3, 4};  
for(auto i : arr) {  
     std::cout<< i << std::endl;  
}  
```

### 遍历vector

```c++
//第一种用法
void showvec(const vector<int>& line) {
  for (auto iter = line.cbegin(); iter != line.cend(); iter++) {
    cout << (*iter) << endl;
  }
}
//第二种用法
for (auto lin : line) {
    cout << lin;
  }
```

### 遍历map

```c++
std::map<int, std::string> hash_map = {{1, “c++”}, {2, “java”}, {3, “python”}};  
for(auto it : hash_map) {  
     std::cout << it.first << “\t” << it.second << std::endl;  
}  
```

## for(auto &i:s)和for(auto i:s)

auto &i:s

```c++
#include<iostream>
#include<string>
using namespace std;

string s = "hello";
for (auto &i : s ) //i是个引用
i = toupper(i); //改变成大写，影响s的值
cout<<s<<endl; //s的值是 HELLO
```

auto i:s

```c++
#include<iostream>
#include<string>
using namespace std;

string s = "hello";
for (auto i : s ) //书上说i 是char类型，那s[n]呢？
i = toupper(i); //改变成大写，不影响s的值
cout<<s<<endl; //s的值是 hello
```

