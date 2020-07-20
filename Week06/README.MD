# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第六周](#第六周)
    - [第 12 课 | 动态规划](#第-12-课--动态规划)
      - [动态规划的实现及关键点](#动态规划的实现及关键点)
        - [动态规划关键点](#动态规划关键点)
        - [参考链接](#参考链接)
      - [实战题目解析](#实战题目解析)
    - [作业](#作业)
      - [中等](#中等)
      - [困难](#困难)
    - [下周预习](#下周预习)
      - [预习题目](#预习题目)

## 第六周

### 第 12 课 | 动态规划

#### 动态规划的实现及关键点

##### 动态规划关键点

1. 最优子结构 `opt[n] = best_of(opt[n - 1],opt[n - 2], ...)`
2. 储存中间状态：`opt[i]`
3. 地推懂事（美其名曰：状态转移方程或者 DP 方程）
   1. `Fib: opt[i] = opt[n - 1] + opt[n - 2]`
   2. 二维路径：`opt[i, j] = opt[i + 1][j] + opt[i][j + 1]`（且判断 `a[i, j]` 是否空地）

##### 参考链接

1. [递归代码模板](https://shimo.im/docs/EICAr9lRPUIPHxsH)
2. [分支代码模板](https://shimo.im/docs/zvlDqLLMFvcAF79A)
3. [动态规划定义](https://en.wikipedia.org/wiki/Dynamic_programming)

#### 实战题目解析

### 作业

#### 中等

1. [最小路径和](https://leetcode-cn.com/problems/minimum-path-sum/)
2. [解码方法](https://leetcode-cn.com/problems/decode-ways)
3. [最大正方形](https://leetcode-cn.com/problems/maximal-square/)
4. [任务调度器](https://leetcode-cn.com/problems/task-scheduler/)
5. [回文子串](https://leetcode-cn.com/problems/palindromic-substrings/)

#### 困难

1. [最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)
2. [编辑距离](https://leetcode-cn.com/problems/edit-distance/)
3. [矩形区域不超过 K 的最大数值和](https://leetcode-cn.com/problems/max-sum-of-rectangle-no-larger-than-k/)
4. [青蛙过河](https://leetcode-cn.com/problems/frog-jump/)
5. [分割数组的最大值](https://leetcode-cn.com/problems/split-array-largest-sum)
6. [学生出勤记录 II](https://leetcode-cn.com/problems/student-attendance-record-ii/)
7. [最小覆盖子串](https://leetcode-cn.com/problems/minimum-window-substring/)
8. [戳气球](https://leetcode-cn.com/problems/burst-balloons/)

### 下周预习

#### 预习题目

1. [实现 Trie (前缀树)](https://leetcode-cn.com/problems/implement-trie-prefix-tree/#/description)
2. [单词搜索 II](https://leetcode-cn.com/problems/word-search-ii/)
3. [岛屿数量](https://leetcode-cn.com/problems/number-of-islands/)
4. [有效的数独](https://leetcode-cn.com/problems/valid-sudoku/description/)
5. [N 皇后](https://leetcode-cn.com/problems/n-queens/)
6. [单词接龙](https://leetcode-cn.com/problems/word-ladder/)
7. [二进制矩阵中的最短路径](https://leetcode-cn.com/problems/shortest-path-in-binary-matrix/)
