# C++刷题总结

## [cppreference.com - C++参考手册](https://cppreference.cn/w/)

[OI Wiki](https://oi-wiki.org/)

## 一、语言基础

### 二、常用

#### 立方根

> 1. `cbrt(n)`  求解立方根
> 2. ==二分== 不断寻找 x ^ 3 = n
> 3. `pow(n, 1/3)`

#### 大小写转换

1.  > ```cpp
    > #include<cctype>
    > 
    > islower()
    > isupper()
    >    
    > ```
    >
    > ==用于检查一个字符是否为小写字母或者大侠字母，函数返回值为`bool`类型== 





2. > ```cpp
   > 
   > tolower()
   > toupper()
   >     
   > ```
   >
   > ==将大小写字母进行转换==







#### 二分查找

>  库函数只能对==**数组**==进行二分查找
>
> ```cpp
> binary_search()
> ```
>
> 用于在已排序大的序列中查找特定元素，通过二分查找来确定序列中是否存在目标元素，函数返回一个 `bool` 值
>
> 如果需要获取找到的元素的位置，可以使用
>
> `std::lower_bound`
>
> `std::upperbound`
>
> `数组`必须非降序
>
> `lower_bound(st,ed,x)`返回地址 `[st`,`ed)` ，中第一个大于等于`x` 的地址
>
> `upper_bound(st,ed,x)`返回地址 `[st`,`ed)` ，中第一个大于等于`x` 的地址





#### 排序

> `sort` 包含在头文件`algorithm` 中
>
> 用于对指定范围内的元素进行排序
>
> `sort` 使用的是快速排序或类似快速排序的改进算法
>
> ```cpp
> sort(起始地址，结束地址的下一位，*比较函数) 左闭右开区间
>     默认升序排序
> 第三个参数可以是 函数，或者 lambda表达式    
>     
> sort(v.begin(), v.end(), [](int u, int v)
> {
>     return u > v;
> });
> ```
>
> 







#### 最值查找

1.  > `min(a, b)`
    >
    > `max(a, b)`
    >
    > 比较值大小

2. > `min_element(st, ed)` 返回地址`[st, ed)` 中最小的那个值的地址(迭代器)，传入参数为地址或迭代器
   >
   > `max_element(st, ed)` 返回地址`[st, ed)` 中最大的那个值的地址(迭代器)，传入参数为地址或迭代器

3. > `nth_element(st, k, ed)` 进行部分排序，返回值为`void()`
   >
   > 传入参数为三个地址或迭代器，其中第二个参数将处于正确的位置，其他位置元素顺序任意，前面的都比他小，后面的都比他大



#### 全排列

1.    > `next_permutation`，用于生成当前序列的下一个排列。按照字典序对序列进行重新排列，如果存在下一个排列，则将当前序列更改为下一个排列，并返回`true`，如果当前序列已经是最后一个排列，则将序列更改为第一个排列，并返回`false`

2. > `prev_permutation` , 用于生成当前序列的上一个排列。按照字典序对序列进行重新排列，如果存在上一个排列，则将当前序列更改为上一个排列，并返回`true`，如果当前序列已经是第一个排列，则将序列更改为最后一个排列，并返回`false`



#### 其他库函数

1. ·`memset()`

   > 用于设置内存块值的函数，原型定义在`<cstring>`
   >
   > `void* memset(void* ptr, int value, size_t num);`

2. `swap()`

   > `swap()`， 接受两个参数，要交换值的变量的引用
   >
   > 可以用于交换任意类型的变量，包括基本类型，自定义类型

3. `reverse()`

   > `reverse()`， 用于反转容器中元素顺序的函数，定义在`<algorithm>`
   >
   > ```cpp
   > template<class BidirIt>
   >     void reverse(BidirIt first, BidirIt last);
   > ```
   >
   > 

4. `unique()`

   > `unique()` 用于去除容器中相邻重复元素的函数，定义在`<algorithm>`
   >
   > ```cpp
   > template<class ForwardIt>
   > ForwardIt unique(ForwardIt first, Forward last);
   > ```
   >
   > 



### 三、`STL`

#### 一、`vector`

> 动态数组容器，可以存储一系列相同类型的元素
>
> ### 构造：
>
> ​	`vector<类型> arr(长度，[初值])`
>
> ```cpp
> #include <vector>
> 
> // 一维
> vector<int> arr;			// 构造 int 数组
> vector<int> arr(100);		// 构造初始长度为100的 int 数组
> vector<int> arr(100, 1);	// 构造初始长度为100的 int 数组，初值为 1
> 
> // 二维
> vector<vector<int>> mat(100, vector<int> ());			// 构造初始100行，不指定列数的二维数组
> ||
> vector<vector<int>> arr(100, vector<int> ());			// 与上一行等价
>     
> vector<vector<int>> mat(100, vector<int> (666, -1));	// 构造初始100行，初始666列的二维数组，初值为 -1.
> ||
> vector<vector<int>> arr(100, vector<int> (666, -1));    // 与上一行等价
> ```
>
> 
>
> 1. 元素访问 ->` [] or at()`
> 2. 元素添加或删除
>    - `push_back()` 
>    - `pop_bavk()`
>    - `insert()`
>    - `erase()`
>    - `size()`
>    - `clear()`
>    - `empty()`
>    - `resize()`
>    - `back()`
> 3. 容器大小管理
> 4. 迭代器
>    - `begin()`
>    - `end()`
>
> 





#### 二、`stack`

> 后进先出（LIFO）的数据结构，**==不可访问内部元素==**
>
> ```cpp
> template <class T, class Container = deque<T>>
> class stack;   
> 
> ```
>
> 1. `push()`：栈顶插入元素
> 2. `pop()`：弹出栈顶元素
> 3. `top()`：返回栈顶元素
> 4. `emety()`：检查栈是否为空
> 5. `size()`：返回栈中元素的个数





#### 三、`set`



1.  `set`
    
    > 是一种容器，用于存储一组唯一的元素，并按照一定的排序规则进行排序，默认是升序排列,`元素唯一`，==确定性，互异性，无序性==，==不存在下标索引，元素只读==
    >
    > ```cpp
    > template <class Key, class Compare = less<Key>,
    > 		  class Allocator = allocator<Key>
    > class set;              
    > ```
    >
    > 1. `insert()`：插入元素
    > 2. `erase()`：移除元素
    > 3. `find()`：查找元素
    > 4. `lower_bound()`：返回第一个不小于给定值的迭代器
    > 5. `upper_bound()`：返回第一个大于给定值的迭代器
    > 6. `equal_range()`：返回一个范围，包含所有给定值的元素
    > 7. `size()`：返回元素的个数
    > 8. `emety()`：检查是否为空
    > 9. `clear`：清空集合
    > 10. `begin()`：返回指向集合起始位置的迭代器
    > 11. `end()`：返回指向集合末尾位置的迭代器
    > 12. `rbegin()`：返回指向集合末尾位置的逆向迭代器
    > 13. `rend()`：返回指向多重集合起始位置的逆向迭代器
    > 14. `swap()`：交换两个集合
    >
    >  
    >
    > **遍历：**
    >
    > ```cpp
    > for (set<int>::iterator it = st.begin();it != st.end(); ++i){
    >     cout << it << endl;
    > }
    > ```
    >
    > ```cpp
    > for (auto &ele : st){
    >     cout << ele << endl;
    > }
    > ```
    >
    > 



2. `multiset`多重集合

   > ```cpp
   > template <class Key, class Compare = less<Key>,
   > 		  class Allocator = allocator<Key>>
   > class multiset;   
   > ```
   >
   > `允许存储重复的元素`
   >
   > 
   >
   > 1. `insert()`：插入元素
   > 2. `erase()`：移除元素
   > 3. `find()`：查找元素
   > 4. `lower_bound()`：返回第一个不小于给定值的迭代器
   > 5. `upper_bound()`：返回第一个大于给定值的迭代器
   > 6. `equal_range()`：返回一个范围，包含所有给定值的元素
   > 7. `size()`：返回元素的个数
   > 8. `emety()`：检查是否为空
   > 9. `clear`：清空集合
   > 10. `begin()`：返回指向集合起始位置的迭代器
   > 11. `end()`：返回指向集合末尾位置的迭代器
   > 12. `rbegin()`：返回指向集合末尾位置的逆向迭代器
   > 13. `rend()`：返回指向多重集合起始位置的逆向迭代器
   > 14. `swap()`：交换两个集合



3. `unordered_set`无序集合

   > ```cpp
   > template <class Key, class Hash = hash<Key>,
   > 		  class KeyEqual = equal_to<Key>,
   > 		  class Allocator = allocator<Key>>
   > class unordered_set;   
   > ```
   >
   > `没有特定顺序且不稳定`
   >
   > 1. `insert()`：插入元素
   > 2. `erase()`：移除元素
   > 3. `find()`：查找元素
   > 4. `count()`:返回元素在集合中出现的次数
   > 5. `size()`：返回无序集合中元素的数量



#### 四、`queue`队列

1. `queue` 队列

   > `queue` 是一种先进先出(FIFO)的数据结构，**==不可访问内部元素==**
   >
   > ```cpp
   > template <class T,class Container = deque<T>>
   > class queue;    
   > ```
   >
   > 1. `push()` 在队尾插入元素
   > 2. `pop()` 弹出队首元素
   > 3. `front()` 返回队首元素
   > 4. `back()` 返回队尾元素
   > 5. `emrty()` 检查队列是否为空
   > 6. `size()` 返回队列中元素的个数



2. `priority_queue` 优先队列

   > `priority_queue` 中的元素是按照一定的**优先级**进行排序的，默认为按照元素值从大到小排列.**==不可访问内部元素且所有元素不可修改==**
   >
   > ```cpp
   > priority_queue<int, vector<int>, greater<int> >;	//小到大
   > priority_queue<int, vector<int>, less<int> >;		//大到小
   > ```
   >
   > 
   >
   > ```cpp
   > template <class T,class Container = vector<T>,
   > 			class Compare = less<typename> Container::value_type>>
   > class priority_queue;                
   > ```
   >
   > 1. `push()` 将元素插入到优先队列中
   > 2. `pop()` 弹出优先队列中的顶部元素
   > 3. `top()` 返回优先队列中的顶部元素
   > 4. `emety()` 检查优先队列是否为空
   > 5. `size()` 返回优先队列中元素的个数



3. `deque` 双端队列

   > `deque` 是一种容器，它允许在两端进行高效的插入和删除操作。`deqeue` 是由一系列连续的存储块（缓冲区）组成的，每个存储块都存储了多个元素
   >
   > ```cpp
   > template <class T,class Allocater = allocater<T>>
   > class deque;    
   > ```
   >
   > 1. `push_back()` 在尾部插入元素
   > 2. `push_front()` 在头部插入元素
   > 3. `pop_back()` 弹出尾部元素
   > 4. `pop_front()` 探出头部元素
   > 5. `front()` 返回头部元素
   > 6. `back()` 返回尾部元素
   > 7. `emety()` 检查双端队列是否为空
   > 8. `size()` 返回双端队列中元素的个数
   > 9. `clear()` 清空双端队列中所有元素
   > 10. `insert(pos, x)` 在指定位置插入元素
   > 11. `erase(pos)`  移除指定位置元素
   > 12. `erase(first, last)` 移除[first, last) 范围内的元素



#### 五、`pair`

1. `pair` 的定义和结构

   > `pair` 是一个模板类，用于表示一对值的组合，位于`<utility>`头文件
   >
   > ```cpp
   > template<class T1, class T2>
   > struct pair {
   >     T1 first;	// 第一个值
   >     T2 second;  // 第二个值
   >     
   >     pair();    //构造函数
   >     pair(const T1& x, const T2&y);
   >     
   >     // 比较运算符重载
   >     bool operator==(const pair& rhs) const;
   >     bool operator!=(const pair& rhs) const;
   > }    
   > ```
   >
   > 

2. `pair` 的嵌套

   > `pair` 可以进行嵌套 可以将一个 pair 对象作为另一个 pair 对象的成员

3. `pair` 自带排序规则

   > `pair` 自带的排序规则是按照`first` 成员进行升序排序，如果`first` 成员相等，则按照`second` 成员进行升序排序







#### 六、`map`

1. `map`

   > `map` 是一种关联容器，用于存储一组键值对，其中每个键都是唯一的
   >
   > `map` 容器根据键来自动进行排序，并且可以根据键来快速查找对应的值
   >
   > `map` 容器使用红黑树数据结构来实现
   >
   > ```cpp
   > template <class Key, class T, class Compare = less<Key>,
   > 			class Allocator = allocator<pair<const Key, T>>>
   > 
   > class map;                
   > ```
   >
   > 1. `insert()` 插入元素
   > 2. `erase()` 删除元素
   > 3. `find()` 查找元素
   > 4. `count()` 统计元素个数
   > 5. `size()` 返回元素个数
   > 6. `begin()` 返回指向容器起始位置的迭代器
   > 7. `end()` 返回指定容器末尾位置的迭代器
   > 8. `clear()` 清空容器
   > 9. `emety()` 判断容器是否为空
   > 10. `lower_bound()` 返回第一个不小于指定键的元素位置
   > 11. `upper_bound()` 返回指向第一个大于指定键的元素位置
   >
   >  
   >
   > ```cpp
   > for (map<int, int>::itrator it = map.begin(); it != map.end(); ++it){
   >     cout << it->first << ' ' << it->second << endl;
   > }
   > ```
   >
   > ```cpp
   > for(auto &els : map){
   >     cout << els.first << ' ' << els.second << endl;
   > }
   > ```
   >
   > 

2. `multimap`

   > 允许存储多个具有相同键的键值对
   >
   > ```cpp
   > template <class Key, class T, class Compare = less<Key>,
   > 			class Allocator = allocator<pair<const Key, T>>>
   > 
   > class multimap;  
   > ```
   >
   > 1. `insert()` 插入元素
   > 2. `erase()` 删除元素
   > 3. `find()` 查找元素
   > 4. `count()` 统计元素个数
   > 5. `size()` 返回元素个数
   > 6. `begin()` 返回指向容器起始位置的迭代器
   > 7. `end()` 返回指定容器末尾位置的迭代器
   > 8. `clear()` 清空容器
   > 9. `emety()` 判断容器是否为空

3. `unordered_map`

   > 不会根据键的顺序进行排序，而是使用**哈希函数**将键映射到存储桶中
   >
   > ```cpp
   > template <class Key, class T, class Hash = hash<Key>,
   > 			class KeyEqual = equal_to<Key>,
   > 			class Allocator = allocator<pair<const Key, T>>>
   > 
   > class unorderer_map;  
   > ```
   >
   > 1. `insert()` 插入元素
   > 2. `erase()` 删除元素
   > 3. `find()` 查找元素
   > 4. `count()` 统计元素个数
   > 5. `size()` 返回元素个数
   > 6. `clear()` 清空容器
   > 7. `emety()` 判断容器是否为空





#### 七、`list`

> `list` 是一种双向链表容器。
>
> `list` 以节点的形式存储元素，并使用指针将这些节点链接在一起，形成一个链表结构
>
> ```cpp
> template <class T, class Allocator = std::allocator<T>>
> class list;    
> ```
>
> 1. `push_back()` 将元素插入到链表的末尾
> 2. `push_front()` 将元素插入到链表开头
> 3. `pop_back()` 移除链表末尾的元素
> 4. `pop_front()` 移除链表开头的元素
> 5. `size()` 返回链表中元素个数
> 6. `emety()` 判断链表是否为空
> 7. `clear()` 清空链表所有元素
> 8. `front()` 返回链表中第一个元素的引用
> 9. `back()` 返回链表中最后一个元素的引用
> 10. `begin()` 返回指向链表第一个元素的迭代器
> 11. `end()` 返回指向链表末尾的下一个位置的迭代器
> 12. `insert()` 在指定位置之前插入一个或多个元素
> 13. `erase()` 从链表中移除指定位置的一个或多个元素



#### 八、`string`





















#### 九、迭代器















#### 十、算法

- ==算法库 Algorithm==
  - [ ] `count()`
  - [ ] `find()`
  - [ ] `fill()`
  - [x] [`swap()`](https://zh.cppreference.com/w/cpp/algorithm/swap)
  - [x] [`reverse()`](https://zh.cppreference.com/w/cpp/algorithm/reverse)
  - [ ] `shuffle()` C++11
  - [x] [`unique()`](https://zh.cppreference.com/w/cpp/algorithm/unique)
  - [x] [`sort()`](https://zh.cppreference.com/w/cpp/algorithm/sort)
  - [x] [`lower_bound()`](https://zh.cppreference.com/w/cpp/algorithm/lower_bound) / [`upper_bound()`](https://zh.cppreference.com/w/cpp/algorithm/upper_bound)
  - [x] [`max()`](https://zh.cppreference.com/w/cpp/algorithm/max) / [`min()`](https://zh.cppreference.com/w/cpp/algorithm/min)
  - [ ] `max_element()` / `min_element()`
  - [ ] `prev_permutation()` / `next_permutation()`
- ==数学函数 cmath==
  - [x] [`abs()`](https://zh.cppreference.com/w/cpp/numeric/math/fabs)
  - [x] [`exp()`](https://zh.cppreference.com/w/cpp/numeric/math/exp)
  - [x] [`log()`](https://zh.cppreference.com/w/cpp/numeric/math/log) / `log10()` / `log2()`
  - [x] [`pow()`](https://zh.cppreference.com/w/cpp/numeric/math/pow)
  - [x] [`sqrt()`](https://zh.cppreference.com/w/cpp/numeric/math/sqrt)
  - [ ] `sin()` / `cos()` / `tan()`
  - [ ] `asin()` / `acos()` / `atan()`
  - [ ] `sinh()` / `cosh()` / `tanh()`
  - [ ] `asinh()` / `acosh()` / `atanh()` C++11
  - [x] [`ceil()`](https://zh.cppreference.com/w/cpp/numeric/math/ceil) / [`floor()`](https://zh.cppreference.com/w/cpp/numeric/math/floor)
  - [x] [`round()`](https://zh.cppreference.com/w/cpp/numeric/math/round) C++11
- ==数值算法 numeric==
  - [ ] `iota()` C++11
  - [ ] `accumulate()`
  - [x] [`gcd()`](https://zh.cppreference.com/w/cpp/numeric/gcd) C++17
  - [x] [`lcm()`](https://zh.cppreference.com/w/cpp/numeric/lcm) C++17
- 伪随机数生成 random
  - [ ] `mt19937`
  - [ ] `random_device()`

##### 1. ==`swap()`==

交换两个变量的值

**用法示例**

```cpp
template< class T >
void swap( T& a, T& b );
```

```cpp
int a = 0, b = 1;
swap(a, b);
// now a = 1, b = 0

int arr[10] {0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
swap(arr[4], arr[6]);
// now arr = {0, 1, 2, 3, 6, 5, 4, 7, 8, 9}
```

**注意事项**

这个 swap 参数是引用的，不需要像 C 语言一样取地址。

##### 2. ==`sort()`==

使用快速排序给一个可迭代对象排序

**用法示例**

```cpp
template< class RandomIt, class Compare >
void sort( RandomIt first, RandomIt last, Compare comp );
```

默认排序从小到大

```cpp
vector<int> arr{1, 9, 1, 9, 8, 1, 0};
sort(arr.begin(), arr.end());
// arr = [0, 1, 1, 1, 8, 9, 9]
```

如果要从大到小，则需要传比较器进去。

```cpp
vector<int> arr{1, 9, 1, 9, 8, 1, 0};
sort(arr.begin(), arr.end(), greater<int>());
// arr = [9, 9, 8, 1, 1, 1, 0]
```

如果需要完成特殊比较，则需要手写比较器。

比较器函数返回值是 bool 类型，传参是需要比较的两个元素。记我们定义的该比较操作为 $\star$：

- 若 $a\star b$，则比较器函数应当返回 `true`
- 若 $a\not\star b$，则比较器函数应当返回 `false`

**注意：**如果 $a=b$，比较器函数必须返回 `false`

```cpp
bool cmp(pair<int, int> a, pair<int, int> b)
{
    if (a.second != b.second)
        return a.second < b.second;
    return a.first > b.first;
}

int main()
{
    vector<pair<int, int>> arr{{1, 9}, {2, 9}, {8, 1}, {0, 0}};
	sort(arr.begin(), arr.end(), cmp);
    // arr = [(0, 0), (8, 1), (2, 9), (1, 9)]
}
```

##### 3. ==`lower_bound()`== / ==`upper_bound()`==

在**已升序排序**的元素中，应用二分查找检索指定元素，返回对应元素迭代器位置。**找不到则返回尾迭代器。**

- `lower_bound()`: 寻找 $\geq x$ 的第一个元素的位置
- `upper_bound()`: 寻找 $>x$ 的第一个元素的位置

怎么找 $\leq x$ / $< x$ 的第一个元素呢？

- $>x$ 的第一个元素的前一个元素（如果有）便是 $\leq x$ 的第一个元素
- $\geq x$ 的第一个元素的前一个元素（如果有）便是 $<x$ 的第一个元素

返回的是迭代器，如何转成下标索引呢？减去头迭代器即可。

**用法示例**

```cpp
template< class ForwardIt, class T >
ForwardIt lower_bound( ForwardIt first, ForwardIt last, const T& value );
```

```cpp
vector<int> arr{0, 1, 1, 1, 8, 9, 9};
vector<int>::iterator it = lower_bound(arr.begin(), arr.end(), 7);
int idx = it - arr.begin();
// idx = 4
```

我们通常写成一行：

```cpp
vector<int> arr{0, 1, 1, 1, 8, 9, 9};
idx = lower_bound(arr.begin(), arr.end(), 7) - arr.begin(); // 4
idx = lower_bound(arr.begin(), arr.end(), 8) - arr.begin(); // 4
idx = upper_bound(arr.begin(), arr.end(), 7) - arr.begin(); // 4
idx = upper_bound(arr.begin(), arr.end(), 8) - arr.begin(); // 5
```

##### 4.==`reverse()`==

反转一个可迭代对象的元素顺序

**用法示例**

```cpp
template< class BidirIt >
void reverse( BidirIt first, BidirIt last );
```

```cpp
vector<int> arr(10);
iota(arr.begin(), arr.end(), 1);
// 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
reverse(arr.begin(), arr.end());
// 10, 9, 8, 7, 6, 5, 4, 3, 2, 1
```

##### 5. ==`max()` / `min()`==

返回最大值 / 最小值的**数值**

**用法示例**

```cpp
int mx = max(1, 2); // 2
int mn = min(1, 2); // 1
```

在 C++11 之后，可以使用列表构造语法传入一个列表，这样就能一次性给多个元素找最大值而不用套娃了：

```cpp
// Before C++11
int mx = max(max(1, 2), max(3, 4)); // 4
int mn = min(min(1, 2), min(3, 4)); // 1

// After C++11
int mx = max({1, 2, 3, 4}); // 4
int mn = min({1, 2, 3, 4}); // 1
```

##### 6. ==`unique()`==

消除数组的重复**相邻**元素，数组长度不变，但是有效数据缩短，返回的是有效数据位置的结尾迭代器。

例如：$[1,1,4,5,1,4]\to[1,4,5,1,4,\underline?]$，下划线位置为返回的迭代器指向。

```cpp
template< class ForwardIt >
ForwardIt unique( ForwardIt first, ForwardIt last );
```

**用法示例**

单独使用 unique 并不能达成去重效果，因为它只消除**相邻**的重复元素。但是如果序列有序，那么它就能去重了。

但是它去重后，序列尾部会产生一些无效数据：$[1,1,2,4,4,4,5]\to[1,2,4,5,\underline?,?,?]$，为了删掉这些无效数据，我们需要结合 erase.

最终，给 vector 去重的写法便是：

```cpp
vector<int> arr{1, 2, 1, 4, 5, 4, 4};
sort(arr.begin(), arr.end());
arr.erase(unique(arr.begin(), arr.end()), arr.end());
```

##### 7. **==数学函数==**

所有函数参数均支持 `int` / `long long` / `float` / `double` / `long double`

| 公式                    | 示例         |
| ----------------------- | ------------ |
| $f(x)=\lvert x\rvert$   | `abs(-1.0)`  |
| $f(x)=e^x$              | `exp(2)`     |
| $f(x)=\ln x$            | `log(3)`     |
| $f(x,y)=x^y$            | `pow(2, 3)`  |
| $f(x)=\sqrt x$          | `sqrt(2)`    |
| $f(x)=\lceil x\rceil$   | `ceil(2.1)`  |
| $f(x)=\lfloor x\rfloor$ | `floor(2.1)` |
| $f(x)=\left<x\right>$   | `rount(2.1)` |

**注意事项**

由于浮点误差，有些的数学函数的行为可能与预期不符，导致 WA。如果你的操作数都是整型，那么用下面的写法会更稳妥。

> 原文地址：https://codeforces.com/blog/entry/107717

- $\lfloor\frac{a}{b}\rfloor$
  - 别用：`floor(1.0 * a / b)`
  - 要用：`a / b`
- $\lceil\frac{a}{b}\rceil$
  - 别用：`ceil(1.0 * a / b)`
  - 要用：`(a + b - 1) / b`  （$\lceil\frac{a}{b}\rceil=\lfloor\frac{a+b-1}{b}\rfloor$）
- $\lfloor\sqrt a\rfloor$
  - 别用：`(int) sqrt(a)`
  - 要用：二分查找 https://io.zouht.com/7.html
- $a^b$
  - 别用：`pow(a, b)`
  - 要用：快速幂 https://io.zouht.com/18.html
- $\lfloor\log_2 a\rfloor$
  - 别用：`log2(a)`
  - 要用：`__lg` （不规范，但是这是竞赛）/ `bit_width`（C++20 可用）

##### 8. ==`gcd()`== / ==`lcm()`==

（C++17）返回最大公因数 / 最小公倍数

```cpp
int x = gcd(8, 12); // 4
int y = lcm(8, 12); // 24
```

如果不是 C++17，但是是 GNU 编译器（g++），那么可以用内置函数 `__gcd()`.

当然，`gcd` / `lcm` 函数也挺好写，直接写也行（欧几里得算法）：

```cpp
int gcd(int a, int b)
{
    if (!b)
        return a;
    return gcd(b, a % b);
}

int lcm(int a, int b)
{
    return a / gcd(a, b) * b;
}
```







- [x] 



## 二、基础算法

### 一、基础算法

#### 1、时间复杂度

> 时间复杂度是衡量算法执行时间随输入规模增长的增长率
>
> 通过分析算法中基本操作的执行次数来确定时间复杂度
>
> `尽可能使程序运算规模的数量级控制在1e8以内`

#### 2、（暴力）枚举

> 枚举算法是一种基本的算法思想，通过穷举所有可能的情况来解决问题。
>
> 它的基本思想是将问题的解空间中的每个可能的解都枚举出来，并进行验证和比较，找到满足问题的最优解或所有解

#### 3、模拟

> 模拟算法通过模拟实际情况来解决问题，一般容易理解但是实现起来较为复杂，有很多需要注意的细节，或者是一些很麻烦的东西。

#### 4、递归

> `递归是指函数直接或间接调用自身的过程`
>
> 1. 基本情况（递归终止条件/递归出口）：当满足该条件时，递归终止，避免无限递归。
> 2. 递归表达式（递归调用）：递归函数中的语句，用于解决规模较小的问题，再将子问题的答案合并成为当前问题的答案
>
> **实现过程：**
>
> 1. 将大问题分解为规模更小的子问题
> 2. 使用递归调用解决每个子问题
> 3. 通过递归终止条件来结束递归

#### 5、进制转换





> #### 任意进制转换为十进制，k 进制，$\sum\limits_{i=1}^n{x}*{k^{(n-1)}}\quad$
>
> ```cpp
> #include <bits/stdc++.h>
> using namespace std;
> using ll = long long;
> string s = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
> int main(){
>     int x; cin >> x;
>     string ss; cin >> ss;
>     ll ans = 0;
>     for(int i = 0; i < ss.size(); i++){
>         int temp;
>         if(ss[i] >= '0' && ss[i] <= '9') temp = ss[i] - '0';
>         else temp = ss[i] - 'A' + 10;
>         ans = ans * x + temp; 
>     }
>     cout << ans << endl;
>     return 0;
> }
> ```
>
> 
>
> #### 十进制转换为任意进制，$x=\sum\limits_{i=1}^{n}{a_{n}}*{k^{n}}$
>
> ```cpp
> # 十进制转任意进制
> string s = "0123456789ABCDEF";
> using ll = long long;
> ll x; cin x;
> while(x){
> a[++cnt] = x % k;
> x /= k;
> }
> reverse(a + 1, a + 1 + cnt); 
> 
> ```
>
> #### 递归：用递归算法将一个十进制整数 X（1≤X≤10 ^ 9）转换成任意进制数 M（2 ≤ M ≤ 16）。
>
> ```cpp
> #include <bits/stdc++.h>
> using namespace std;
> string s = "0123456789ABCDEF";
> 
> void f(int x, int m){
>  // 辗转相除法
>  if(x / m) f(x / m, m);
>  cout << s[x % m];           // 倒序输出
> }
> int main(){
>  long long x; cin >> x;
>  int m; cin >> m;
>  f(x, m);
>  return 0;
> }
> ```
>
> 

#### 6、前缀和

![](./Images/蓝桥前缀和1.jpg)



> `prefix` 表示前缀和，前缀和由一个用户输入的数组生成
>
> 定义一个数组`a[]（下标从 1 开始）` 
>
> $prefix[i] = \sum\limits_{j=1}^{j}{a[j]}$
>
> 
>
> `prefix有一个重要的特性，可用于快速生成 prefix`
>
> $prefix[i]=\sum\limits_{j=1}^{i-1}{a[j]}+{a[i]}=prefix{[i-1]} + {a[i]}$
>
> 
>
> `prefix 可以求数组a[]的一段区间的和`
>
> $sum(l,r)=prefix[r] - prefix[l-1]$
>
> ```cpp
> for(int i = 1; i<= n; i++){
>     prefix[i] = prefix[i - 1] + a[i];
> }
> ```
>
> 









![](./Images/蓝桥二位前缀和1.jpg)



![](./Images/蓝桥二维前缀和2.jpg)

#### 7、差分![](./Images/蓝桥差分数组1.jpg)

![](./Images/蓝桥差分数组2.jpg)



> **定义**
>
> 
>
> $diff[i]=a[i]-a[i-1]$
>
>  
>
> $\sum\limits_{j=1}^{i}{diff[j]}={a[i]}$
>
>  
>
> ==利用差分数组可以实现快速的区间修改，将区间 `[l,r]` 都加上 x==
>
> ```cpp
> diff[l] += x;
> diff[r + 1] -= x;
> ```
>
> **差分的实现**：==注意使`a[0] = 0`, `即令 diff[1] = 0` 
>
> ```cpp
> for(int i = 1; i <= n; i++){
>     diff[i] = a[i] - a[i - 1];
> }
> ```
>
> 











![](./Images/蓝桥二维差分数组1.jpg)



![](./Images/蓝桥二维差分数组2.jpg)



![](./Images/蓝桥二维差分数组3.jpg)

#### 8、离散化

> **把无限空间中有限的个体映射到有限的空间中去**，**以此提高算法的时空效率**。
>
> **离散化是一种将数组的值域压缩，从而更加关注元素的大小关系的算法**
>
> **离散化数组要求内部是==有序==（一般是去重的），可以直接通过离散化下标得到值，也可以通过值得到离散化下标（通过二分来实现）。**

#### 9、贪心

> **贪心的基本原理**： 每一步都选择==局部最优解==，而尽量不考虑对后续的影响，最终达到全局最优解。
>
> **贪心的局限性**： 贪心算法不能保证获得全局最优解，但在某些问题上具有高效性。
>
> **贪心的特征**： 贪心选择性质、最优子结构性质（==不同的操作产生的贡献相同==的特征，再次特征下每次选择代价最小的）
>
>  
>
>  
>
> **实现步骤：**
>
> 1. 确定问题的最优子结构
> 2. 构建贪心选择的策略，可能通过“分类讨论”、“最小代价”、“最大价值”等方式。==这样做一定不会是的结果变差，不存在比当前方案更好的方案==
> 3. 通过贪心选择逐步求解问题，知道得到最终解。

#### 10、双指针

> 双指针算法是一种常用的算法技巧，它通常用于在数组或字符串中进行==快速查找、匹配、排序或移动==操作
>
> 双指针一般用两个变量来表示下表（在后面都用指针来表示）
>
> 双指针算法使用两个指针在数据结构上进行迭代，并根据问题的要求移动指针
>
>  
>
> 1. 对撞指针
>
>    > 指的是两个指针`lefe、right`，分别指向有序序列的第一个和最后一个元素，然后`left` 指针不断递增，`right` 指针不断递减，直到两个指针的值相撞或错开（`l >= r `）或满足其他特殊条件。
>
> 2. 快慢指针
>
>    > 指的是两个指针从==同一侧开始遍历序列==，且移动的步长一个快一个慢。
>    >
>    > 移动快的指针称为快指针，移动慢的称为慢指针
>    >
>    > 设快指针为`right`，慢指针为`left`，这样构成了一个区间`[left,right]`
>    >
>    > 两个指针以不同速度、不同策略移动，==直到快指针移动到数组尾端或两指针相交或满足其他特殊条件==



#### 11、二分 [【二分查找】详细图解_二分法算法流程图-CSDN博客](https://blog.csdn.net/qq_45978890/article/details/116094046?ops_request_misc=%7B%22request%5Fid%22%3A%228d9f0c956ffb2e0b30ea062ca864147f%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=8d9f0c956ffb2e0b30ea062ca864147f&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-2-116094046-null-null.142^v100^pc_search_result_base4&utm_term=二分查找&spm=1018.2226.3001.4187)

![](./Images/蓝桥二分.jpg)



![](./Images/蓝桥二分答案.jpg)

> 二分法是一种高效的查找方法，它将问题的搜索范围一分为二（两边具有明显的区别）迭代的缩小搜索范围，直到找到目标或确定目标不存在
>
> 二分法适用于==有序数据集合==，并且每次迭代可以将搜索范围缩小一半  
>
> 
>
> 
>
> **解题步骤：**
>
> 1. 发现数据结构的单调性
>
> 2. 确定最大区间`[left,right]`，确保分界点一定在里面，细节：若以`right`为答案，那么答案区间在`[left+1,right]`；若以`left`为答案，那么答案在`[left,right-1]`
>
> 3. `确定 check 函数`，一般为传入 `mid（区间中某个下标）`，返回`mid` 所属区间或一个值
>
> 4. ==计算中点`mid = (left + right) / 2` ，用`check` 判断该移动哪个指针
>
> 5. 返回`left` 或者 `right`
>
> 
>
> 
>
> **常见类型：**
>
> ​	退出循环时 l 、r 相邻
>
> 1. 整数二分
>
>    ```cpp
>    // 找到升序数组 a 中的 x 第一次出现的位置
>    int l = 0, r = n;
>    // 注意判断条件，可以保证 l、 r 最终一定收敛到分界点
>    while(l + 1 != r){
>        int mid = (l + r) / 2;
>        // 如果 a 为升序，说明mid偏大，需要减小mid, 只能将r变小，即 r = mid
>        if(a[mid] >= x) r = mid;
>        else l = mid;
>    }
>    cout << r << endl;
>    ```
>
>    
>
> 2. 浮点二分
>
> 3. ==二分答案==
>
>    ```cpp
>    int l = 0, r = 1e9;
>    while(l + 1 != r){
>        int mid = (l + r) / 2;
>        if(check(mid)) l = mid;
>        else r = mid;
>    }
>    cout << l;
>    ```
>
>    
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
>  
>
> #  二分
>
>  
>
> >  写在前面：
> >
> > > （一）[二分法](https://so.csdn.net/so/search?q=二分法&spm=1001.2101.3001.7020)的思想十分容易理解，但是二分法边界处理问题大多数人都是记忆模板，忘记模板后处理边界就一团乱（👁:“我懂了”， ✋ :"你懂个🔨"）因为我此前也是记忆模板，所以现在想通过一边学习，**一边将所学记录成博客教出去（费曼学习法）**，希望以后能自己推导出边界如何处理，而**不仅仅是记忆模板**。欢迎一起交流学习，如有看法不一样之处也欢迎留言一起讨论！
> > >
> > > （二）我主要解释了二分法的左闭右闭区间，左闭右开区间两种写法，并且每个写法都举了相应的反例，范围写错的话可能会出现的错误等…
> >
> > ### 1. 简介
> >
> > 故事分享🏬：
> >
> > > 有一天小明到图书馆借了 N 本书，出图书馆的时候，警报响了，于是保安把小明拦下，要检查一下哪本书没有登记出借。小明正准备把每一本书在报警器下过一下，以找出引发警报的书，但是保安露出不屑的眼神：你连二分查找都不会吗？于是保安把书分成两堆，让第一堆过一下报警器，报警器响；于是再把这堆书分成两堆…… 最终，检测了 logN 次之后，保安成功的找到了那本引起警报的书，露出了得意和嘲讽的笑容。于是小明背着剩下的书走了。 从此，图书馆丢了 N - 1 本书。
> >
> > 保安怎么知道只有一本书📖没有登记出借，万一全部都没有登记呢？
> >
> > 这个故事其实说出了二分查找需要的条件
> >
> > - 用于查找的内容逻辑上来说是需要有序的
> > - 查找的数量只能是一个，而不是多个
> >
> > 比如在一个有序的数组并且无重复元素的数组中，例如[1, 2, 3, 4, 5, 6]，需要查找3的位置就可以使用二分查找。
> >
> > > 在二分查找中，目标元素的查找区间的定义十分重要，不同的区间的定义写法不一样
> >
> > 因为查找的区间是不断迭代的，所以确定查找的范围十分重要，主要就是左右区间的开和闭的问题，开闭不一样，对应的迭代方式也不一样，有以下两种方式：
> >
> > - 左闭右闭`[left, right]`
> > - 左闭右开`[left, right)`
> >
> > ### 2. 例子
> >
> > 这是一个使用二分查找的例题
> >
> > 题目如下：
> >
> > > 给定一个 n 个元素有序的（升序）整型数组 nums 和一个目标值 target ，写一个函数搜索 nums 中的 target，如果目标值存在返回下标，否则返回 -1。
> >
> > 示例一：
> >
> > > 输入: nums = [-1,0,3,5,9,12], target = 9
> > > 输出: 4
> > > 解释: 9 出现在 nums 中并且下标为 4
> >
> > 示例二：
> >
> > > 输入: nums = [-1,0,3,5,9,12], target = 2
> > > 输出: -1
> > > 解释: 2 不存在 nums 中因此返回 -1
> >
> > 提示：
> >
> > - 你可以假设 nums 中的所有元素是不重复的。
> > - n 将在 [1, 10000]之间。
> > - nums 的每个元素都将在 [-9999, 9999]之间。
> >
> > 出自[704. 二分查找 - 力扣（LeetCode） (leetcode-cn.com)](https://leetcode-cn.com/problems/binary-search/)
> >
> > 二分法的思想很简单，**因为整个数组是有序的**，数组默认是递增的。
> >
> > - 首先选择数组中间的数字和需要查找的目标值比较
> > - 如果相等最好，就可以直接返回答案了
> > - 如果不相等
> >   - 如果中间的数字**大于**目标值，则**中间数字向右**的**所有数字都大于目标值**，全部排除
> >   - 如果中间的数字**小于**目标值，则**中间数字向左**的**所有数字都小于目标值**，全部排除
> >
> > 二分法就是按照这种方式进行快速排除查找的
> >
> > > tips:
> > >
> > > 不用去纠结数组的长度是奇数或者偶数的时候，怎么取长度的一半，以下说明，可以跳过。
> >
> > **当数组的长度为奇数的时候**：
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/1448715c0b4e877c582e72df18bfa9ed.png)
> >
> > 是奇数的情况很简单，指向中间的数字很容易理解，如果需要查找的数字为29
> >
> > 因为29大于中间的数字大于11，所以左边的所有数字全部排除
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/6bbf1fdbd6ce915514ffb3101e75381a.png)
> >
> > **当数组的长度为偶数的时候**：
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/59949bb50515b0684d3fa4f37f3a7ef1.png)
> >
> > 这个时候中间的数字两边的数字数量就不一样了（刚开始学习二分法的时候我经常纠结这个问题，和另外一个长度除2得到的是最中间的数吗的问题，我相信不止我一个人纠结过……但其实这是同一个问题，每次长度除2，如果长度为奇数，得到的中间的数字两边数字数量相同，如果长度为偶数就为上图中间的数字两边的相差为 1）
> >
> > **但是千万不要一直纠结中间的数字两边的数字数量不一样这个问题**，因为：
> >
> > - 两边数量不一样是一定会出现的情况
> > - 但是这种情况并不影响我们对中间数字和目标数字大小关系的判断
> >   - 只要中间数字大于目标数字，就排除右边的
> >   - 只要中间数字小于目标数字，就排除左边的
> >
> > **所以数组长度是偶数还是奇数这个真的不重要，不影响怎么排除的问题**，无非是多排除一个数字或者少排除一个数字
> >
> > - **真正影响的是中间那个数字到底该不该加入下一次的查找中，也就是边界问题**
> >
> > ### 3. 第一种写法（左闭右闭）
> >
> > **二分法最重要的两个点：**
> >
> > - while循环中 left 和 right 的关系，到底是 left <= right 还是 left < right
> > - 迭代过程中 middle 和 right 的关系，到底是 right = middle - 1 还是 right = middle
> >
> > #### 3.1 正向写法（正确演示）
> >
> > 第一种写法：每次查找的区间在`[left, right]`（左闭右闭区间），根据查找区间的定义（左闭右闭区间），就决定了后续的代码应该怎么写才能对。因为定义 target 在`[left, right]`区间，所以有如下两点：
> >
> > - 循环条件要使用`while(left <= right)`，因为当`(left == right)`这种情况发生的时候，得到的结果是有意义的
> > - `if(nums[middle] > target)` ， right 要赋值为 middle - 1， 因为当前的 nums[middle] 一定不是 target ，需要把这个 middle 位置上面的数字丢弃，那么接下来需要查找范围就是`[left, middle - 1]`
> >
> > 代码如下：
> >
> > ```c
> > int search(int nums[], int size, int target) //nums是数组，size是数组的大小，target是需要查找的值
> > {
> >     int left = 0;
> >     int right = size - 1;	// 定义了target在左闭右闭的区间内，[left, right]
> >     while (left <= right) {	//当left == right时，区间[left, right]仍然有效
> >         int middle = left + ((right - left) / 2);//等同于 (left + right) / 2，防止溢出
> >         if (nums[middle] > target) {
> >             right = middle - 1;	//target在左区间，所以[left, middle - 1]
> >         } else if (nums[middle] < target) {
> >             left = middle + 1;	//target在右区间，所以[middle + 1, right]
> >         } else {	//既不在左边，也不在右边，那就是找到答案了
> >             return middle;
> >         }
> >     }
> >     //没有找到目标值
> >     return -1;
> > }
> > ```
> >
> > 下面图解算法的实现过程，建议将代码复制到一个文本编辑器中，边看代码边看图。或者我直接准备了图片，保存下来打开看就好了。
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/4c0f010c989e1de7194b3e0bc8d4714e.png)
> >
> > 首先看一个数组，需要对这个数组进行操作。需要对33进行查找的操作，那么**target 的值就是33**
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/3aeb51055fcae5e7169a2d5ef2cc7c0d.png)
> >
> > - 首先，对 left 的值和 right 的值进行初始化，然后计算 middle 的值
> >   - `left = 0, right = size - 1`
> >   - `middle = (left + (right - left) / 2 )`
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/f52c4afee7247ec6787f9bd254d37e2d.png)
> >
> > - 比较 nums[middle] 的值和 target 的值大小关系
> >   - `if (nums[middle] > target)`，代表middle向右所有的数字大于`target`
> >   - `if (nums[middle] < target)`，代表middle向左所有的数字小于`target`
> >   - 既不大于也不小于就是找到了相等的值
> > - `nums[middle] = 13 < target = 33，left = middle + 1`
> > - 见下图：
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/5dce2e5e1fe48c4676fd06aeb442f059.png)
> >
> > - 循环条件为 `while (left <= right)`
> > - 此时，`left = 6 <= right = 11`，则继续进行循环
> > - 当前，`middle = left + ((right - left) / 2)`，计算出 middle 的值
> >   ![img](https://i-blog.csdnimg.cn/blog_migrate/ca0d491584e7da812444b414145732d6.png)
> > - 计算出 middle 的值后，比较 nums[middle] 和 target 的值，发现：
> >   - nums[middle] = 33 == target = 33，**找到目标**
> >
> > #### 3.2 反向写法(错误演示)
> >
> > 对应第一种正向的写法，我们把循环条件修改看看会发生什么事
> >
> > - 原查找区间 [left, right]
> > - 原循环条件是 while (left <= right)
> >
> > 修改后题目对应的条件：
> >
> > - 查找区间不变，仍然是[left, right]
> > - 查找数字为27 (target = 27)
> > - **循环条件修改为while (left < right)**
> >
> > 代码：
> >
> > ```c
> > int search(int nums[], int size, int target) 
> > {
> >     int left = 0;
> >     int right = size - 1;	
> >     while (left < right) {	//left <= right 修改为 left < right,其他不变
> >         int middle = left + ((right - left) / 2);
> >         if (nums[middle] > target) {
> >             right = middle - 1;
> >         } else if (nums[middle] < target) {
> >             left = middle + 1;
> >         } else {	
> >             return middle;
> >         }
> >     }
> >     //没有找到目标值
> >     return -1;
> > }
> > ```
> >
> > 代码图片，边看模拟过程边看代码哦！
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/34ca6f9ecfa84ccfa689d2a0f4f96e73.png)
> >
> > 好了，现在开始用图片模拟过程
> >
> > - 初始化一个数组，计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/00f5bdade75247bf76ac6203099ef3a1.png)
> >
> > - 根据计算的 middle 值确定 nums[middle]
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/1cc4720bf67670f2cea3f6c37e27ef10.png)
> >
> > - 因为nums[middle] = 13 < target = 27，所以left = middle + 1
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/ca227ef728f4ba77de5b439f1e31a8b5.png)
> >
> > - 继续计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/d67ae380f9f0bfc62d1475c946748179.png)
> >
> > - 因为 nums[middle] = 33 > target = 27，所以 right = middle - 1
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/47dd92a2950ae70f7db6465457c0243e.png)
> >
> > - 接着计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/86e053fce967d03b6f817c645087ebfb.png)
> >
> > - 因为 nums[middle] = 22 < target = 27，此时 left = middle + 1，此时 left = right，而循环条件为while (left < right)，所以还未找到27 的情况下算法就跳出了循环，返回 -1
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/7f9fdc0d5fa511dd2a3c109a7cb77c8f.png)
> >
> > ------
> >
> > ### 4. 第二种写法（左闭右开）
> >
> > #### 4.1 正向写法（正确演示）
> >
> > 第二种写法：每次查找的区间在 [left, right)，（左闭右开区间）， 根据区间的定义，条件控制应该如下：
> >
> > - 循环条件使用while (left < right)
> > - if (nums[middle] > target)， right = middle，因为当前的 nums[middle] 是大于 target 的，不符合条件,不能取到 middle，并且区间的定义是 [left, right)，刚好区间上的定义就取不到 right, 所以 right 赋值为 middle。
> >
> > 代码如下：
> >
> > ```c
> > int search(int nums[], int size, int target)
> > {
> > 	int left = 0;
> > 	int right = size; //定义target在左闭右开的区间里，即[left, right)
> > 	while (left < right) {	//因为left = right的时候，在[left, right)区间上无意义
> > 		int middle = left + ((right - left) / 2);
> > 		if (nums[middle] > target) {
> > 			right = middle; //target 在左区间，在[left, middle)中 
> > 		} else if (nums[middle] < target) {
> > 			left = middle + 1;
> > 		} else {
> > 			return middle;
> > 		}
> > 	} 
> >     // 没找到就返回-1
> > 	return -1;
> > }
> > ```
> >
> > 代码图片：保存下来边看代码边看图片演示过程
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/ce55af53ec94b5eaeaba969b865cc900.png)
> >
> > - **需要查找的值为3**
> >
> > 第一步是初始化 left 和 right 的值，然后计算 middle 的值
> >
> > - left = 0, right = size
> > - **循环条件while (left < right)**
> >
> > 因为是左闭右开区间，所以数组定义如下：
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/23f3d4b022baa66812dbb89cd36a58c8.png)
> >
> > - 计算 middle 的值，
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/49a2d06d25a27d952149d9d9b469ead4.png)
> >
> > - 比较 nums[middle] 和 target 的大小：因为 nums[middle] = 22 > target = 3
> > - 所以 right = middle
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/bd274ca03b15b9f8a5883b90316e9289.png)
> >
> > - 符合循环的条件，接着计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/7f9bb0f483419ff8cece9f6a4e83e2d3.png)
> >
> > - 比较 nums[middle] 和 target 的大小：因为 nums[middle] = 9 > target = 3
> > - 所以 right = middle
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/b3dc4ad1d6df091be3e77f139b8b26b2.png)
> >
> > - 符合循环的条件，继续计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/575b09e57b3b82ac3b12948258d61fde.png)
> >
> > - 比较 nums[middle] 和 target 的大小关系：因为nums[middle] = 0 < target = 3
> > - 所以 left = middle + 1
> >
> > ![在这里插入图片描述](https://i-blog.csdnimg.cn/blog_migrate/edd2d7f3d6d1c6034511aeac0cc4a4a8.png#pic_center)
> >
> > - 符合循环条件，接着计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/2e7d319c09b55a91e91453ae1fe1d6cd.png)
> >
> > - 比较 nums[middle] 和 target 的关系：nums[middle] = 3 == target = 3
> > - 成功找到 target
> >
> > #### 4.2 反向写法（错误演示）
> >
> > 对应第二种正确的写法，照样把循环条件修改，看会发生什么事
> >
> > 正确的写法中条件为：
> >
> > - 查找原区间 [left, right)
> > - 循环条件为 while (left < right)
> >
> > 修改后题目对应的条件：
> >
> > - 查找区间不变，仍然是 [left, right)
> > - 循环条件修改为：while (left <= right)
> > - 查找的数字为26（数组中不存在这个数字！！！）
> >
> > 代码：
> >
> > ```c
> > int search(int nums[], int size, int target)
> > {
> > 	int left = 0;
> > 	int right = size; 
> > 	while (left <= right) {	//条件left < right 修改为 left <= right
> > 		int middle = left + ((right - left) / 2);
> > 		if (nums[middle] > target) {
> > 			right = middle; 
> > 		} else if (nums[middle] < target) {
> > 			left = middle + 1;
> > 		} else {
> > 			return middle;
> > 		}
> > 	} 
> >     // 没找到就返回-1
> > 	return -1;
> > }
> > ```
> >
> > 代码图片：（记得边看边保存图片代码边看图片演示哦！）
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/2937ab2354d3c3bf7fd9e408fe4f5a8f.png)
> >
> > 以下是演示全过程：
> >
> > - 同样，开始初始化一个数组
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/094965cc218dcc38cf6118caf092324e.png)
> >
> > - 先计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/116491e9c3cce77a2508c3778b5bca81.png)
> >
> > - 判断 nums[middle] 和 target 的大小关系：nums[middle] = 22 < target = 26
> > - left = middle + 1 （其实这里nums[left] 已经等于27，26不可能找到，接下去就看算法是否能够知道数组中不存在26并且返回-1 了）
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/b7e26335e848084ed1355ddfe3ad5920.png)
> >
> > - 符合循环条件，计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/7e510db4cd754272acb8f0ddf6b38c89.png)
> >
> > - 判断 nums[middle] 和 target 的大小关系：nums[middle] = 57 > target = 26
> > - right = middle
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/bee9b2c5a189955c6928ce74f126b33e.png)
> >
> > - 满足循环条件，接着计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/7f93f3a137f4fddb4e97026a40a0fa96.png)
> >
> > - 比较 nums[middle] 和 target 的大小关系：nums[middle] = 33 > target = 26
> > - right = middle
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/183d4f6cc4913f87f1ed97b2858114c1.png)
> >
> > - 符合循环条件，继续计算 middle 的值
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/300494b3797ee7181434c92d37a8005b.png)
> >
> > - 比较 nums[middle] 和 target 大小关系，因为 nums[middle] = 27 > target = 26，
> > - 所以 right = middle，自此，left 和 right 相遇，但是循环条件被我们修改成 while (left <= right) 会接着做循环
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/60d4d188644bca444b89ff7a5369c043.png)
> >
> > - 接下来就是死循环
> > - 因为 middle = left + ((right - left) / 2)，当 left = right 的时候，middle 的值不会继续改变
> > - middle 不继续改变，由于right = middle，right 也不会改变，所以三个数字自此开始不会继续改变
> > - 循环条件 while (left <= right) 却仍然满足，不会跳出循环
> > - 死循环……
> >
> > ### 5. 总结
> >
> > 二分法最重要的两个点，就是循环条件和后续的区间赋值问题
> >
> > ![img](https://i-blog.csdnimg.cn/blog_migrate/dde6e66fd6822ad0fbe1e92c2688eb9e.png)
> >
> > 因为两者是相互联系，相互影响的，所以就需要两者统一，如果两者不统一，就会出现问题
> >
> > 所以循环条件和赋值问题必须统一，也就是循环不变量。
> >
> > 

#### 12、倍增

#### 13、构造

> 观察问题的结构和规律，找到一种通用的方法或模式，使得在问题规模较大时依然能够高效地得到答案
>
> 1. 观察问题规模的增长
> 2. 推广规律
> 3. ==注意特殊情况==
>
> > 1. 分析题目要求和条件
> > 2. 尝试特里和极端情况
> > 3. 寻找模式和规律
> > 4. 尝试逆向构造
> > 5. 使用数学归纳法
> > 6. 灵活运用所学知识
> > 7. 反复实践总结
> > 8. 保持耐心和信心

#### 14、位运算

>  位运算是一种对==二进制数的位进行操作的运算方式==
>
> 他直接对二进制数的每一位进行逻辑操作，而不考虑整个数数值大小，一般情况位运算中每一位都相互独立，各自运算得出结果（左右移除外）
>
> ==位运算只能应用于整数，且一般为非负整数==
>
>  
>
> - #### 按位与AND `&`
>
>   > 只有当两个都为 1 时，结果位才为 1 ，否则为零
>
> - #### 按位或OR `|`
>
>   > 只要两个位中有一个为 1 ，结果就为 1 ，否则为 0
>
> - #### 按位异或 XOR `^`
>
>   > 当两个位不同时，结果位为 1 ，否则为 0 。
>
> - #### 按位取反 `~`
>
>   > 对操作数的每一位进行取反操作，0 变为 1 ，1 变为 0
>
> - #### 按位左移 `<<`
>
>   > 将操作数的每一位都向左移动指定的位数，相当于对原数进行乘以 2的幂次方
>
> - #### 按位右移 `>>`
>
>   > 将操作数的每一位都向右移动指定的位数，相当于对原数进行除以 2的幂次方
>
>  
>
> > - #### 判断奇偶性，即二进制最后一位
> >   
> >   - `x & 1`
> >   
> > - #### 求二进制的第 `i `位
> >   
> >   - `(x >> i) & 1`
> >   
> > - #### 将二进制的第 `i `位变为 1
> >   
> >   - `x | (1 << i)`
> >   
> > - #### 将二进制的第 ` i ` 位 变 0
> >   
> >   - `x & ~(1 << i)`
> >   
> > - #### 判断一个数字是否为 2 的幂次方
> >
> >   - `x & (x - 1)`  如果x为2的幂次方，则x的二进制位只有一个1，x-1 就有很多1 且与 x 没有交集，两者与运算一定为0
> >
> > - #### 获取 x 的最低位的 `1`
> >   
> >   - `Lowbit(x) = x & (-x)`







#### 15、[高精度](https://blog.csdn.net/wmy0217_/article/details/104269844)



> 高精度算法，属于处理大数字的数学计算方法。在一般的科学计算中，会经常算到小数点后几百位或者更多，当然也可能是几千亿几百亿的大数字。一般这类数字我们统称为`高精度数`，高精度算法是用计算机对于超[大数据](https://so.csdn.net/so/search?q=大数据&spm=1001.2101.3001.7020)的一种模拟加，减，乘，除，乘方，阶乘，开方等运算。



> ```cpp
> #include <bits/stdc++.h>
> using namespace std;
> using ll = long long;
> 
> // https://www.luogu.com.cn/problem/P1303
> // 高精度乘法
> int main(){
>     char a[100010], b[100010];
>     int a1[100010], b1[100010], c[100010];
>     cin >> a >> b;                        // 输入两个字符串
>     int lena = strlen(a), lenb = strlen(b);                     // 字符串长度
> 
>     // 字符串转数字,因为要计算乘法，所以模拟数学列竖式乘法
>     // 先把字符串转成数字数组，要从右至左计算每一位乘法，所以转换成数字时要倒序转化
>     for(int i = 1; i <= lena; i++) a1[i] = a[lena-i] - '0';     
>     for(int i = 1; i <= lenb; i++) b1[i] = b[lenb-i] - '0';
> 
>     // 高精度乘法，用数组模拟竖式乘法
>     for(int i = 1; i <= lena; i++){
>         for(int j = 1; j <= lenb; j++){
>             c[i + j - 1] += a1[i] * b1[j];                      // 注意乘积是在哪一位上乘的，要进位
>         }
>     }
>     for(int i = 1; i <= lena + lenb; i++){
>         if(c[i] > 9){                                     // 进位，得出乘积的数字大于 9 时，要进位
>             c[i+1] += c[i] / 10;                            // 进位
>             c[i] %= 10;                                    // 取余更新当前位
>         }
>     }
>     int lenc = lena + lenb;                                 // 结果的长度
>     while(lenc > 1 && c[lenc] == 0) lenc--;                 // 去除前导 0
>     for(int i = lenc; i >= 1; i--){                          // 输出结果，倒序输出
>         cout << c[i];
>     }
>     return 0;
> }
> 
> ```
>
>  
>
>  
>
>  
>
>  
>
> ```cpp
> #include <bits/stdc++.h>
> using namespace std;
> using ll = long long;
> 
> // 高精度加法
> // https://www.luogu.com.cn/problem/P1601
> int main(){
>     char a[100005], b[100005];
>     int a1[100005], b1[100005], c1[100005];
>     cin >> a >> b;
>     int lena = strlen(a), lenb = strlen(b);
>     for(int i = 1; i <= lena; i++) a1[i] = a[lena - i] - '0';
>     for(int i = 1; i <= lenb; i++) b1[i] = b[lenb - i] - '0';
>     for(int i = 1; i <= max(lena, lenb) + 1; i++){
>         c1[i] += a1[i] + b1[i];
>         c1[i + 1] += c1[i] / 10;
>         c1[i] %= 10;
>     }
>     // if(c1[max(lena, lenb) + 1]) cout << c1[max(lena, lenb) + 1];
>     for(int i = max(lena, lenb); i >= 1; i--){
>         cout << c1[i];
>     }
>     return 0;
> }
> ```
>
> 













### 二、排序

#### 1、冒泡排序

#### 2、选择排序

#### 3、插入排序

#### 4、快速排序

#### 5、归并排序

#### 6、桶排序

## 三、搜索

### 一、DFS

#### 一、DFS基础

> ==深度优先搜索算法（Depth First Search，简称DFS）：一种用于遍历或搜索树或图的算法。 沿着树的深度遍历树的节点，尽可能深的搜索树的分支。当节点v的所在边都己被探寻过或者在搜寻时结点不满足条件，搜索将回溯到发现节点v的那条边的起始节点。整个进程反复进行直到所有节点都被访问为止。属于盲目搜索,最糟糕的情况算法时间复杂度为O(!n)。==
>
>  
>
> 
>
> > ==在深度优先搜索中，对于最新发现的顶点，如果它还有以此为顶点而未探测到的边，就沿此边继续探测下去，当顶点v的所有边都已被探寻过后，搜索将回溯到发现顶点v有起始点的那些边。这一过程一直进行到已发现从源顶点可达的所有顶点为止。如果还存在未被发现的顶点，则选择其中一个作为源顶点，并重复上述过程。整个过程反复进行，直到所有的顶点都被发现时为止。==
>
>  
>
>  
>
>  ```cpp
>  vector<int> a; // 记录每次排列 
>  vector<int> book; //标记是否被访问 
>  
>  void DFS(int cur, int k, vector<int>& nums){
>      if(cur == k){ //k个数已经选完，可以进行输出等相关操作 
>          for(int i = 0; i < cur; i++){
>  			printf("%d ", a[i]);
>  		} 
>          return ;
>      }
>      for(int i = 0; i < k; i++){ //遍历 n个数，并从中选择k个数 
>          if(book[nums[i]] == 0){ //若没有被访问
>              a.push_back(nums[i]); //选定本输，并加入数组 
>              book[nums[i]] = 1; //标记已被访问 
>              DFS(cur + 1, n, nums); //递归，cur+1 
>              book[nums[i]] = 0; //释放，标记为没被访问，方便下次引用 
>              a.pop_back(); //弹出刚刚标记为未访问的数
>          }
>      }
>  }
>  
>  ```
>
> 

#### 二、DFS回溯

```cpp
int a[N];
bool vis[N];

void dfs(int dep){
    if(dep == n + 1){
        for(int i = 1; i <= n; ++i) cout << a[i] << ' ';
        cout << '\n';
        return;
    }
    for(int i = 1; i <= n; ++i){
        // 排除不合法的路径
        if(vis[i]) continue;
        
        // 修改状态
        vis[i] = true;
        a[dep] = i;
        
        // 下一层
        dfs(dep + 1);
        
        // 恢复现场
        vis[i] = false;
        
        // a[dep] = 0 可以省略
    }
}
```



#### 三、DFS剪枝

> 其实就是将搜索过程中一些不必要的部分直接剔除掉，因为搜索的过程构成了一棵树，剔除不必要的部分就像是在树上将树枝剪掉，故名剪枝
>
> 剪枝是回溯法的一种重要优化手段，方法往往先写一个暴力搜索，然后找到特殊的数学关系或逻辑关系，通过他们的约束让==搜索树尽可能浅而小==，达到降低时间复杂度的目的

#### 四、记忆化搜索

> 将搜索过程中会重复计算且结果相同的部分保存下来，作为一个状态，下次访问到这个状态时直接将这个子搜索的结果返回，不需要重新算一遍
>
> 通常会使用数组或 map 来进行记忆化，==下标一般和 dfs 的参数表对应==
>
> ==注意使用记忆化需要保证重读计算的结果是相同的==，否则可能产生数据失真

### 二、BFS

> ==就是从根结点位置开始遍历，遍历结束后依次遍历与根节点相邻的点，相邻点遍历结束后继续遍历上轮第一个遍历结点的相邻的未遍历的点，直至所有的点都遍历结束。==

## 四、动态规划

### 一、动态规划基础

> 将一种复杂问题分解为很多重叠的子问题，并通过子问题的解得到整个问题的解
>
>  
>
> 1. 状态
> 2. 状态转移
> 3. 最终状态







> ## 动态规划原理
>
> 能用动态规划解决的问题，需要满足三个条件：最优子结构，无后效性和子问题重叠。
>
> ### 最优子结构
>
> 具有最优子结构也可能是适合用贪心的方法求解。
>
> 注意要确保我们考察了最优解中用到的所有子问题。
>
> 1. 证明问题最优解的第一个组成部分是做出一个选择；
> 2. 对于一个给定问题，在其可能的第一步选择中，假定你已经知道哪种选择才会得到最优解。你现在并不关心这种选择具体是如何得到的，只是假定已经知道了这种选择；
> 3. 给定可获得的最优解的选择后，确定这次选择会产生哪些子问题，以及如何最好地刻画子问题空间；
> 4. 证明作为构成原问题最优解的组成部分，每个子问题的解就是它本身的最优解。方法是反证法，考虑加入某个子问题的解不是其自身的最优解，那么就可以从原问题的解中用该子问题的最优解替换掉当前的非最优解，从而得到原问题的一个更优的解，从而与原问题最优解的假设矛盾。
>
> 要保持子问题空间尽量简单，只在必要时扩展。
>
> 最优子结构的不同体现在两个方面：
>
> 1. 原问题的最优解中涉及多少个子问题；
> 2. 确定最优解使用哪些子问题时，需要考察多少种选择。
>
> 子问题图中每个定点对应一个子问题，而需要考察的选择对应关联至子问题顶点的边。
>
> ### 无后效性
>
> 已经求解的子问题，不会再受到后续决策的影响。
>
> ### 子问题重叠
>
> 如果有大量的重叠子问题，我们可以用空间将这些子问题的解存储下来，避免重复求解相同的子问题，从而提升效率。
>
> ### 基本思路
>
> 对于一个能用动态规划解决的问题，一般采用如下思路解决：
>
> 1. 将原问题划分为若干 **阶段**，每个阶段对应若干个子问题，提取这些子问题的特征（称之为 **状态**）；
> 2. 寻找每一个状态的可能 **决策**，或者说是各状态间的相互转移方式（用数学的语言描述就是 **状态转移方程**）。
> 3. 按顺序求解每一个阶段的问题。

#### 1、线性DP

#### 2、二维DP



> 二维 dp 就是指 dp 数组的维度为二维的 dp，用于描述 dp 状态的变量不止一个
>
>  
>
> [1.数字三角形 - 蓝桥云课](https://www.lanqiao.cn/problems/505/learning/?page=1&first_category_id=1&problem_id=505)
>
> > ```cpp
> > #include <bits/stdc++.h>
> > using namespace std;
> > const int N = 105;
> > int a[N][N], dp[N][N][N];
> > 
> > int main(){
> >     int n; cin >> n;
> >     for(int i = 1; i <= n; i++){
> >         for(int j = 1; j <= i; j++){
> >             cin >> a[i][j];
> >         }
> >     }
> >     // dp[i][j][k] 表示从该点（i， j）出发，一共进行了 k 次右移（自然有 n - i - k 次左移）
> >     // dp[i][j][k] = max(dp[i+1][j][k], dp[i + 1][j+1][k - 1]) + a[i][j]
> >     // 即，如果从 (i, j) 出发，一共进行了 k 次右移，那么可以选择右移还是左移，
> >     // 右移的话，则 dp[i+1][j][k] 就是从 (i+1, j) 出发的最优解，左移的话，则 dp[i+1][j+1][k-1] 就是从 (i+1, j+1) 出发的最优解。
> >     // 所以 dp[i][j][k] 就是从 (i, j) 出发，一共进行了 k 次右移的最优解。
> >     // 最后根据总移动次数 n - 1 奇偶性，来决定输出哪个值。分类讨论
> >     for(int i = n; i >= 1; i--){
> >         for(int j = 1; j <= i; j++){
> >             for(int k = 0; k <= n - i; k++){
> >                 if(k >= 1) dp[i][j][k] = max(dp[i+1][j][k], dp[i + 1][j+1][k - 1]) + a[i][j];
> >                 else dp[i][j][k] = dp[i+1][j][k] + a[i][j];
> >             }
> >         }
> >     }
> >     if(n & 1) cout << dp[1][1][(n - 1) / 2];
> >     else cout << max(dp[1][1][(n - 1) / 2], dp[1][1][n - 1 - (n - 1) / 2]);
> >     return 0;
> > }
> > ```
> >
> > 

#### 3、LIS 最长上升子序列

![](./Images/LIS.jpg)

>  $LIS$
>
>  子序列是指一个序列中，按照原顺序选出若干个不一定连续的元素所组成的序列
>
>   
>
>  > ==dp[i] 表示 1~i 序列中以 a[i] 结尾的最长上升子序列的长==
>  >
>  > - ```cpp
>  >   if(a[i] > a[j]){
>  >       dp[i] = max(dp[j] + 1)
>  >   }
>  >   ```
>  >
>  > 



#### 4、LCS 最长公共子序列

![](./Images/蓝桥最长公共子序列.jpg)

>  
> 
>  $LCS(Longest Common Subsequence )最长公共子序列$
> 
> 

### 二、背包问题

#### 1、0-1背包

![](./Images/蓝桥0-1背包.jpg)

> ```python
> # dp[i][j] 表示选择第 i 个物品，容量为 j
> # 状态转移方程为
> 
> n, V = map(int, input().split())		# 读入物品数量和背包容量
> dp = [[0] * (V + 1) for _ in range(n + 1)]
> for i in range(1, n + 1):				# 选择第 i 个物品
> w, v = map(int, input().split())	# 读入物品体积和价值
> for j in range(V + 1):				
>   if j < w:					
>       # 若当前背包容量小于物品体积，从前一个物品，容量为 j 转移
>       dp[i][j] = dp[i - 1][j]
>   else:
>       # 否则，当前储存值为不选、选当前物品的最大价值
>       # 不选：dp[i - 1][j]
>       # 选：dp[i - 1][j - w] + v
>       dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - w] + v)
> print(dp[n][V])            
> ```
>
> 



![](./Images/蓝桥0-1背包滚动数组优化.jpg)

> ```python
> n, V = map(int, input().split())
> dp = [0] * (V + 1)
> for i in range(1, n + 1):
> w, v = map(int, input().split())
> # 必须从大到小
> for j in range(V, w - 1, -1):
>   dp[j] = max(dp[j], dp[j - w] + v)
> print(dp[V])        
> ```
>
> 

#### 2、完全背包

![](./Images/蓝桥完全背包.jpg)





![](./Images/蓝桥完全背包2.jpg)

> ```python 
> n, V = map(int, input().split())		# 读入物品数量和背包总量
> dp = [[0] * (V + 1) for _ in range(n)]
> for i in range(1, n + 1):
> w, v = map(int, input().split())	# 读入每一个物体的体积和价值
> for j in range(V + 1):
>   if j < w:
>       dp[i][j] = dp[i - 1][j]
>   else:
>       dp[i][j] = max(dp[i - 1][j], dp[i][j - w] + v)
> print(dp[n][V])            
> ```
>
> 



![](./Images/蓝桥完全背包优化.jpg)

> ```python
> n, V = map(int, input().split())
> dp = [0] * (V + 1)
> for i in range(1, n + 1):
> w, v = map(int, input().split())
> for j in range(w, V + 1):
>   dp[j] = max(dp[j], dp[j - w] + v)
> print(dp[V])       
> ```
>
> 



#### 3、多重背包

![](./Images/蓝桥多重背包1.jpg)

> ```python
> n, V = map(int, input().split())
> dp = [[0] * (V + 1) for _ in range(n)]
> for i in range(1, n + 1):
> w, v, s = map(int, input().split())
> for j in range(V + 1):
>   for k in range(min(s, j // w) + 1):
>       dp[i][j] = max(dp[i][j], dp[i - 1][j - k * w] + k * v)
> print(dp[n][V])            
> ```
>
> 



#### 4、单调队列多重背包

#### 5、二维费用背包&分组背包

### 三、树形DP

[P2014 CTSC1997\] 选课 - 洛谷 | 计算机科学教育新生态 (luogu.com.cn)](https://www.luogu.com.cn/problem/P2014)

#### 1、自上而下树型DP

#### 2、自下而上树型DP

#### 3、路径相关树型DP

#### 4、换根DP



### 四、区间DP

![](./Images/蓝桥区间dp1.jpg)

[1.石子合并 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/1233/learning/?page=1&first_category_id=1&problem_id=1233)

> ```python
> n = int(input())        
> li = [0] + list(map(int, input().split()))
> dp = [[float('inf')] * (n + 1) for _ in range(n + 1)]       # dp[i][j] 表示合并 i ~ j 堆石子的最小花费
> for i in range(1, n + 1):                                   # 前缀和
> li[i] += li[i - 1]
> dp[i][i] = 0                                            # 只有一堆的石子不需要合并，花费为0
> for l in range(2, n + 1):                                   # 枚举区间长度
> for i in range(1, n - l + 2):                           # 枚举区间左端点
>   j = i + l - 1                                       # 区间右端点
>   for k in range(i, j):                               # 选择 i ~ j 区间中某一值进行合并
>       dp[i][j] = min(dp[i][j], dp[i][k] + dp[k + 1][j] + li[j] - li[i - 1])
> print(dp[1][n])
> ```
>
> 
>
> 

### 五、状压DP

[1.糖果 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/186/learning/?page=1&first_category_id=1&name=糖果)

### 六、数位DP

### 七、期望DP







## 五、字符串

### 一、KMP&字符串哈希

###### ==KMP==

![](./Images/蓝桥KMP算法1.jpg)



![](./Images/蓝桥KMP算法2.jpg)



![](./Images/蓝桥KMP算法3.jpg)



###### ==字符串哈希==

![](./Images/蓝桥字符串哈希1.jpg)





![](./Images/蓝桥字符串哈希2.jpg)

### 二、Manacher

### 三、01tire









## 六、数学

### 一、线性代数&矩阵运算&数论

#### 1、矩阵乘法

#### 2、整除&同余&GCD&LCM

##### 1、整除

$$
a对b向下取整： a//b\\
a对b向上取整：(a+b-1)//b；(a-1)//b+1\\
$$



##### 2、同余

> $如果 a≡bmod   c*a*≡*b*mod *c* ,则 a×bmod  c=((amod  c)×(bmod  c))mod   c*a*×*b*mod*c*=((*a*mod*c*)×(*b*mod*c*))mod *c*$



##### 3、GCD 最大公约数

>  `gcd(a, b)` = `gcd(b, a % b)`





##### 4、LCM 最小公倍数

> `lcm(a, b)` = `a * b // gcd(a, b)`

#### 3、高斯消元

#### 4、行列式

#### 5、素数朴素判定&埃氏筛法

##### 素数

>  ```python
>  def is_prime(x):
>  if x <= 1:
>     return False
>  for i in range(2, int(x ** 0.5) + 1):
>     if x % i == 0:
>         return False
>  return True
>  ```
>
>  



##### 埃氏筛

![](./Images/蓝桥质数筛选-埃式筛.jpg)

> ```python
> def get_prinme(x):
> # vis表示是否被标记
> vis = [0] * (x + 1)
> # prime 存储所有素数
> prime = []
> 从 2-x 遍历所有数字，找到第一个未标记的数字，即为素数
> for i in range(2, x + 1):
> 	if vis[i] == 0:
>  		prime.append(i)
>      # 将这个素数的所有倍数标记
>   	for j in range(i + i, x + 1, i):
>           vis[j] = 1
> return prime
> ```
>
> 

#### 6、唯一分解定理

$唯一分解定理：即算术基本定理，对任意一个大于等于1的整数N，其要么为质数，要么可以分解为有限个质数的乘积$



![](./Images/蓝桥唯一分解定理.jpg)



![](./Images/蓝桥扩展欧几里得算法1.jpg)



![](./Images/蓝桥扩展欧几里得算法2.jpg)

> ```python
> # 求解 ax + by = gcd(a, b) 的一组解
> # 返回g, x, y
> def exgcd(a, b):
> # 递归出口
> if b == 0:
>   return a, 1, 0
> g, x2, y2 = exgcd(b, a % b)
> x1, y1 = y2, x2 - (a // b) * y2
> return g, x1, y1
> 
> def func(a, b, m):
> g, x1, y1 = exgcd(a, b)
> # m 必须是gcd(a, b) 的倍数才有解
> if m % g != 0:
>   return None, None, None
> x0, y0 = x1 * m // g, y1 * m // g
> return g, x0, y0
> ```
>
> 



###### 欧拉函数

![](./Images/蓝桥欧拉函数1.jpg)



![](./Images/蓝桥欧拉函数2.jpg)



![](./Images/蓝桥欧拉函数3.jpg)



###### 欧拉定理



![](./Images/蓝桥欧拉定理1.jpg)



![](./Images/蓝桥欧拉定理2.jpg)

[蓝桥1151](https://www.lanqiao,cn/problems//1155/learning/)

![](./Images/蓝桥1155.jpg)







#### 7、快速幂

1. ```cpp
    long long int quik_power(int base, int power)
    {
        long long int result = 1;   //用于存储项累乘与返回最终结果，由于要存储累乘所以要初始化为1
        while (power > 0)           //指数大于0说明指数的二进制位并没有被左移舍弃完毕
        {
            if (power & 1)          //指数的当前计算二进制位也就是最末尾的位是非零位也就是1的时候
                                    //例如1001的当前计算位就是1， 100*1* 星号中的1就是当前计算使用的位
                result *= base;     //累乘当前项并存储
            base *= base;           //计算下一个项，例如当前是n^2的话计算下一项n^2的值
                                    //n^4 = n^2 * n^2;
            power >>= 1;            //指数位右移，为下一次运算做准备
                                    //一次的右移将舍弃一个位例如1011(2)一次左移后变成101(2)
        }
        return result;              //返回最终结果
    }
    
    ```



2. ```cpp
   long long int quik_power(int base, int power)
   {
   	long long int result = 1;
   	while (power > 0)           //指数大于0进行指数折半，底数变其平方的操作
   	{
   		if (power % 2 == 1)     //指数为奇数
   			result *= base;     //分离出当前项并累乘后保存
   		power /= 2;        	    //指数折半
   		base *= base;           //底数变其平方
   	}
   	return result;              //返回最终结果
   }
   
   ```

3. 



#### 8、费马小定理&逆元

##### 费马小定理

![](./Images/蓝桥费马小定理1.jpg)



##### 逆元

![](./Images/蓝桥逆元1.jpg)



![](./Images/蓝桥逆元2.jpg)

> ```python
> # 求解 ax + by = gcd(a, b) 的一组解
> # 返回g, x, y
> def exgcd(a, b):
> # 递归出口
> if b == 0:
>   return a, 1, 0
> g, x2, y2 = exgcd(b, a % b)
> x1, y1 = y2, x2 - (a // b) * y2
> return g, x1, y1
> 
> def func(a, b, m):
> g, x1, y1 = exgcd(a, b)
> # m 必须是gcd(a, b) 的倍数才有解
> if m % g != 0:
>   return None, None, None
> x0, y0 = x1 * m // g, y1 * m // g
> return g, x0, y0
> 
> def Inv(a, n):
> g, x, y = func(a, n, 1)
> if x is None:
>   return None
> else:
>   return (x % n + n) % n
> ```
>
> 



#### 9、素数筛

##### 欧拉筛

![](./Images/蓝桥欧拉筛.jpg)



#### 10、裴蜀定理

#### 11、欧拉函数&欧拉降幂

### 二、组合数学

#### 一、计数原理

#### 二、排列组合





## 七、基础数据结构

### 一、基础数据结构

#### 1、链表

#### 2、队列

#### 3、栈

#### 4、堆

#### 5、ST表

#### 6、并查集

![](./Images/蓝桥基础数据结构并查集1.jpg)

#### 7、可撤销并查集

#### 8、带权并查集

### 二、基础的树上问题

#### 1、树的基本概念

#### 2、树的遍历

#### 3、树的直径与重心

#### 4、LCA

#### 5、树上差分

#### 6、DFS序

#### 7、树链刨分

### 三、树型数据结构

#### 1、树状数组基础

#### 2、二维树状数组

#### 3、树状数组上二分

#### 4、线段树--动态开点

#### 5、线段树--标记永久化

#### 6、线段树维护矩阵

#### 7、线段树维护哈希

#### 8、可持久化线段树

#### 9、扫描线二维树点

#### 10、平衡树--splay

#### 11、平衡树--FHQ_Treap



### 四、单调数据结构

#### 单调栈

### 五、分块

#### 1、分块基础

#### 2、普通莫队







## 八、图论

### 一、图的基础

#### 1、图的基本概念

![](./Images/蓝桥图的基本概念.jpg)



![](./Images/蓝桥图的基本概念2.jpg)



![](./Images/蓝桥图的基本概念3.jpg)



![](./Images/蓝桥图的存储方式1.jpg)



![](./Images/蓝桥图的存储方式2.jpg)



#### 2、DFS

![](./Images/蓝桥图论dfs遍历.jpg)

#### 3、BFS

![](./Images/蓝桥图论BFS遍历.jpg)

### 二、拓扑排序

#### 基础拓扑排序

![](./Images/蓝桥BFS实现拓扑排序.jpg)

### 三、最短路

#### 1、Floyd

#### 2、Dijkstra

#### 3、Johnson

### 四、生成树

#### 1、Kruskal

#### 2、Prim





## 九、计算几何

### 一、计算机和基础

### 二、二维计算机和基础

### 三、点积和叉积

### 四、点和线的关系

### 五、任意多边形的面积



