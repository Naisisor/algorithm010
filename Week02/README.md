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
    - [作业](#作业)
      - [简单](#简单)
      - [中等](#中等)
    - [下周作业](#下周作业)
      - [预习题](#预习题)

## 第二周

### 第 5 课 | 哈希表、映射、集合

#### 哈希表、映射、集合的实现与特性

待补充.....

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
- 思考题
  - 树的面试题解法一般都是递归，为什么？

#### 实战题目解析

### 第 6 课 | 堆和二叉堆、图

#### 堆和二叉堆的实现和特性

#### 实战题目解析

### 作业

#### 简单

1. 写一个关于 HashMap 的小总结。(Java)
2. [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/description/)
3. [两数之和](https://leetcode-cn.com/problems/two-sum/description/)

    ```py
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
5. 自学 [HeapSort](https://www.geeksforgeeks.org/heap-sort/)

#### 中等

1. [字母异位词分组](https://leetcode-cn.com/problems/group-anagrams/)
2. [二叉树的中序遍历](https://leetcode-cn.com/problems/binary-tree-inorder-traversal/)
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
