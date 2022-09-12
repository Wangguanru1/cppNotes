# vector用法

## vector初始化

```c++
(1) vector<int> a(10); //定义了10个整型元素的向量（尖括号中为元素类型名，它可以是任何合法的数据类型），但没有给出初值，其值是不确定的。
(2) vector<int> a(10,1); //定义了10个整型元素的向量,且给出每个元素的初值为1
(3) vector<int> a(b); //用b向量来创建a向量，整体复制性赋值
(4) vector<int> a(b.begin(),b.begin+3); //定义了a值为b中第0个到第2个（共3个）元素
(5) int b[7]={1,2,3,4,5,9,8};
    vector<int> a(b,b+7); //从数组中获得初值
```

## vector函数

```c++
(1) a.begin()//返回向量头指针，指向第一个元素
    vector<int>a={1,0};
    vector<int>::iterator iter=a.begin();
    cout<<*iter;//输出1
(2) a.front()//返回a第一个元素的引用
    vector<int>a={1,0};
    cout<<a.front();
(3) a.end()//返回向量尾指针，指向向量最后一个元素的下一个位置
(4) a.back()//返回a的最后一个元素的引用
(5) a.assign(b.begin(), b.begin()+3); //b为向量，将b的0~2个元素构成的向量赋给a
(6) a.assign(4,2); //是a只含4个元素，且每个元素为2
(7) a.clear(); //清空a中的元素
(8) a.empty(); //判断a是否为空，空则返回ture,不空则返回false
(9) a.pop_back(); //删除a向量的最后一个元素
(10) a.erase(a.begin()+1,a.begin()+3); //删除a中第1个（从第0个算起）到第2个元素，也就是说删除的元素从a.begin()+1算起（包括它）一直到a.begin()+3（不包括它）
(11) a.push_back(5); //在a的最后一个向量后插入一个元素，其值为5,效果等于emplace_back()
(12) a.insert(a.begin()+1,5); //在a的第1个元素（从第0个算起）的位置插入数值5，如a为1,2,3,4，插入元素后为1,5,2,3,4
```

### 使用方法

#### insert()

```c++
    std::vector<int> demo{1,2};
    //第一种格式用法
    demo.insert(demo.begin() + 1, 3);//{1,3,2}
 
    //第二种格式用法
    demo.insert(demo.end(), 2, 5);//{1,3,2,5,5}
 
    //第三种格式用法
    std::array<int,3>test{ 7,8,9 };
    demo.insert(demo.end(), test.begin(), test.end());//{1,3,2,5,5,7,8,9}
 
    //第四种格式用法
    demo.insert(demo.end(), { 10,11 });//{1,3,2,5,5,7,8,9,10,11}
```

####  erase()

    vector<int>demo{ 1,2,3,4,5 };
    auto iter = demo.erase(demo.begin() + 1);//删除元素 2
    //输出 dmeo 容器新的size
    cout << "size is :" << demo.size() << endl;
    //输出 demo 容器新的容量
    cout << "capacity is :" << demo.capacity() << endl;
    for (int i = 0; i < demo.size(); i++) {
        cout << demo[i] << " ";

运行结果：

```c++
size is :4
capacity is :5
1 3 4 5
3
```

## vector算法

```
#include<algorithm>//包含头文件

(1) sort(a.begin(),a.end()); //对a中的从a.begin()（包括它）到a.end()（不包括它）的元素进行从小到大排列
(2) reverse(a.begin(),a.end()); //对a中的从a.begin()（包括它）到a.end()（不包括它）的元素倒置，但不排列，如a中元素为1,3,2,4,倒置后为4,2,3,1
(3) copy(a.begin(),a.end(),b.begin()+1); //把a中的从a.begin()（包括它）到a.end()（不包括它）的元素复制到b中，从b.begin()+1的位置（包括它）开        始复制，覆盖掉原有元素
(4) find(a.begin(),a.end(),10); //在a中的从a.begin()（包括它）到a.end()（不包括它）的元素中查找10，若存在返回其在向量中的位置
```