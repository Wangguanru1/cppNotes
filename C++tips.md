# C++tips

## 2022-10-17

__builtin_popcount( num ) : 用于返回一个32位无符号数num中有多少位为1

## 2022-10-21

1. 关于string下标的地址

```c++
int main(){
    string str="abcde";
    cout<<&str[1];
}
//输出为bcde,而不是b
```

## 2022-10-22

1. 获得string的子串

```c++
string str(“helloworld”);
string strSub = str.substr(0, 5);
//strsub="hello"
```

**string substr(size_type _Off = 0,size_type _Count = npos) const;**
_Off：所需的子字符串的起始位置。字符串中第一个字符的索引为 0,默认值为0。
_Count：复制的字符数目。 返回值：一个子字符串，从其指定的位置开始。

2. 关于memset()与sizeof()

   - **sizeof()**

     返回一个对象或者一个类型所占内存的字节数

     ```c++
     int a=10;
     cout<<sizeof(a);//输出为4
     int b[]={1,2,3}
     cout<<sizeof(b);//输出为12
     cout<<sizeof(int);//输出为4
     char[] c="hello";
     cout<<sizeof(c)//输出为6
     ```

   - **memset()**

     **void *memset(void *_Dst, int _Val, size_t _Size)**

     把一整块内存区域全部填充为某个特定的值，填充的时候是一个字节一个字节进行填充的

     > 可以用memset给一个数组初始化为0、-1或一个很大的数，但是不要用memset函数来赋具体的值

     ```c++
     int a=0;
     memset(&a,1,sizeof(a));
     cout<<a;//输出为16843009
     ```

     ![img](https://img-blog.csdnimg.cn/20181029092700447.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L21lbG9keV8xMDE2,size_27,color_FFFFFF,t_70)

     

## 2022-10-29

- GCC编译器下基本数据类型大小

  | 数据类型  | 32bits（字节） | 64bits（字节） |
  | --------- | -------------- | -------------- |
  | char      | 1              | 1              |
  | short     | 2              | 2              |
  | int       | 4              | 4              |
  | long      | 4              | 8              |
  | long long | 8              | 8              |
  | char*     | 4              | 8              |
  | float     | 4              | 4              |
  | double    | 8              | 8              |

  
