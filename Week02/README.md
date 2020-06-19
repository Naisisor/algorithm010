# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第二周](#第二周)
    - [第 5 课 | 哈希表、映射、集合](#第-5-课--哈希表映射集合)
      - [哈希表、映射、集合的实现与特性](#哈希表映射集合的实现与特性)
      - [实战题目解析](#实战题目解析)
    - [第 6 课 | 树、二叉树、二叉搜索树](#第-6-课--树二叉树二叉搜索树)
      - [树、二叉树、二叉搜索树的实现和特性](#树二叉树二叉搜索树的实现和特性)
      - [实战题目解析](#实战题目解析-1)
    - [第 6 课 | 堆和二叉堆、图](#第-6-课--堆和二叉堆图)
      - [堆和二叉堆的实现和特性](#堆和二叉堆的实现和特性)
      - [实战题目解析](#实战题目解析-2)
      - [图（了解）](#图了解)
    - [作业](#作业)
      - [简单](#简单)
      - [中等](#中等)
    - [下周作业](#下周作业)
      - [预习题](#预习题)

## 第二周

### 第 5 课 | 哈希表、映射、集合

#### 哈希表、映射、集合的实现与特性

- 哈希表（Hash Table）
  - 哈希表（Hash Table），也叫散列表，是根据关键码值（key value）而直接进行访问的数据，它通过把关键码值映射到表中一个位置来访问记录，以加快查找的速度。这个映射函数叫作散列函数（Hash Function），存放记录的数组叫哈希表（或散列表）
  - 工程实践：电话号码薄、用户信息表、缓存（LRU Cache）、键值对存储(Redis)等。

#### 实战题目解析

- [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/description/)
- [字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/)
- [两数之和](https://leetcode-cn.com/problems/two-sum/description/)

### 第 6 课 | 树、二叉树、二叉搜索树

#### 树、二叉树、二叉搜索树的实现和特性

- 树
  - 有环的树被称为图
- 二叉树
  - 二叉树遍历方式
    1. 前序（Pre-order）：根 - 左 - 右

        ```python
        # 示例代码
        def preorder(self, root):
            if root:
                self.traverse_path.append(root.val)
                self.preorder(root.left)
                self.preorder(root.right)
        ```

    2. 中序（In-order）：左 - 根 - 右

        ```python
        # 示例代码
        def inorder(self, root):
            if root:
                self.inorder(root.left)
                self.traverse_path.append(root.val)
                self.inorder(root.right)
        ```

    3. 后序（Post-order）：左 - 右 - 根

        ```python
        # 示例代码
        def postorder(self, root):
            if root:
                self.postorder(root.left)
                self.postorder(root.right)
                self.traverse_path.append(root.val)
        ```

- 二叉搜索树
  - 二叉搜索树，也称二叉排序树、有序二叉树（Ordered Binary Tree）、排序二叉树（Sorted Binary Tree），是指一颗空树或者具有下列性质 的二叉树。（空树就是二叉搜索树）
    1. 左子树上所有节点的值均小于它的根节点的值；
    2. 右子树上所有节点的值均大于它的根节点的值；
    3. 以此类推：左、右子树也分别为二叉查找树。（这就是重复性）
  - 中序遍历：升序排列
  - 常见操作
    1. 查询，时间复杂度 O(logn)
    2. 插入新节点（创建），时间复杂度 O(logn)
    3. 删除，时间复杂度 O(logn)
        **二叉搜索树的特点就是大部分的操作的时间复杂度都是 O(logn)**
- 其它
  - [树的遍历 Demo](https://visualgo.net/zh/bst)
  - [All DFS traversals (preorder, inorder, postorder) in Python in 1 line
](https://leetcode.com/problems/binary-tree-inorder-traversal/discuss/283746/All-DFS-traversals-(preorder-inorder-postorder)-in-Python-in-1-line)
- 思考题
  - 树的面试题解法一般都是递归，为什么？

#### 实战题目解析

### 第 6 课 | 堆和二叉堆、图

#### 堆和二叉堆的实现和特性

- 堆（Heap）
  - Heap：可以迅速找到一堆数中的最大或者最小值的数据结构物
  - 将根节点最大的堆叫做顶推或大根堆，根节点最小的堆叫做小顶堆或者小根堆。常见的堆有二叉堆、斐波那契堆等
  - 假设是大顶堆，则常见操作（API）：
    - find-max: O(1)
    - delete-max: O(logn)
    - insert(creat): O(logn) or O(1)
    - 不同实现的比较：[https://en.wikipedia.org/wiki/Heap_(data_structure)](https://en.wikipedia.org/wiki/Heap_(data_structure))
  - 参考链接
    - [维基百科：堆（Heap）](https://en.wikipedia.org/wiki/Heap_(data_structure))
    - 堆的实现代码: [https://shimo.im/docs/Lw86vJzOGOMpWZz2/]( https://shimo.im/docs/Lw86vJzOGOMpWZz2/)
- 二叉堆
  - 二叉堆是通过完全二叉树来实现（注意：不是二叉搜索树）
  - 二叉堆（大顶）它满足以下性质
    1. 是一颗完全树
    2. 树中任意节点的值总是 >= 其子节点的值
  - 二叉堆的实现细节
    1. 二叉堆一般都是通过 `数组` 来实现的
    2. 假设「第一个元素」 在数组中的索引未 0 的话，则父节点和子节点的位置关系如下：
       1. 索引为 `i` 的左孩子的索引为 `2 * i + 1`
       2. 索引为 `i` 的右孩子的索引为 `2 * i + 2`
       3. 索引为  `i` 的父节点的索引为 `floor((i - 1) / 2)`
  - 常用操作
    - Insert 插入操作，时间复杂度 O(logn)
      1. 新元素一律插入到堆的尾部
      2. 依次向上调整整个堆的结构（一直到根即可）HeapifyUp
    - Delete Max 删除堆顶操作
      1. 将堆尾元素替换到顶部（即堆顶被替换删除掉）
      2. 依次从根部向下调整整个堆的结构（一直到堆尾即可）HeapifyDown

#### 实战题目解析

1. [最小的 k 个数](https://leetcode-cn.com/problems/zui-xiao-de-kge-shu-lcof/)
2. [滑动窗口最大值](https://leetcode-cn.com/problems/sliding-window-maximum/)

#### 图（了解）

- 图的属性和分类：待补充......
- 基于图相关的算法：待补充......
- 参考链接
  1. [连通图个数](https://leetcode-cn.com/problems/number-of-islands/)
  2. [拓扑排序（Topological Sorting）](https://zhuanlan.zhihu.com/p/34871092)
  3. [最短路径（Shortest Path）：Dijkstra](https://www.bilibili.com/video/av25829980?from=search&seid=13391343514095937158)
  4. [最小生成树（Minimum Spanning Tree）](https://www.bilibili.com/video/av84820276?from=search&seid=17476598104352152051)

### 作业

#### 简单

1. 写一个关于 HashMap 的小总结（Java）。参考 [史上最全的Java容器集合之HashMap（源码解读）](https://juejin.im/post/5dedb448f265da33b071716a)
2. [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/description/)

    ```python
    class Solution:
        def isAnagram(self, s: str, t: str) -> bool:
            return sorted(s) == sorted(t)

        def isAnagram1(self, s: str, t: str) -> bool:
            d = {} # d = collections.defaultdict(int)
            for _s in s:
                d[_s] = d.get(_s, 0) + 1
            for _t in t:
                if _t not in d:
                    return False
                d[_t] -= 1
            return not any(d.values())

        def isAnagram2(self, s: str, t: str) -> bool:
            return collections.Counter(s) == collections.Counter(t)
    ```

3. [两数之和](https://leetcode-cn.com/problems/two-sum/description/)

    ```python
    class Solution:
        def twoSum(self, nums: List[int], target: int) -> List[int]:
            # hash，O(n)
            d = {}
            for i, n in enumerate(nums):
                if target - n in d:
                    return [d[target - n], i]
                d[n] = i
            return []
    ```

4. [N 叉树的前序遍历](https://leetcode-cn.com/problems/n-ary-tree-preorder-traversal/description/)

    ```python
    """
    # Definition for a Node.
    class Node:
        def __init__(self, val=None, children=None):
            self.val = val
            self.children = children
    """

    class Solution:
        def preorder(self, root: 'Node') -> List[int]:
            # 递归
            if not root:
                return []
            res = [root.val]
            for child in root.children:
                res.extend(seld.preorder(child))
            return res
            # 或者，用一行代码搞定
            # return root and sum([[root.val], *map(self.preorder, root.children)], [])

        def preorder1(self, root: 'Node') -> List[int]:
            # 迭代
            res, stack = [], root and [root]
            while stack:
                node = stack.pop()
                res.append(node.val)
                stack.extend(reversed(node.children))
            return res
    ```

5. 自学 [HeapSort](https://www.geeksforgeeks.org/heap-sort/)

#### 中等

1. [字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/)

    ```python
    class Solution:
        def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
            # hash，O(n)
            d = collections.defaultdict(list)
            for s in strs:
                key = ''.join(sorted(s))
                d[key].append(s)
            return list(d.values())
    ```

2. [二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)

    ```python
    # Definition for a binary tree node.
    # class TreeNode:
    #     def __init__(self, x):
    #         self.val = x
    #         self.left = None
    #         self.right = None

    class Solution:
        def inorderTraversal(self, root: TreeNode) -> List[int]:
            # 递归
            if not root:
                return []
            res = []
            res.extend(self.inorderTraversal(root.left))
            res.append(root.val)
            res.extend(self.inorderTraversal(root.right))
            return res

        def inorderTraversal1(self, root: TreeNode) -> List[int]:
            # 迭代
            ans, stack = [], []
            while stack or root:
                if root:
                    stack.append(root)
                    root = root.left
                else:
                    __root = stack.pop()
                    ans.append(__root.val)
                    root = __root.right
            return ans
    ```

3. [二叉树的前序遍历](https://leetcode-cn.com/problems/binary-tree-preorder-traversal/)
4. [N 叉树的层序遍历](https://leetcode-cn.com/problems/n-ary-tree-level-order-traversal/)
5. [丑数](https://leetcode-cn.com/problems/chou-shu-lcof/)
6. [前 K 个高频元素](https://leetcode-cn.com/problems/top-k-frequent-elements/)

### 下周作业

#### 预习题

1. [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)
2. [括号生成](https://leetcode-cn.com/problems/generate-parentheses/)
3. [Pow(x, n)](https://leetcode-cn.com/problems/powx-n/)
4. [子集](https://leetcode-cn.com/problems/subsets/)
5. [N 皇后](https://leetcode-cn.com/problems/n-queens/)
