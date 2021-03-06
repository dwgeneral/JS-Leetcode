## 学习笔记

#### 如何使用Leetcode进行算法学习
  - 不在于AC的题数量，而是针对每道题，要多练（五遍）
    - 第一遍：
      - 计时五分钟思考，写出自己能想到的可能的解法的伪代码，一般五分钟内能想到2-3个解法就是极好的
      - 如果完全没有思路，熬五分钟后直接去官网+中文网站看题解，选出3个题解，背下来
    - 第二遍：
      - 自己重新看这道题，从思路整理到代码AC，看自己是否能一遍过，如果不行，重复此操作
      - 考虑是否将此题加入到后续练习题目中
    - 第三遍：
      - 三天后，重新做自己记录的练习题目
    - 第四遍：
      - 一周后，重新做自己记录的练习题目
      - 考虑是否此题已完全掌握，移出练习题目
    - 第五遍：
      - 面试前, 重新做
      - 官网一遍
      - 中文网一遍
      - 换语言再一遍

#### Array 数组
  - 是一种线性表结构，它用一组连续的存储空间，来存储一组具有相同类型的数据
  - 线性表是指数据排列像一条线一样的数据结构，数组，链表，队列，栈，都是线性表结构
#### LinkedList 链表
  - 是一种线性表结构，它通过指针将一组零散的内存块串联在一起，这些内存块中除了存储数据外，还会记录下一个内存块的地址
  - 链表是一种物理存储单元上非连续、非顺序的存储结构，数据元素的逻辑顺序是通过链表中的指针链接次序实现的
  - 链表存在多种形式
    - 单链表
      - 只有一个后继指针的链表
    - 双链表
      - 一个后继指针，一个前驱指针
      - 占用更多空间，插入和删除效率更高
      - 空间换时间的思想
      - 实际使用例子：Java 的 LinkedHashMap
    - 循环链表
      - 尾节点指针指向头节点的链表
      - 可以是单链表，也可以是双链表
      - 约瑟夫问题
    - 静态链表
      - 用二维数组描述的链表称为静态链表
#### SkipList 跳表
  ![https://redisbook.readthedocs.io/en/latest/_images/skiplist.png](https://redisbook.readthedocs.io/en/latest/_images/skiplist.png)
  - 出现背景：为了弥补链表在查询中的缺陷而设计
  - 工程应用：Redis中应用广泛
  - 掌握范畴：以理解它的工作原理为主，一般不会在面试中出题
  - 设计思想：
    - 以空间换时间
    - 增加多级索引（指针）来达到跨越查询，以此来提高查询效率
    - 每个节点除了存储本身的 Next指针外，还需要存储多个跳级的指针，占用了更多的内存空间，提高了效率，此之谓空间换时间
  - 缺点：
    - 在工程中，一旦涉及到节点的增加和删除，索引就要重新更新，进而导致各个节点的跨级不一致，导致维护成本高，导致插入和删除操作的时间复杂度也会达到O(logn)而不是O(1)了
  - 复杂度分析：
    - 时间复杂度：O(logn)
    - 空间复杂度：O(n)
#### Stack 栈
  - 是一种“操作受限”的线性表，只允许在一端插入和删除数据，先进后出
  - 栈既可以用数组来实现，也可以用链表来实现
  - 用数组实现的栈，叫做顺序栈
  - 用链表实现的栈，叫做链式栈
#### Queue 队列
  - 是一种“操作受限”的线性表，只支持入队和出队操作，先进先出
  - 队列既可以用数组来实现，也可以用链表来实现
  - 用数组实现的队列，叫做顺序队列
  - 用链表实现的队列，叫做链式队列
  - Priority Queue 优先队列
    - 插入操作：O(1)
    - 取出操作：O(logn) -- 按照元素的优先级取出
    - 底层实现的数据结构较为复杂和多样：heap, BST, 红黑树, AVL, treap

#### 哈希表
- Hash Table
  - 将KeyValuePair通过哈希函数映射到数组中具体下标。存储这种KeyValuePair的数据结构

- Hash Collisions（哈希碰撞）
  - 两组KV，通过哈希函数得到了相同的下标，那么就在此下标对应的位置构建一个链表，来存储数据

#### 树的遍历
- 前序遍历  根-左-右
- 中序遍历  左-根-右
- 后续遍历  左-右-根
- 树的遍历一般都是采用递归的方式，因为树结构用循环的话会很复杂和麻烦。我们要拥抱递归

```python
// 树的遍历代码模版
def preorder(self, root):
	if root:
		self.traverse_path.append(root.val)
		self.preorder(root.left)
		self.preorder(root.right)

def inorder(self, root):
	if root:
		self.inorder(root.left)
		self.traverse_path.append(root.val)
		self.inorder(root.right)

def postorder(self, root):
	if root:
		self.postorder(root.left)
		self.postorder(root.right)
		self.traverse_path.append(root.val)
```

#### Binary Search Tree
- 动态示例Demo：[https://visualgo.net/zh/bst](https://visualgo.net/zh/bst)
- 指一棵空树或者具有下列性质的二叉树
    - 左子树上所有结点的值 < 根结点值
    - 右子树上所有结点的值 > 根结点值
- 常见操作
    - 查询 O(logn)
    - 插入 O(logn)
    - 删除 O(logn)
        - 如果删除的结点存在子结点，则先找到比该结点值大的第一个元素，将其替换后，删除该结点
- tips
  - 树和图最关键的差别，就是看有没有环
  - 链表是特殊化的树，树是特殊化的图（没有环的图就是树）


#### 递归、回溯
```python
// 递归代码模版
def recursion(level, params1, params2, ...):
	# recursion terminator 终止条件
	if level > MAX_LEVEL
		process_result
		return

	# process logic in current level 处理当前层逻辑
	process(level, data...)

	# drill down 下探到下一层
	self.recursion(level+1, p1, ...)
	
	# reverse the current level status if needed 清理当前层
```

```python
// 回溯代码模版
result = []
def backtrack(路径，选择列表):
	if 满足结束条件:
		result.add(路径)
		return
	for 选择 in 选择列表
		做选择
		backtrack(路径，选择列表)
		撤销选择
```

- Backtracking 回溯
  - 回溯法是暴力搜索法中的一种（from wikipedia）
  - 回溯法是一种可以找出所有（或一部分）解的一般性算法，尤其适用于约束满足问题
  - 回溯法采用试错的思想，它尝试分步的去解决一个问题。在分步解决问题的过程中，当它通过尝试发现现有的分步答案不能得到有效的正确的解答的时候，它将取消上一步甚至是上几步的计算，再通过其它的可能的分步解答再次尝试寻找问题的答案。回溯法通常用最简单的递归方法来实现，在反复重复上述的步骤后可能出现两种情况：
      - 找到一个可能存在的正确的答案
      - 在尝试了所有可能的分步方法后宣告该问题没有答案
  - 在最坏的情况下，回溯法会导致一次复杂度为指数时间的计算。
  - 参考资料
      - [https://zh.wikipedia.org/wiki/回溯法](https://zh.wikipedia.org/wiki/%E5%9B%9E%E6%BA%AF%E6%B3%95)

#### 分治、回溯的实现和特性

- 分治和回溯都是递归而已
- 分治（Divide & Conquer）：将一个大问题分成若干小问题，解决掉这些小问题，Merge回去，就解决了大问题
  ```javascript
  // 递归
  const recursion = (level, params) => {
    // recursion terminator
    if (level > MAX_LEVEL) {
      process_result
      return
    }
    // process current level
    process(level, params)
    // drill down
    recursion(level + 1, params)
    // clean current level status if needed	
  }
  
  // 分治
  const divide_conquer = (problem, params) => {
    // recursion terminator
    if (problem == null) {
      process_result
      return
    } 
    // process current problem
    subproblems = split_problem(problem, data)
    subresult1 = divide_conquer(subproblem[0], p1)
    subresult2 = divide_conquer(subproblem[1], p1)
    subresult3 = divide_conquer(subproblem[2], p1)
    ...
    // merge
    result = process_result(subresult1, subresult2, subresult3)
    // revert the current level status
  }
  ```

#### 深度优先搜索 DFS

- 递归、栈来实现
    ```python
    def dfs(node):
    	if node in visited:
    		return
    	visited.add(node)
    	dfs(node.left)
    	dfs(node.right)

#### 广度优先搜索 BFS

- 队列实现
    ```python
    def bfs(graph, start, end):
      queue = []
      queue.append([start])
      visited.add(start)

      while queue:
        node = queue.pop()
        visited.add(node)
        process(node)
        nodes = generate_related_nodes(node)
        queue.push(nodes)

    // BFS
    const BFS = (root) => {
      if (!root) return []
      let result = [], queue = [root]
      while (queue.length > 0) {
        let level = [], n = queue.length
        for (let i = 0; i < n; i++) {
          let node = queue.pop()
          level.push(node.val) 
          if (node.left) queue.unshift(node.left)
          if (node.right) queue.unshift(node.right)
        }
        result.push(level)
      }
      return result
    };

#### 贪心算法

- 是一种在每一步选择中都采取在当前状态下最好或最优的选择，不能回退，从而希望导致结果是全局最好或最优的算法
- 解决一些最优问题，如：求图中的最小生成树、哈夫曼编码。然而对于工程和生活上的问题，贪心算法一般不能得到我们所要求的答案
- 那为什么还会有这个算法呢？因为一旦一个问题通过贪心算法来解决，那么贪心算法一般是解决这个问题的最好办法。由于贪心算法的高效性以及其所求得的答案比较接近最优结果。

#### 贪心算法、回溯算法、动态规划

- 贪心算法：只会当下做局部最优判断且不能回退
- 回溯算法：能够回退
- 动态规划：会保存之前的运算结果，根据以前的结果对当前进行选择，可以回退

#### 二分查找

- 使用二分查找的条件
    - 有序
    - 存在上下界
    - 能够通过索引访问
    ```python
    # 代码模版
    left, right = 0, len(array) - 1
    while left <= right:
      mid = (left + right) / 2
      if array[mid] == target:
        # find the target
        return
      elsif array[mid] < target:
        left = mid + 1
      else
        right = mid - 1

#### 动态规划

动态规划 和 递归或者分治 没有根本上的区别

- 共性：找到重复子问题
- 差异性：动态规划是找到最优子结构，中途淘汰次优解；如果没有最优子结构，那就变成了分治算法了
- 也正是存在最优子结构，所以动态规划的时间复杂度会明显由于指数级的分治算法

动态规划关键点

- 最优子结构 opt[n] = best_of(opt[n-1], opt[n-2])  （第n个的值等于前面几个值的关系）
- 储存中间状态：opt[i]
- 递推公式
    - Fib：opt[i] = opt[n-1] + opt[n-2]
    - 二维路径：opt[i,j] = opt[i+1][j] + opt[i][j+1] （且判断a[i,j]是否空地）

动态规划思维框架

- 采用自底向上的思维方式（for循环）(PS:  递归、分治等都是采用自顶向下的思维方式，构造递归树）
- 动态规划问题的一般形式就是求最值，其实是运筹学的一种最值优化方法
- 既然是求最值，核心问题是什么？是穷举。因为要求最值，肯定要把所有可行的答案穷举出来找
- 但是动归的穷举有点特别，因为这类问题存在「**重叠子问题**」，所以可以通过「备忘录」或者「DP Table」来优化穷举过程，避免不必要的计算
- 而且，动态规划问题一定会具备「**最优子结构**」，才能通过子问题的最值得到原问题的最值。
- 而要要找重叠子问题以及最优子结构，只有列出正确的「**状态转移方程**」才能正确地穷举
    - 先明确「状态」—— 原问题和子问题中变化的变量
        - 例如 coin change 问题，状态是目标金额 amount
    - 确定 dp 函数的定义 ——- 也就是问题
        - 例如 coin change 问题，dp(n) 表示至少需要 dp(n) 个硬币凑出目标金额 n
    - 确定「选择」并择优 ——  也就是对于每个状态，可以做出什么选择，改变当前状态
        - 例如 coin change 问题，无论当前的目标金额是多少，选择就是从 coins 中选择一个硬币，然后目标金额就会减少
    - 最后明确 base case
        - 例如 coin change 问题，显然目标金额为 0 时，所需硬币数量为 0；当目标金额小于 0 时，无解，返回 -1

解决动态规划类问题的一般优化顺序

- Find recursive relation
- Recursive（top-down)
- Recursive + memo (top-down)
- Iterative + memo (bottom-up)
- Iterative + N variables (bottom-up)

**位运算**
- 为什么需要位运算
  - 直接进行二进制运算，速度快，比十进制运算要快很多
- 位运算常用场景
  - 判断奇偶
      - x % 2 == 1  ——>  (x & 1) == 1  (判断二进制最后一位是0或1)
      - x % 2 == 0 ——>  (x & 1) == 0
  - 除2运算
      - x = x / 2 ——>  x = x >> 1 (右移一位)
  - 清零最低位的1
      - x = x & (x-1)
  - 得到最低位的1
      - x & -x
  - x & ~x =⇒ 0

**布隆过滤器（Bloom Filter）**
- 是什么
    - 一个很长的二进制向量和一系列随机映射函数
- 干嘛用
    - 用于检索一个元素是否在一个集合中
- 为什么用它
    - Bloom Filter vs Hash Table
        - 哈希表是精确存储信息，如果产生哈希冲突会采用拉链式存储，保证所有数据都存储精确
        - 布隆过滤器的空间效率和查询效率都远远超过一般的算法
        - 布隆过滤器是一种模糊的查询方式，缺点是有一定的误识别率和删除困难

**LRU Cache**
- 常规实现：Hash Table + Double LinkedList
- 效率： 查询、修改都是 O(1)

**比较类排序**
- 通过比较来决定元素间的相对次序，其时间复杂度不能突破 O(nlogn)，属于非线性时间排序
- 适用于各种数据结构，数字类型，字符串类型，对象类型等
- 交换排序
  - 冒泡排序 O(n^2)
  - 快速排序 O(nlogn)
- 插入排序
  - 简单插入排序 O(n^2)
  - 希尔排序 
- 选择排序
  - 简单选择排序 O(n^2)
  - 堆排序 O(nlogn)
- 归并排序 O(nlogn)
  - 二路归并排序
  - 多路归并排序

**非比较类排序**
- 不通过比较来决定元素间的相对次序，它可以突破基于比较排序的时间下界，以线性时间运行，属于线性时间排序
- 一般只适用于整数型数据，同时需要额外的内存空间
- 计数排序、基数排序、桶排序

![sortAlgorithms](./assets/sortAlgorithms.png)

### 初级排序 O(n^2)

- 选择排序
    - 每次找最小值，然后放到待排序数组的起始位置
      ```javascript
      // 选择排序
      export default (nums) => {
        for (let i = 0; i < nums.length; i++) {
          let min = nums[i]
          for (let j = i+1; j < nums.length; j++) {
            if (nums[j] < min) [nums[j], min] = [min, nums[j]]
          }	
          arr[i] = min
        }
      }
      ````

- 插入排序
    - 从前到后逐步构建有序序列；对于未排序数据，在已排序序列中从后向前扫描，找到相应位置并插入
      ```javascript
      // 插入排序
      export default (nums) => {
        for (let i = 1; i < nums.length; i++) {
          for (let j = i; j > 0; j--) {
            if (nums[j-1] <= nums[i]) break
            nums[j] = nums[j-1]
          }
          nums[j] = nums[i]
        }
      }
      ```

- 冒泡排序
    - 嵌套循环，每次查看相邻的元素如果逆序，就交换
      ```javascript
      // 冒泡排序
      export default (nums) => {
        for (let i = nums.length-1; i > 0; i--) {
          for (let j = 0; j < i; j++) {
            if (nums[j] > nums[j+1]) [nums[j], nums[j+1]] = [nums[j+1], nums[j]]
          }		
        }
      }
      ```

### 高级排序 O(nlogn)

- 快速排序
    - 基于分治的思想
    - 数组取标杆 pivot，将小元素放在 pivot 左边，大元素放右侧，然后依次对右边和右边的子数组继续快排；以达到整个序列有序
      ```javascript
      // 快速排序
      const quickSort = (nums, left, right) => {
        if (nums.length <= 1) return nums
        if (left < right) {
          index = partition(nums, left, right)
          quickSort(nums, left, index-1)
          quickSort(nums, index+1, right)
        }
      }
      
      const partition = (nums, left, right) => {
        let pivot = left, index = left + 1
        for (let i = index; i <= right; i++) {
          if (nums[i] < nums[pivot]) {
            [nums[i], nums[index]] = [nums[index], nums[i]]
            index++
          }
        }
        [nums[pivot], nums[index-1]] = [nums[index-1], nums[pivot]]
        return index
      }
      
      quickSort(nums, 0, nums.length-1)
      return nums
      ```
        

- 归并排序
    - 把长度为 n 的序列分成两个长度为 n/2 的子序列
    - 对子序列分别采用归并排序
    - 将两个排序好的子序列合并成一个最终的排序序列
      ```javascript
      // 归并排序
      const mergeSort = (nums) => {
        if (nums.length <= 1) return nums
        let mid = Math.floor(nums.length/2), 
            left = nums.slice(0, mid), 
            right = nums.slice(mid)
        return merge(mergeSort(left), mergeSort(right))
      }
      
      const merge(left, right) => {
        let result = []
        while(left.length && right.length) {
          result.push(left[0] <= right[0] ? left.shift() : right.shift()
        }
        while(left.length) result.push(left.shift())
        while(right.length) result.push(right.shift())
        return result
      }
      ```
    - 归并和快排具有相似性，但步骤顺序相反
        - 归并：先一分为二，分成左右子数组，分别排序左右子数组，再合并
        - 快排：先选择pivot，然后分成左右，左边为已排序，再对右子数组继续快排，以达到整个序列有序

- 堆排序
    - 分大顶堆和小顶堆
    - 插入、删除堆操作 O(logn)，取最大值最小值都是 O(1)
    - 数组元素依次建立小顶堆
    - 依次取堆顶元素，并删除
- 计数排序
    - 计数排序的核心在于将输入的数据值转化为键存储在额外开辟的数组空间中。作为一种线性时间复杂度的排序，计数排序要求输入的数据必须是有确定范围的整数。
- 桶排序
    - 桶排序是计数排序的升级版。它利用了函数的映射关系，高效与否的关键就在于这个映射函数的确定。为了使桶排序更加高效，我们需要做到这两点：
        1. 在额外空间充足的情况下，尽量增大桶的数量
        2. 使用的映射函数能够将输入的 N 个数据均匀的分配到 K 个桶中
    - 同时，对于桶中元素的排序，选择何种比较排序算法对于性能的影响至关重要。
- 基数排序
    - 先排各位的值，0-9；再排十位的值，0-9；依此类推
    - 基数排序是一种非比较型整数排序算法，其原理是将整数按位数切割成不同的数字，然后按每个位数分别比较。由于整数也可以表达字符串（比如名字或日期）和特定格式的浮点数，所以基数排序也不是只能使用于整数。

**扩展阅读**

- 十大经典排序算法多语言实现  [https://sort.hust.cc/](https://sort.hust.cc/)

#### 高级动态规划

**不同路径2的状态转移方程**
```javascript
if (dp[i][j] is obstacle) dp[i][j] = 0
else dp[i][j] = dp[i][j-1] + dp[i-1][j]
```

**知识回顾**

- 动态规划、递归、分治 没有根本上的区别（关键看有无最优子结构）
- 拥有共性：找到重复子问题

**典型动态规划题目**

- 爬楼梯问题
```javascript
  // 就是斐波那契数列
  // 暴力解法，直接递归 O(2^n)
  const fn = (n) => {
    if (n <= 1) return 1
    return f(n-1) + f(n-2)
  }
  // 优化1: 递归 + 记忆化搜索  O(n)
  const fn = (n) => {
    if (n <= 1) return 1
    if (!mem.has(n)) mem.set(n, f(n-1) + f(n-2))
    return mem.get(n)
  }
  // 优化2: 将递归转换为顺推的形式，通过状态转移方程来求解 O(n)
  const fn = (n) => {
    for (let i = 2; i < n + 1; i++) {
      dp[i] = dp[i-1] + dp[i-2]
    }
    return dp[n]
  }
  // 优化3: 进行空间复杂度优化，去掉dp数组，使用两个变量来处理 O(n) O(1)
  const fn = (n) => {
    for (let i = 1; i < n; i++) {
      curr, prev = prev + curr, curr
    }
  }
```
- 路径问题
```javascript
  dp[i][j] = dp[i-1][j] + dp[j][i-1]
```
- 打家劫舍问题
```javascript
// 第一种状态方程的定义 dp[i] 表示打劫第0-i个房子的总收益是多少
dp[i] = max(dp[i-2] + nums[i], dp[i-1])

//第二种状态方程的定义
// 二维DP  
// dp[i][0] 表示 打劫第0-i个房子且第i个房子没偷时的收益
// dp[i][1] 表示 打劫第0-i个房子且第i个房子偷了时的收益
dp[i][0] = max(dp[i-1][0], dp[i-1][1])
dp[i][1] = dp[i-1][0] + nums[i]
```
- 最小路径和
```javascript
  dp[i][j] = min(dp[i-1][j], dp[i][j-1]) + A[i][j]
```
- 股票买卖
```javascript
// i 为天数；k 为最多交易次数；[0,1] 为是否持有股票
// 初始状态
dp[-1][k][0] = dp[i][0][0] = 0
dp[-1][k][1] = dp[i][0][1] = -infinity
// 状态转移方程
dp[i][k][0] = max(dp[i-1][k][0], dp[i-1][k][1] + prices[i])
dp[i][k][1] = max(dp[i-1][k][1], dp[i-1][k-1][0] - prices[i])
```

**高阶DP解读**

- 状态拥有更多维度（二维、三维、或者更多、甚至需要压缩）
- 能通过面试题定义出维度，对逻辑思维能力要求高
- 状态方程更加复杂
- 本质：内功、逻辑思维、数学
- 训练：多练多思考

#### 字符串算法

- Javascript, Java, C#, Python, Go 中，string 是 immutable 不可变的
- Ruby, PHP 中，string 是 mutable 可变的
- Swift 中，string 是 mutable 可变的，但可以使用 let 来让它变成 immutable

**字符串匹配算法**

- Rabin-Karp 算法
    - 假设子串的长度为M（pat），目标字符串的长度为 N （txt）
    - 计算子串的 hash 值 hash_pat
    - 计算目标字符串 txt 中每个长度为 M 的子串的 hash 值（共需要计算 N-M+1 次）
    - 比较 hash 值：如果 hash 值不同，字符串必然不匹配；如果 hash 值相同，还需要使用朴素算法再次确认一下
- KMP 算法
    - 写出 pat 子串的所有前缀字符串(prefixStr)，不包含自身
    - 计算出每个前缀字符串(prefixStr)的最长公共前后缀字符数是多少（数字）
    - 将上面的数字组合成 prefixTable，并设置 prefixTable[0] = -1