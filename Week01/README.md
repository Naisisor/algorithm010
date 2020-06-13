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
    - [第三课 | 数组、链表、跳表](#第三课--数组链表跳表)
      - [数组、链表、跳表的基本实现和特性](#数组链表跳表的基本实现和特性)
      - [实战题目解析](#实战题目解析)
      - [常见问题解决办法](#常见问题解决办法)
    - [第四课 | 栈、队列、优先队列、双端队列](#第四课--栈队列优先队列双端队列)
      - [栈和队列的实现与特性](#栈和队列的实现与特性)
      - [实战题目解析](#实战题目解析-1)
    - [作业](#作业)
      - [简单](#简单)
      - [中等](#中等)
      - [困难](#困难)
    - [下周预习](#下周预习)
      - [预习题目](#预习题目)

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

### 第三课 | 数组、链表、跳表

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

- Array 实战题目
    1. [两数之和](https://leetcode-cn.com/problems/two-sum/)
    2. [移动零](https://leetcode-cn.com/problems/move-zeroes/)
    3. [盛最多水的容器](https://leetcode-cn.com/problems/container-with-most-water/) 使用 「左右夹逼」双指针的方法解决
    4. [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)
    5. [三数之和](https://leetcode-cn.com/problems/3sum/)
- Linked List 实战题目
    1. [反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)

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

    2. [两两交换链表中的节点](https://leetcode-cn.com/problems/swap-nodes-in-pairs) 图解 [Python | Dummynode](https://leetcode.com/problems/swap-nodes-in-pairs/discuss/171788/Python-or-Dummynode)

        ```py
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

    3. [环形链表](https://leetcode-cn.com/problems/linked-list-cycle)
    4. [环形链表 II](https://leetcode-cn.com/problems/linked-list-cycle-ii)
    5. [K 个一组翻转链表](https://leetcode-cn.com/problems/reverse-nodes-in-k-group/)

#### 常见问题解决办法

> 解决各种问题的关键是找最近重复子问题

1. 遇到问题不会解，懵逼的情况下怎么解决
    1. 思考能不能暴力解决
    2. 最基本的情况应该怎么解决

### 第四课 | 栈、队列、优先队列、双端队列

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

- 什么样题目可以用 Stack 来解决？
  - 具有最近相关性的事物，适合用 Stack 方法解决，如 [有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)

#### 实战题目解析

- [有效的括号](https://leetcode-cn.com/problems/valid-parentheses/)
- [最小栈](https://leetcode-cn.com/problems/min-stack/)
- [柱状图中最大的矩形](https://leetcode-cn.com/problems/largest-rectangle-in-histogram)
- [滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum)

### 作业

#### 简单

1. 用 add first 或 add last 这套新的 API 改写 Deque 的代码

    ```python
    # 待补充......
    ```

2. 分析 Queue 和 Priority Queue 的源码

    ```python
    # 待补充......
    ```

3. [删除排序数组中的重复项](https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/)

    ```python
    class Solution:
        def removeDuplicates(self, nums: List[int]) -> int:
            # 时间复杂度 O(n)
            i = 1
            n = len(nums)
            while i < n:
                if nums[i] == [i - 1]:
                    nums.pop(i)
                    n += 1
                else:
                    i += 1
            return nums

        def removeDuplicates1(self, nums: List[int]) -> int:
          # 时间复杂度 O(n)
            if len(nums) == 0:
                return 0
            i = 0
            for n in mums:
                if nums[i] == n:
                    continue
                i += 1
                nums[i] = n
            return nums
    ```

4. [旋转数组](https://leetcode-cn.com/problems/rotate-array/submissions/)

    ```python
    class Solution:
        def rotate(self, nums: List[int], k: int) -> None:
          """
          Do not return anything, modify nums in-place instead.
          """
          k = k % len(nums)
          while k != 0:
              nums.insert(0, nums.pop())
              k -= 1
          return nums

        def rotate1(self, nums: List[int], k: int) -> None:
          for _ in range(k):
              nums.insert(0, nums.pop())
          return nums

        def rotate2(self, nums: List[int], k: int) -> None:
          k = k % len(nums)
          nums[:] = nums[-k:] + nums[:-k]
          return nums
    ```

5. [合并两个有序链表](https://leetcode-cn.com/problems/merge-two-sorted-lists/)

    ```python
    # Definition for singly-linked list.
    # class ListNode:
    #     def __init__(self, val=0, next=None):
    #         self.val = val
    #         self.next = next

    class Solution:
        def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
            # 迭代 iteratively
            prev = prehead = ListNode(0)
            while l1 and l2:
                if l1.val < l2.val:
                    prev.next, l1 = l1, l1.next
                else:
                    prev.next, l2 = l2, l2.next
                prev = prev.next
            prev.next = l1 if l1 else l2
            return prehead.next

        def mergeTwoLists2(self, l1: ListNode, l2: ListNode) -> ListNode:
            # 递归 recursively
            if l1 is None: return l2
            if l2 is None: return l1
            if l1.val < l2.val:
                l1.next = self.mergeTwoLists(l1.next, l2)
                return l1
            else:
                l2.next =  self.mergeTwoLists(l2.next, l1)
                return l2
    ```

6. [合并两个有序数组](https://leetcode-cn.com/problems/merge-sorted-array/)
7. [两数之和](https://leetcode-cn.com/problems/two-sum/)

    ```python
    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
          # 暴力解法，时间复杂度 O(n²)
          for i, m in enumerate(nums):
            for j, n in enumerate(nums[i + 1:], i + 1):
              if m + n == target:
                return [i, j]
          return []

        def twoSum2(self, nums: List[int], target: int) -> List[int]:
          # hash，时间复杂度 O(n)
          d = {}
          for i, n in enumerate(nums):
            if taget - n in d:
              return [d[taget - n], i]
          return []
    ```

8. [移动零](https://leetcode-cn.com/problems/move-zeroes/)

    ```python
    class Solution:
        def moveZeroes(self, nums: List[int]) -> None:
            """
            Do not return anything, modify nums in-place instead.
            """
            cur = 0
            for i, n in enumerate(nums):
              if n == 0: continue
              nums[cur], nums[i] = n, nums[cur]
              cur += 1
    ```

9. [加一](https://leetcode-cn.com/problems/plus-one/)

    ```python
    class Solution:
        def plusOne(self, digits: List[int]) -> List[int]:
          num =  functools.reduce(lambda x, y: x * 10 + y, digits) + 1
          return [int(n) for n in str(num)]  # or return list(map(int, str(num)))

        def plusOne1(self, digits: List[int]) -> List[int]:
          if digits == []: return [1]
          last = digits.pop()
          if last == 9:
            digits = self.plusOne(digits) + [0]
          else:
            digits.append(last + 1)
          return digits
    ```

#### 中等

1. [设计循环双端队列](https://leetcode.com/problems/design-circular-deque)

#### 困难

1. [接雨水](https://leetcode.com/problems/trapping-rain-water/)

### 下周预习

#### 预习题目

1. [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/description/)
2. [二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)
3. [最小的 k 个数](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)
