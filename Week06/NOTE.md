# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第六周](#第六周)
    - [第 12 课 | 动态规划](#第-12-课--动态规划)
      - [动态规划的实现及关键点](#动态规划的实现及关键点)
        - [动态规划关键点](#动态规划关键点)
        - [参考链接](#参考链接)

## 第六周

### 第 12 课 | 动态规划

#### 动态规划的实现及关键点

##### 动态规划关键点

1. 最优子结构 `opt[n] = best_of(opt[n - 1],opt[n - 2], ...)`
2. 储存中间状态：`opt[i]`
3. 递推公式（美其名曰：状态转移方程或者 DP 方程）
   1. `Fib: opt[i] = opt[n - 1] + opt[n - 2]`
   2. 二维路径：`opt[i, j] = opt[i + 1][j] + opt[i][j + 1]`（且判断 `a[i, j]` 是否空地）

##### 参考链接

1. [递归代码模板](https://shimo.im/docs/EICAr9lRPUIPHxsH)
2. [分支代码模板](https://shimo.im/docs/zvlDqLLMFvcAF79A)
3. [动态规划定义](https://en.wikipedia.org/wiki/Dynamic_programming)
