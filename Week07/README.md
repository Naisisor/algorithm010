# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第 7 周](#第-7-周)
    - [第 13 课 | 字典树和并查集](#第-13-课--字典树和并查集)
      - [字典树 Trie](#字典树-trie)
        - [字典树的数据结构](#字典树的数据结构)
        - [字典树的核心思想](#字典树的核心思想)
        - [字典树的基本性质](#字典树的基本性质)
        - [参考链接](#参考链接)
    - [第 14 课 | 高级搜索](#第-14-课--高级搜索)
      - [剪枝的实现和特性](#剪枝的实现和特性)
    - [第 15 课 | 红黑树和 AVL 树](#第-15-课--红黑树和-avl-树)
      - [AVL 树和红黑树的实现与特性](#avl-树和红黑树的实现与特性)
        - [AVL](#avl)
        - [红黑树](#红黑树)
        - [参考链接](#参考链接-1)
    - [作业](#作业)
      - [简单](#简单)
      - [中等](#中等)
      - [困难](#困难)
    - [下周预习](#下周预习)
      - [预习题](#预习题)

## 第 7 周

### 第 13 课 | 字典树和并查集

#### 字典树 Trie

##### 字典树的数据结构

字典树，即 `Trie` 树，又称单词查找树或键树，是一种树行的结构。典型应用是用于统计和排序大量的字符串（但不仅限于字符串），所以经常被搜索引擎系统用于文本词频统计

优点：最大限度的减少无谓的字符串比较，查询效率比哈希表高

##### 字典树的核心思想

Trie 树的核心思想是空间换时间

利用字符串的公共前缀来降低查询时间的开销已达到提高效率的目的

##### 字典树的基本性质

1. 节点本身不存完整单词
2. 从根节点到某一节点，路径上经过的字符连接起来，为改节点的字符串
3. 每个节点的所有子节点路径代表的字符都不相同

##### 参考链接

1. [二叉树的层次遍历](https://leetcode-cn.com/problems/binary-tree-level-order-traversal/)
2. [实现 Trie](https://leetcode-cn.com/problems/implement-trie-prefix-tree/solution/)
3. [Tire 树代码模板](https://shimo.im/docs/DP53Y6rOwN8MTCQH)

### 第 14 课 | 高级搜索

#### 剪枝的实现和特性

### 第 15 课 | 红黑树和 AVL 树

#### AVL 树和红黑树的实现与特性

##### AVL

##### 红黑树

红黑树是 `近似平衡` 的二叉搜索树（Binary Search Tree），它能确保任何一个结点的左右子树的 `高度差小于两倍`。具体来说，黑红树是满足以下条件的二叉搜索树：

1. 每个结点要么是红色，要么是黑色
2. 根节点是黑色
3. 每个叶结点（NIL 结点，空节点）是黑色
4. 不能有相邻的两个红色结点
5. 从任一结点到其每个叶子的所有路径都包含相同数目的黑色节点

##### 参考链接

- [平衡树](https://en.wikipedia.org/wiki/Self-balancing_binary_search_tree)

### 作业

#### 简单

- [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)

  ```Python
  class Solution:
      def climbStairs(self, n: int) -> int:
          if n <= 2:
              return n
          f1, f2, f3 = 1, 2, 0
          for n in range(2, n):
              f3 = f1 + f2
              f1, f2 = f2, f1 + f2
          return f3
  ```

#### 中等

1. [实现 Trie (前缀树) ](https://leetcode-cn.com/problems/implement-trie-prefix-tree/#/description)
2. [朋友圈](https://leetcode-cn.com/problems/friend-circles)
3. [岛屿数量](https://leetcode-cn.com/problems/number-of-islands/)
4. [被围绕的区域](https://leetcode-cn.com/problems/surrounded-regions/)
5. [有效的数独](https://leetcode-cn.com/problems/valid-sudoku/description/)
6. [括号生成](https://leetcode-cn.com/problems/generate-parentheses/)

   ```Python
   class Solution:
       def generateParenthesis(self, n: int) -> List[str]:
           ans = []
           def _generate(left, right, s):
               if left == n and right == n:
                   ans.append(s)
                   return
               if left < n:
                   _generate(left + 1, right, s + '(')
               if right < left:
                   _generate(left, right + 1, s + ')')
           _generate(0, 0, '')
           return ans
   ```

7. [单词接龙](https://leetcode-cn.com/problems/word-ladder/)
8. [最小基因变化](https://leetcode-cn.com/problems/minimum-genetic-mutation/)

#### 困难

1. [单词搜索 II ](https://leetcode-cn.com/problems/word-search-ii/)
2. [N 皇后](https://leetcode-cn.com/problems/n-queens/)
3. [解数独](https://leetcode-cn.com/problems/sudoku-solver/#/description)

### 下周预习

#### 预习题

1. [LRU 缓存机制](https://leetcode-cn.com/problems/lru-cache/#/)
2. [有效的字母异位词](https://leetcode-cn.com/problems/valid-anagram/)
