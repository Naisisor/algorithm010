# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第四周](#第四周)
    - [第 9 课 | 深度优先搜索和广度优先搜索](#第-9-课--深度优先搜索和广度优先搜索)
      - [深度优先搜索和广度优先搜索的实现和特性](#深度优先搜索和广度优先搜索的实现和特性)
      - [实战题目解析](#实战题目解析)
    - [第 10 课 | 贪心算法](#第-10-课--贪心算法)
      - [贪心算法的实现、特性](#贪心算法的实现特性)
      - [实战题目解析](#实战题目解析-1)
    - [第 11 课 | 二分查找](#第-11-课--二分查找)
      - [二分查找的实现、特性](#二分查找的实现特性)
      - [实战题目](#实战题目)
  - [作业](#作业)
    - [简单](#简单)
    - [中等](#中等)
    - [困难](#困难)
  - [第 6 周预习](#第-6-周预习)
    - [预习题目](#预习题目)

## 第四周

### 第 9 课 | 深度优先搜索和广度优先搜索

#### 深度优先搜索和广度优先搜索的实现和特性

- 搜索 - 遍历
  - 每个节点都要访问一次
  - 每个节点仅访问一下
  - 对于节点的访问顺序不限
    - 深度优先：depth first search
    - 广度优先：breadth first search
- [DFS 代码模板](https://shimo.im/docs/UdY2UUKtliYXmk8t/)

  ```Python
  # Python
  # 递归写法（二叉树）
  def dfs(node):
    if node in visited:
      # already visited
      return
    visited.add(node)

    # process current node
    # ... # logic here

    dfs(node.left)
    dfs(node.right)

  # 递归写法（多叉树）
  visited = set()
  def dfs(node, visited):
      if node in visited: # terminator
        # already visited
        return
    visited.add(node)
    # process current node here.
    ...
    for next_node in node.children():
      if next_node not in visited:
        dfs(next_node, visited)

  # 非递归写法
  def DFS(self, tree):
    if tree.root is None:
      return []
    visited, stack = [], [tree.root]
    while stack:
      node = stack.pop()
      visited.add(node)
      process (node)
      nodes = generate_related_nodes(node)
      stack.push(nodes)
    # other processing work
    ...
  ```

- [BFS 代码模板](https://shimo.im/docs/ZBghMEZWix0Lc2jQ/)

  ```Python
  # Python
  def BFS(graph, start, end):
      visited = set()
    queue = []
    queue.append([start])
    while queue:
      node = queue.pop()
      visited.add(node)
      process(node)
      nodes = generate_related_nodes(node)
      queue.push(nodes)
    # other processing work
    ...
  ```

#### 实战题目解析

1. [二叉树的层序遍历](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/#/description)
2. [最小基因变化](https://leetcode-cn.com/problems/minimum-genetic-mutation/#/description)
3. [括号生成](https://leetcode-cn.com/problems/generate-parentheses/#/description)
4. [在每个树行中找最大值](https://leetcode-cn.com/problems/find-largest-value-in-each-tree-row/#/description)

### 第 10 课 | 贪心算法

#### 贪心算法的实现、特性

- 贪心算法 Greedy
  - 贪心算法是一种在每一步选择中都采取在当前状态下最好或最优（即最有利）的选择，从而希望导致结果是全局最好或最优的算法
  - 贪心算法与动态规划的不同在于它对每个子问题的解决方案都是做出选择不能回退。动态规划会保存以前的运算结果，并根据以前的结果对当前进行选择，有回退功能
  - 贪心法可以解决一些最优化问题，如：求图中的最小生成树、求哈夫曼编码等。然而对于工程和生活中的问题，贪心法一般不能得到我们所要求的答案。
  - 一旦一个问题可以通过贪心法来解决，那么贪心法一般是解决这个问题的最好办法。由于贪心法的高效性以及其所求得的答案比较接近最优结果，贪心法也可用作辅佐算法或者直接解决一些要求结果不特别精确的问题。
- 贪心算法的适用场景
  - 简单地说，问题能够分解成子问题来解决，子问题的最优解能递推到最终问题的最优解。这种子问题最优解称为最优子结构。
  - 贪心算法与 [动态规划](https://zh.wikipedia.org/wiki/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92) 的不同在于它对每个子问题的解决方案都是做出选择，不能回退。动态规化则会保存以前的远算结果，并根据以前的结果对当前的进行选择，有回退功能。

#### 实战题目解析

### 第 11 课 | 二分查找

#### 二分查找的实现、特性

- 二分查找的前提条件
  1. 目标函数单调性（单调递增或者递减）
  2. 存在上下界（bounded）
  3. 能够通过索引访问（index accessible）
- 参考链接

  - [Fast InvSqrt() 扩展阅读](https://www.beyond3d.com/content/articles/8/)
  - [二分查找代码模板](https://shimo.im/docs/xvIIfeEzWYEUdBPD/read)

    ```Python
    # Python
    def binary_search(nums, target):
        left, right = len(nums) - 1
        while left <= right:
            mid = (left + right) / 2
            if nums[mid] == target:
                # find the target
                break or return result
            elif nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1
    ```

#### 实战题目

1. [x 的平方根](https://leetcode-cn.com/problems/sqrtx/)
2. [有效的完全平方数](https://leetcode-cn.com/problems/valid-perfect-square/)

## 作业

### 简单

1. [柠檬水找零](https://leetcode-cn.com/problems/lemonade-change/description/)
2. [买卖股票的最佳时机 II](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/description/)
3. [分发饼干](https://leetcode-cn.com/problems/assign-cookies/description/)
4. [模拟行走机器人](https://leetcode-cn.com/problems/walking-robot-simulation/description/)
5. 使用二分查找，寻找一个半有序数组 [4, 5, 6, 7, 0, 1, 2] 中间无序的地方

### 中等

1. [单词接龙](https://leetcode-cn.com/problems/word-ladder/description/)
2. [岛屿数量](https://leetcode-cn.com/problems/number-of-islands/)
3. [扫雷游戏](https://leetcode-cn.com/problems/minesweeper/description/)
4. [跳跃游戏](https://leetcode-cn.com/problems/jump-game/)

   ```Python
   class Solution:
       def canJump(self, nums: List[int]) -> bool:
           if not nums:
             return False
           end_reachble = len(nums) - 1
           for i in range(len(nums) - 1, -1, -1):
             if nums[i] + i >= end_reachble:
                 end_reachble = i
           return end_reachble == 0
   ```

5. [搜索旋转排序数组](https://leetcode-cn.com/problems/search-in-rotated-sorted-array/)

   ```Python
   class Solution:
       def search(self, nums: List[int], target: int) -> int:
           # 暴力求解，时间复杂度 O(n)
           for i, n in enumerate(nums):
               if n == target:
                 return i
           else:
               return -1

       def search1(self, nums: List[int], target: int) -> int:
           # 二分法查找，时间复杂度 O(logn)
           if len(nums) == 0: return -1
           left, right = 0, len(nums) - 1
           while left <= right:
               mid = (left + right) // 2
               if nums[mid] == target: return mid
               if nums[0] <= target < nums[mid] or target < nums[mid] < nums[0] or nums[mid] < nums[0] <= target:
                   right = mid - 1
               else:
                   left = mid + 1
           return -1
   ```

6. [搜索二维矩阵](https://leetcode-cn.com/problems/search-a-2d-matrix/)
7. [寻找旋转排序数组中的最小值](https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/)

### 困难

1. [单词接龙 II](https://leetcode-cn.com/problems/word-ladder-ii/description/)
2. [跳跃游戏 II](https://leetcode-cn.com/problems/jump-game-ii/)

## 第 6 周预习

### 预习题目

1. [最长公共子序列题目](https://leetcode-cn.com/problems/longest-common-subsequence/)
2. [三角形最小路径和](https://leetcode-cn.com/problems/triangle/description/)
3. [最大子序和](https://leetcode-cn.com/problems/maximum-subarray/)
4. [打家劫舍](https://leetcode-cn.com/problems/house-robber/)
