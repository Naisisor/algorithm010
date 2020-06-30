# Table of Contents

- [Table of Contents](#table-of-contents)
  - [预习课程](#预习课程)
    - [LeetCode](#leetcode)
    - [数据结构与算法总览](#数据结构与算法总览)
    - [切题四件套](#切题四件套)
    - [五毒练习法](#五毒练习法)
    - [刷题核心思想和误区](#刷题核心思想和误区)
    - [Know Thy Complexities!](#know-thy-complexities)
  - [第一周](#第一周)
    - [第 3 课 | 数组、链表、跳表](#第-3-课--数组链表跳表)
      - [数组、链表、跳表的基本实现和特性](#数组链表跳表的基本实现和特性)
      - [实战题目解析](#实战题目解析)
        - [Array 实战题目](#array-实战题目)
        - [Linked List 实战题目](#linked-list-实战题目)
      - [常见问题解决办法](#常见问题解决办法)
    - [第 4 课 | 栈、队列、优先队列、双端队列](#第-4-课--栈队列优先队列双端队列)
      - [栈和队列的实现与特性](#栈和队列的实现与特性)
      - [实战题目解析](#实战题目解析-1)

## 预习课程

### LeetCode

- LeetCode 官网：[https://leetcode.com/](https://leetcode.com/)
- LeetCode 中文社区：[https://leetcode-cn.com/](https://leetcode-cn.com/)

### 数据结构与算法总览

待补充......

### 切题四件套

- Clarification
- Possible solutions
  - compare (time/space)
  - optimal（加强）
- Coding（多写）
- Test cases

### 五毒练习法

1. 刷题第一遍
   1. 5 分钟：读题 + 思考（最多不要超过 15 分钟）
   2. 直接看解决：注意！多解法，比较解法优劣（如何 15 分钟后依旧没思路的情况下）
   3. **背诵、默写好的解法**（这一步很重要）
2. 刷题第二遍
   1. 将每种解法写一遍（闭卷），反复 Debug，直到代码在 [LeetCode](https://leetcode-cn.com/) 上执行通过
   2. 对多种解法之间的优劣进行体会、优化
   3. 总结及反思自己写的时候遇到的一些问题
3. 刷题第三遍
   1. 时隔一天后，再重复做题
   2. 对于不同解法的熟练程度进行专项练习
4. 刷题第四遍：时隔一周后，反复回来练习相同的题目
5. 刷题第五遍：面试前一周进行恢复性训练

### 刷题核心思想和误区

- 思想
  1. 重复刷题至少刷 5 遍
  2. 优化方法：空间换时间、升维（二维）
- 误区：做题只做一遍

### [Know Thy Complexities!](https://www.bigocheatsheet.com/)

- Big-O Complexity Chart

![Big-O Complexity Chart](./Big-O%20Complexity%20Chart.png)

- Common Data Structure Operations

![Common Data Structure Operations](./Common%20Data%20Structure%20Operations.png)

- Array Sorting Algorithms

![Array Sorting Algorithms](./Array%20Sorting%20Algorithms.png)

## 第一周

### 第 3 课 | 数组、链表、跳表

#### 数组、链表、跳表的基本实现和特性

- 数组（Array）：
  - 访问任何一个元素的时间复杂度 O(1)
  - 插入、修改、删除的时间复杂度 O(n)
- 链表（Linked List）
  - 查找（lookup），时间复杂度 O(n)
  - prepend（头/尾节点增加）、append、insert、delete 时间复杂度 O(1)
- 跳表(Skip List)
  - 插入、删除、搜索时间复杂度 O(logn)
  - 跳表的实现原理是 升维思想 + 空间换时间
  - 跳表里面的元素必须是有序的，跳表对标的是平衡树也就是二叉搜索数中和二分查找
  - 跳表的最大优势是原理简单、容易实现、方便扩展、效率更高。因此在一些热门的项目里用来替代平衡树，如 Redis、LevelDB 等，缺点：维护成本较高
- 参考链接
  - [Java 源码分析（ArrayList）](http://developer.classpath.org/doc/java/util/ArrayList-source.html)
  - [Linked List 的标准实现代码](http://www.geeksforgeeks.org/implementing-a-linked-list-in-java-using-class/)
  - [Linked List 示例代码](http://www.cs.cmu.edu/~adamchik/15-121/lectures/Linked%20Lists/code/LinkedList.java)
  - [Java 源码分析（LinkedList）](http://developer.classpath.org/doc/java/util/LinkedList-source.html)
  - LRU Cache - Linked list - [LRU 缓存机制](http://leetcode-cn.com/problems/lru-cache)
  - Redis - Skip List：[跳跃表、为啥 Redis 使用跳表（Skip List）而不是使用 Red-Black？](http://www.zhihu.com/question/20202931)

#### 实战题目解析

##### Array 实战题目

1. [两数之和](https://leetcode-cn.com/problems/two-sum/)
2. [移动零](https://leetcode-cn.com/problems/move-zeroes/)
3. [盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/) 使用 「左右夹逼」双指针的方法解决

   ```Python
    class Solution:
        def maxArea(self, height: List[int]) -> int:
          # 暴力解法，时间复杂度 O(n²)
          ans = 0
          for i, m in enumerate(height):
              for j, n in enumerate(height[i + 1:], i + 1):
                  ans = max(ans, min(m, n) * (j - i))
          return ans

        def maxArea1(self, height: List[int]) -> int:
          # 双指针，左右夹逼，时间复杂度 O(n)
            ans, left, right = 0, 0, len(height) - 1
            while left < right:
                ans = max(ans, min(height[left], height[right]) * (right - left))
                if height[left] < height[right]:
                    left += 1
                else:
                    right -= 1
            return ans
   ```

4. [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)
5. [三数之和](https://leetcode-cn.com/problems/3sum/)

```python
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        # 三重循环暴力解法， 时间复杂度 O(n³)
        nums.sort()
        res = []
        for i in range(len(nums)):
          for j in range(i + 1, len(nums)):
            for k in range(j + 1, len(nums)):
              if nums[i] + nums[j] + nums[k] == 0:
                item = sorted([nums[i], nums[j], nums[k]])
                if item not in res:
                    res.append(item)
        return res

    def threeSum1(self, nums: List[int]) -> List[List[int]]:
        # hash 解法，时间复杂度 O(n²)
        nums.sort()
        d = {-x: i for i, x in enumerate(nums)}
        res = []
        for i in range(len(nums)):
          if nums[i] > 0: break
          for j in range(i + 1, len(nums)):
            if nums[i] + nums[j] in d:
              index = d[nums[i] + nums[j]]
              if index in (i, j):
                continue
              c = sorted([nums[i] , nums[j], nums[index]])
              if c not in res:
                res.append(c)
        return res

    def threeSum2(self, nums: List[int]) -> List[List[int]]:
        # 排序、双指针，左右夹逼，时间复杂度 O(n²)
        # 双指针方法通常先排序
        nums.sort()
        res = []
        for k in range(len(nums) - 2):
          if nums[k] > 0: break
          if k > 0 and nums[k] == nums[k - 1]: continue
          i, j = k + 1, len(nums) - 1
          while i < j:
            s = nums[i] + nums[j] + nums[k]
            if s < 0:
              i += 1
            elif s > 0:
              j -= 1
            else:
              res.append([nums[k], nums[i], nums[j]])
              i += 1
              j -= 1
              while i < j and nums[i] == nums[i - 1]: i += 1
              while i < j and nums[j] == nums[j + 1]: j -= 1
        return res
```

##### Linked List 实战题目

1.  [反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None

    class Solution:
        def reverseList(self, head: ListNode) -> ListNode:
            # 迭代
            cur, prev = head, None
            while cur:
                prev, cur.next, cur, = cur, prev, cur.next
            return prev

        def reverseList1(self, head: ListNode) -> ListNode:
            # 递归
            if not (head and head.next):
                return head
            new_head = self.reverseList(head.next)
            head.next.next, head.next = head, None
            return new_head
    ```

2.  [两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs) 图解 [Python | Dummynode](https://leetcode.com/problems/swap-nodes-in-pairs/discuss/171788/Python-or-Dummynode)

    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None

    class Solution:
        def swapPairs(self, head: ListNode) -> ListNode:
            # 迭代
            dummy = cur = ListNode(0)
            cur.next = head
            while cur.next and cur.next.next:
                fir, sec = cur.next, cur.next.next
                cur.next, fir.next, sec.next = sec, sec.next, fir
                cur = cur.next.next
            return dummy.next

        def swapPairs1(self, head: ListNode) -> ListNode:
            # 递归
            if not head or not head.next:
                return head
            new_start = head.next.next
            head, head.next = head.next, head
            head.next.next = self.swapPairs(new_start)
            return head
    ```

3.  [环形链表](https://leetcode-cn.com/problems/linked-list-cycle)
4.  [环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii)
5.  [K 个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

#### 常见问题解决办法

> 解决各种问题的关键是找最近重复子问题

1. 遇到问题不会解，懵逼的情况下怎么解决
   1. 思考能不能暴力解决
   2. 最基本的情况应该怎么解决

### 第 4 课 | 栈、队列、优先队列、双端队列

#### 栈和队列的实现与特性

- Stack（栈）：
  - 特征：后进先出（LIFO），添加、删除皆为 O(1)，查询 O(n)
  - 查询资料关键字，比如 Java 资料，搜索关键字为 stack java 10
- Queue（队列）：
  - 特征：先入先出（FIFO），添加、删除皆为 O(1)，查询 O(n)
  - 查询资料关键字：queue python 3
- Deque（Double-End Queue，双端队列）
  - 简单理解：双端可以进出的 Queue，Double-End Queue（Stack 和 Queue 的结合）
  - 插入和删除都是 O(1) 操作，查询 O(n)
- Priority Queue（优先队列）
  - 插入： O(1)
  - 取出操作：O(logN) - 按照元素的优先级取出。好处：取出操作不再是先入先出的，而是按照优先级
    - 底层具体实现的数据源结构较为多样和复杂：heap（堆）、bst、treap
      - heap 也是多种实现的，可能是所谓的二叉树实现的堆，也可能是 Fibonacci 堆或者其它形式的堆
- 参考链接
  - [Java 的 PriorityQueue 文档](http://docs.oracle.com/javase/10/docs/api/java/util/PriorityQueue.html)
  - [Java 的 Stack 源码](http://developer.classpath.org/doc/java/util/Stack-source.html)
  - [Java 的 Queue 源码](http://fuseyism.com/classpath/doc/java/util/Queue-source.html)
  - [Python 的 heapq](http://docs.python.org/2/library/heapq.html)
  - [高性能的 container 库](http://docs.python.org/2/library/collections.html)
- 什么样题目可以用 Stack 来解决？
  - 具有最近相关性的事物，适合用 Stack 方法解决，如 [有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

#### 实战题目解析

1. [有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

   ```python
   class Solution:
       def isValid(self, s: str) -> bool:
           stack = []
           d = {')': '(', ']': '[', '}': '{'}
           for char in s:
               if char in d:
                   if stack == [] or d[char] != stack.pop():
                       return False
               else:
                   stack.append(char)
           return not stack
   ```

2. [最小栈](https://leetcode-cn.com/problems/min-stack/)

   ```python
   class MinStack:

       def __init__(self):
           """
           initialize your data structure here.
           """
           self.stack = []
           self.min_stack = [math.inf]

        def push(self, x: int) -> None:
            self.stack.append(x)
            self.min_stack.append(min(x, self.min_stack[-1]))

        def pop(self) -> None:
            self.stack.pop()
            self.min_stack.pop()

        def top(self) -> int:
            return self.stack[-1]

        def getMin(self) -> int:
            return self.min_stack[-1]
   ```

3. [柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram)
4. [滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum)
