# 蓝桥省赛无忧班Python

## 1、进制转换

> ```python
> # 任意进制转十进制
> def K_to_Ten(k, num):
>     ans = 0
>     for i in num:
>         ans = ans * k + char_to_int[i]
>     return ans
> 
> 
> int_to_char = "0123456789ABCDEF"
> char_to_int = {}
> for idx, char in enumerate(int_to_char):
>     char_to_int[char] = idx
> print(char_to_int)
> k, n = map(int, input().split())
> n = str(n)
> print(K_to_Ten(k, n))
> ```
>
> ```python
> # 十进制转任意进制
> def Ten_to_K(k, num):
>     ans = ""
>     while num != 0:
>         ans += int_to_char[num % k]
>         num //= k
>     return ans[::-1]
> int_to_char = "0123456789ABCDEF"
> k, n = map(int, input().split())
> print(Ten_to_K(k, n))
> ```

## 2、快速幂

> ```python
> def Ten_to_two(num, base = 2):	# 将指数转换为二进制
>     char = "0123456789"
>     ans = ""
>     while num != 0:
>         ans += char[num % base]
>         num //= base
>     return int(ans[::-1])
> def quick_power(base, power):	# 快速幂函数
>     result = 1
>     while power > 0:		# 只需计算二进制中不为零的数字，从右往左计算
>         if power & 1:		# 每次判断后底数变为原来一倍
>             result *= base
>         base *= base
>         power >>= 1
>     return result
> base, power = map(int, input().split())
> power = Ten_to_two(power)
> print(quick_power(base, power))
> ```

## 3、位运算

> - 判断奇偶性，即二进制最后一位
>   - `x & 1`
> - 求二进制的第 i 位
>   - `(x >> i) & 1`
> - 将二进制的第 i 位变为 1
>   - `x | (1 << i)`
> - 将二进制的第 i 位 变 0
>   - `x & ~(1 << i)`
> - 获取 x 的最低位的 1
>   - `Lowbit(x) = x & (-x)`

## 4、前缀和

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥前缀和1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二位前缀和1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二维前缀和2.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥差分数组1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥差分数组2.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二维差分数组1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二维差分数组2.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二维差分数组3.jpg)

## 5、二分

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二分.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥二分答案.jpg)

> ```python
> def check(x)
> 	pass		# 判断取值是否合法
> 
> left, right, ans = 初始化
> while left <= right:
>     mid = left + (right - left) / 2
>     if check(mid):
>         ans = mid
>         left = mid + 1
>     else::
>         right = mid - 1
> print(ans)       
> ```
>
> 



## 6、最长上升子序列==LIS==

> ```python
> # dp[i] 表示以第 i 个数结尾的最长上升子序列的长度
> # 如果一个上升子序列的最大值小于在他后面的数，则这个数和原上升子序列可以组成新的上升子序列
> # 每一个数都可以当作是长度为 1 的最长上升子序列
> 
> 
> n = int(input())
> li = list(map(int, input().split()))
> dp = [1] * (n)
> for i in range(n):
> 	for j in range(i):
>    		if li[j] < li[i]:
>             dp[i] = max(dp[j] + 1, dp[i])
>    print(max(dp))
> ```
> 
>

## 7、最长公共子序列==LCS==

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥最长公共子序列.jpg)

> ```python
> # dp[i][j] 表示字符 s1 前 i 个与字符 s2 前 j 个的最长公共子序列的长度
> n, m = map(int, input().split())		# 读入两个字符串长度
> s1 = [0] + list(map(int, input().split()))			# 使下标从 0 开始
> s2 = [0] + list(map(int, input().split()))
> dp = [[0] * (m + 1) for _ in range(n + 1)]
> for i in range(1, n + 1):
>     for j in range(1, m + 1):
>         if s1[i] == s2[j]:
>             dp[i][j] = dp[i - 1][j - 1] + 1
>         else:
>             dp[i][j] = max(dp[i - 1][j], dp[i][j - 1]) + 1
> print(dp[n][m]) 
> 
> # 输出最长公共子序列
> ans = []
> x, y = n, m
> while x != 0 and y != 0:
>     if dp[x][y] == dp[x - 1][y]:
>         x -= 1
>     elif dp[x][y] == dp[x][y - 1]:
>         y -= 1
>     else:
>         ans.append(s1[x])
>         x -= 1
>         y -= 1
> print(*ans[::-1])        
>        
> ```
>
> 



## 8、背包问题

### 8-1、0-1 背包

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥0-1背包.jpg)

> ```python
> # dp[i][j] 表示选择第 i 个物品，容量为 j
> # 状态转移方程为
> 
> n, V = map(int, input().split())		# 读入物品数量和背包容量
> dp = [[0] * (V + 1) for _ in range(n + 1)]
> for i in range(1, n + 1):				# 选择第 i 个物品
>     w, v = map(int, input().split())	# 读入物品体积和价值
>     for j in range(V + 1):				
>         if j < w:					
>             # 若当前背包容量小于物品体积，从前一个物品，容量为 j 转移
>             dp[i][j] = dp[i - 1][j]
>         else:
>             # 否则，当前储存值为不选、选当前物品的最大价值
>             # 不选：dp[i - 1][j]
>             # 选：dp[i - 1][j - w] + v
>             dp[i][j] = max(dp[i - 1][j], dp[i - 1][j - w] + v)
> print(dp[n][V])            
> ```
>
> 

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥0-1背包滚动数组优化.jpg)

> ```python
> n, V = map(int, input().split())
> dp = [0] * (V + 1)
> for i in range(1, n + 1):
>     w, v = map(int, input().split())
>     # 必须从大到小
>     for j in range(V, w - 1, -1):
>         dp[j] = max(dp[j], dp[j - w] + v)
> print(dp[V])        
> ```
>
> 

### 8-2、完全背包

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥完全背包.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥完全背包2.jpg)

> ```python 
> n, V = map(int, input().split())		# 读入物品数量和背包总量
> dp = [[0] * (V + 1) for _ in range(n)]
> for i in range(1, n + 1):
>     w, v = map(int, input().split())	# 读入每一个物体的体积和价值
>     for j in range(V + 1):
>         if j < w:
>             dp[i][j] = dp[i - 1][j]
>         else:
>             dp[i][j] = max(dp[i - 1][j], dp[i][j - w] + v)
> print(dp[n][V])            
> ```
>
> 

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥完全背包优化.jpg)

> ```python
> n, V = map(int, input().split())
> dp = [0] * (V + 1)
> for i in range(1, n + 1):
>     w, v = map(int, input().split())
>     for j in range(w, V + 1):
>         dp[j] = max(dp[j], dp[j - w] + v)
> print(dp[V])       
> ```
>
> 

### 8-3、多重背包

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥多重背包1.jpg)

> ```python
> n, V = map(int, input().split())
> dp = [[0] * (V + 1) for _ in range(n)]
> for i in range(1, n + 1):
>     w, v, s = map(int, input().split())
>     for j in range(V + 1):
>         for k in range(min(s, j // w) + 1):
>             dp[i][j] = max(dp[i][j], dp[i - 1][j - k * w] + k * v)
> print(dp[n][V])            
> ```
>
> 

## 9、树形DP

[P2014 CTSC1997\] 选课 - 洛谷 | 计算机科学教育新生态 (luogu.com.cn)](https://www.luogu.com.cn/problem/P2014)



## 10、区间DP

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥区间dp1.jpg)

[1.石子合并 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/1233/learning/?page=1&first_category_id=1&problem_id=1233)

> ```python
> n = int(input())        
> li = [0] + list(map(int, input().split()))
> dp = [[float('inf')] * (n + 1) for _ in range(n + 1)]       # dp[i][j] 表示合并 i ~ j 堆石子的最小花费
> for i in range(1, n + 1):                                   # 前缀和
>     li[i] += li[i - 1]
>     dp[i][i] = 0                                            # 只有一堆的石子不需要合并，花费为0
> for l in range(2, n + 1):                                   # 枚举区间长度
>     for i in range(1, n - l + 2):                           # 枚举区间左端点
>         j = i + l - 1                                       # 区间右端点
>         for k in range(i, j):                               # 选择 i ~ j 区间中某一值进行合并
>             dp[i][j] = min(dp[i][j], dp[i][k] + dp[k + 1][j] + li[j] - li[i - 1])
> print(dp[1][n])
> ```
>
> 
>
> 

## 11、状压DP

[1.糖果 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/186/learning/?page=1&first_category_id=1&name=糖果)



## 12、数位DP





## 13、期望DP





## 14、数论

### 14-1 整除
$$
a对b向下取整： a//b\\
a对b向上取整：(a+b-1)//b；(a-1)//b+1\\
$$

### 14-2 ==GCD==最大公约数

> `gcd(a, b)` = `gcd(b, a % b)`

### 14-3 ==LCM==最小公倍数

> `lcm(a, b)` = `a * b // gcd(a, b)`

### 14-4 素数

> ```python
> def is_prime(x):
>     if x <= 1:
>         return False
>     for i in range(2, int(x ** 0.5) + 1):
>         if x % i == 0:
>             return False
>     return True
> ```
>
> 

#### 埃式筛

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥质数筛选-埃式筛.jpg)

> ```python
> def get_prinme(x):
>     # vis表示是否被标记
>     vis = [0] * (x + 1)
>     # prime 存储所有素数
>     prime = []
>     从 2-x 遍历所有数字，找到第一个未标记的数字，即为素数
>     for i in range(2, x + 1):
>     	if vis[i] == 0:
>        		prime.append(i)
>            # 将这个素数的所有倍数标记
>         	for j in range(i + i, x + 1, i):
>                 vis[j] = 1
>     return prime
> ```
>
> 

#### 唯一分解定理

$唯一分解定理：即算术基本定理，对任意一个大于等于1的整数N，其要么为质数，要么可以分解为有限个质数的乘积$

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥唯一分解定理.jpg)

#### 扩展欧几里得算法

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥扩展欧几里得算法1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥扩展欧几里得算法2.jpg)

> ```python
> # 求解 ax + by = gcd(a, b) 的一组解
> # 返回g, x, y
> def exgcd(a, b):
>     # 递归出口
>     if b == 0:
>         return a, 1, 0
>     g, x2, y2 = exgcd(b, a % b)
>     x1, y1 = y2, x2 - (a // b) * y2
>     return g, x1, y1
>    
> def func(a, b, m):
>     g, x1, y1 = exgcd(a, b)
>     # m 必须是gcd(a, b) 的倍数才有解
>     if m % g != 0:
>         return None, None, None
>     x0, y0 = x1 * m // g, y1 * m // g
>     return g, x0, y0
> ```
>
> 

#### 逆元

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥逆元1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥逆元2.jpg)

> ```python
> # 求解 ax + by = gcd(a, b) 的一组解
> # 返回g, x, y
> def exgcd(a, b):
>     # 递归出口
>     if b == 0:
>         return a, 1, 0
>     g, x2, y2 = exgcd(b, a % b)
>     x1, y1 = y2, x2 - (a // b) * y2
>     return g, x1, y1
>    
> def func(a, b, m):
>     g, x1, y1 = exgcd(a, b)
>     # m 必须是gcd(a, b) 的倍数才有解
>     if m % g != 0:
>         return None, None, None
>     x0, y0 = x1 * m // g, y1 * m // g
>     return g, x0, y0
> 
> def Inv(a, n):
>     g, x, y = func(a, n, 1)
>     if x is None:
>         return None
>     else:
>         return (x % n + n) % n
> ```
>
> 

#### 费马小定理

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥费马小定理1.jpg)

#### 欧拉筛

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥欧拉筛.jpg)

### 14-5 欧拉函数

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥欧拉函数1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥欧拉函数2.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥欧拉函数3.jpg)







### 14-6 欧拉定理

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥欧拉定理1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥欧拉定理2.jpg)

[蓝桥1151](https://www.lanqiao,cn/problems//1155/learning/)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥1155.jpg)





### 14-7 卡特兰数

[5. 卡特兰数（Catalan）公式、证明、代码、典例.](https://blog.csdn.net/sherry_yue/article/details/88364746)

## 15、图论

### 15-1 图的基本概念

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图的基本概念.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图的基本概念2.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图的基本概念3.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图的存储方式1.jpg)

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图的存储方式2.jpg)

### 15-2 DFS 遍历

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图论dfs遍历.jpg)

### 15-3 BFS 遍历

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥图论BFS遍历.jpg)

### 15-4 拓扑排序

> **==适用于有向无环图==**

![](D:\fileprogram\typoraprogram\编程语言基础\Images\蓝桥BFS实现拓扑排序.jpg)



### 15-5 ==Floyd==















### 15-6 ==Dijkstra==











### 15-7 ==Johnson==







































## 16、数据结构

### 16-1 基础数据结构

#### 16-1-1 并查集基础

![](D:\typoraprogram\编程语言基础\Images\蓝桥基础数据结构并查集1.jpg)





















































[1.蓝桥幼儿园 - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/1135/learning/?page=1&first_category_id=1&name=蓝桥幼儿园)

> ```python
> import sys
> input = sys.stdin.readline
> def findroot(x):
>     if x == p[x]:
>         return x
>     p[x] = findroot(p[x])
>     return p[x]
> def merge(x, y):
>     rootx = findroot(x)
>     rooty = findroot(y)
>     p[rootx] = rooty
> def query(x, y):
>     rootx, rooty = findroot(x), findroot(y)
>     return rootx == rooty
> 
> 
> n, m = map(int, input().split())
> p = list(range(n + 1))
> for i in range(m):
>     op, x, y = map(int, input().split())
>     if op == 1:
>         merge(x, y)
>     else:
>         if query(x, y):
>             print("YES")
>         else:
>             print("NO")
> ```
>
> 



## 17、字符串

### 17-1 **==KMP==**

![](D:\typoraprogram\编程语言基础\Images\蓝桥KMP算法1.jpg)

![](D:\typoraprogram\编程语言基础\Images\蓝桥KMP算法2.jpg)

![](D:\typoraprogram\编程语言基础\Images\蓝桥KMP算法3.jpg)



[1.斤斤计较的小Z - 蓝桥云课 (lanqiao.cn)](https://www.lanqiao.cn/problems/2047/learning/?page=1&first_category_id=1&name=斤斤计较的小)

> ```python
> def get_next(t):
>     for i in range(1, len(t)):
>         j = next[i]
>         while j > 0 and t[i] != t[j]:
>             j = next[j]
>         if t[i] == t[j]:
>             next[i + 1] = j + 1
>         else:
>             next[i + 1] = 0
> 
> def KMP(s, t):
>     ans = 0
>     j = 0
>     for i in range(len(s)):
>         while j > 0 and s[i] != t[j]:
>             j = next[j]
>         if s[i] == t[j]:
>             j += 1
>         if j == len(t):
>             ans += 1
>             j = next[j]
>     return ans
> 
> 
> next = [0] * 1000010
> s = input()
> t = input()
> print(KMP(t, s))
> ```
>
> ```python
> s = input()
> t = input()
> mod = 10 ** 9 + 7
> m, n = len(s), len(t)
> hash = [0] * (n + 1)
> numT = 0
> B = 26
> p = B ** m
> ans = 0
> for i in s:
>     numT = numT * B + ord(i) - ord('A')
>     numT %= mod
> for i in range(1, n + 1):
>     hash[i] = hash[i - 1] * B + ord(t[i - 1]) - ord('A')
>     hash[i] %= mod
> 
> for l in range(n + 1):
>     r = l + m - 1
>     if r > n:
>         break
>     if (hash[r] - hash[l - 1] * p + mod) % mod == numT:
>         ans += 1
> print(ans)
> ```
>
> 





### 17-2 字符串哈希

![](D:\typoraprogram\编程语言基础\Images\蓝桥字符串哈希1.jpg)

![](D:\typoraprogram\编程语言基础\Images\蓝桥字符串哈希2.jpg)
