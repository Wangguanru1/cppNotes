# C++STL queue,stack,set

## stack

###  构造

1. 构建一个空栈

   ```c++
   stack<int> stk; //默认以deque为底层容器
   ```

2. 栈不能直接初始化，可以用另一个容器来初始化

   ```c++
   int main()
   {
       deque<int> mydeck (3,100);        //创建一个deque含3个100
       list<int> mylist (2,200);         //创建一个list含2个200
   
       stack<int> first;                 //创建一个空的堆栈
       stack<int> second (mydeck);       //用mydeck的拷贝作为堆栈的初始值
       //第二个参数模板默认即为 deque，因此可以不写。
   
       stack<int,list<int>> third; //空堆栈，列表作为底层容器,<type,list<type>>
       stack<int,list<int>> fourth (mylist); //用mylist的拷贝作为堆栈的初始值
   
       cout << "size of first: " << first.size() << endl;
       cout << "size of second: " << second.size() << endl;
       cout << "size of third: " << third.size() << endl;
       cout << "size of fourth: " << fourth.size() << endl;
       return 0;
   }
   ```

   输出

   ```c++
   size of first: 0
   size of second: 3
   size of third: 0
   size of fourth: 2
   ```

### 函数

| name        | use                          |
| ----------- | ---------------------------- |
| empty()     | 判断栈是否为空，为空返回true |
| top()       | 返回栈顶元素                 |
| push( ... ) | 将一个元素压入栈             |
| pop()       | 将栈顶元素出栈               |
| size()      | 返回栈中元素的个数           |

## queue

### 构造

1. 构造一个空队列

   ```c++
   queue<int> que; //默认以deque为底层容器
   ```

   > stack可以将vector作为底容器，但queue不可以，因为vector不提供pop_front()的方法

2. 复制构造函数

   ```c++
   deque<int> d1 = {1,2,3,4,5};
   queue<int, deque<int>> q6(d1);
   
   std::queue<std::string> words;
   std::queue<std::string> copy_words {words}; // A duplicate of words
   ```

### 函数

| name        | use                            |
| ----------- | ------------------------------ |
| empty()     | 判断队列是否为空，为空返回true |
| front()     | 返回队头元素（出口）           |
| back()      | 返回队尾元素（进口）           |
| push( ... ) | 将一个元素入队                 |
| pop()       | 将队头元素出队                 |
| size()      | 返回队列中元素的数目           |

### 优先队列priority_queue

#### 构造

1. 默认构造（以vector为底层容器，以less\<T>为比较函数）

   ```c++
   priority_queue<int> q;
   ```

2. 常用构造函数

   ```c++
   priority_queue <node> q;
   //node是一个结构体
   //结构体里重载了‘<’小于符号
   priority_queue <int,vector<int>,greater<int> > q;
   //不需要#include<vector>头文件
   //注意后面两个“>”不要写在一起，“>>”是右移运算符
   priority_queue <int,vector<int>,less<int> >q;
   ```

   > less<T>: 值越大越先出队(大根堆)
   >
   > greater<T>: 值越小越先出队(小根堆)

#### 函数

| name        | use                    |
| ----------- | ---------------------- |
| empty()     | 判断优先队列是否为空   |
| size()      | 返回优先队列元素的个数 |
| top()       | 获取队首元素           |
| push( ... ) | 将一个元素入队         |
| pop()       | 将队首元素出队         |

#### 用例

```c++
#include<cstdio>
#include<queue>
using namespace std;
priority_queue <int> q;
int main()
{
	q.push(10),q.push(8),q.push(12),q.push(14),q.push(6);
	while(!q.empty())
		printf("%d ",q.top()),q.pop();
}
```

输出: `14 12 10 8 6`

## set

### 关于set

set作为一个容器也是用来存储同一数据类型的数据类型，并且能从一个数据集合中取出数据，在set中每个元素的值都唯一，而且系统能根据元素的值自动进行排序。set中数元素的值不能直接被改变。

### 构造

1. 默认构造,创造一个空的set,默认为less\<T>规则

   ```c++
   std::set<std::string> myset;
   ```

2. 在创建set的过程中，同时对其进行初始化

   ```c++
   std::set<std::string> myset{"http://c.biancheng.net/java/",
                               "http://c.biancheng.net/stl/",
                               "http://c.biancheng.net/python/"};
   ```

3. 复制构造函数

   ```c++
   std::set<std::string> copyset(myset);
   //等同于
   //std::set<std::string> copyset = myset;
   ```

4. 用其他容器的部分元素来初始化set

   ```c++
   std::set<std::string> myset{ "http://c.biancheng.net/java/",
                       "http://c.biancheng.net/stl/",
                       "http://c.biancheng.net/python/" };
   std::set<std::string> copyset(++myset.begin(), myset.end());
   //copyset保存的结果为{"http://c.biancheng.net/stl/","http://c.biancheng.net/python/"}
   ```

### 函数

| name          | use                                      |
| ------------- | ---------------------------------------- |
| empty()       | 如果集合为空，返回true                   |
| size()        | 返回集合中元素的个数                     |
| count()       | 返回某个值的元素的个数，0或1             |
| clear()       | 清空set中的所有元素                      |
| find()        | 返回一个指向被查找元素的迭代器           |
| insert( ... ) | 向集合中添加一个元素                     |
| erase( ... )  | 删除集合中的一个元素                     |
| begin()       | 返回指向第一个元素的迭代器               |
| end()         | 返回指向最后一个元素的下一个位置的迭代器 |

