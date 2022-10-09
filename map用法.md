# map用法

C++ 中 map 提供的是一种键值对容器，里面的数据都是成对出现的，每一对中的第一个值称之为关键字(key)，每个关键字只能在 map 中出现一次；第二个称之为该关键字的对应值。

## 头文件

```c++
#include<map>
```

## map的构造

**map 对象是一个模版类，需要关键字和存储对象两个模版参数**

```
std::map<int , std::string> person;
```

**对模版进行类型定义使其使用方便**

```c++
typedef std::map<int , std::string> MAP_INI_STRING;
MAP_INI_STRING person;
```

## map插入数据

1. **insert 函数插入 pair 数据**

   ```c++
   std::map < int , std::string > mapPerson;
   mapPerson.insert(pair < int,string > (1,"Jim"));
   ```

2. **insert 函数插入 value_type 数据**

   ```c++
   mapPerson.insert(std::map < int, std::string > ::value_type (2, "Tom"));
   ```

3. **用数组方式插入数据**

   ```c++
   mapPerson[3] = "Jerry";
   ```

## map遍历

1. 迭代器

   ```c++
   std::map < int ,std::string > ::iterator it;
   std::map < int ,std::string > ::iterator itEnd;
   it = mapPerson.begin();
   itEnd = mapPerson.end();
   while (it != itEnd) {
   	cout<<it->first<<' '<<it->second<<endl;  
   	it++;
   }
   ```

2. auto

   ```c++
   for(auto it : mapperson){
   	cout << it.first <<" "<< it.second <<endl;
   }
   ```

## map函数

| name         | usage                                                       |
| ------------ | ----------------------------------------------------------- |
| begin()      | 返回头部的迭代器                                            |
| end()        | 返回尾部的迭代器                                            |
| count( ... ) | 返回指定元素出现的次数（0或1），用于判断map中是否含有某元素 |
| find( ... )  | 查找一个元素，如果找到返回该元素的迭代器，否则返回end()     |
| size()       | 返回map中元素的个数                                         |
| clear()      | 删除map中的所有元素                                         |
| rbegin()     | 返回一个指向map尾部的逆向迭代器                             |
| empty()      | map为空返回ture                                             |
| erase()      | 删除指向某个元素的迭代器，并返回指向下一个元素的迭代器      |

