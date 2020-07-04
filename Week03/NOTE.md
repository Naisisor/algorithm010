# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第三周](#第三周)
    - [第 7 课 | 泛型递归、树的递归](#第-7-课--泛型递归树的递归)
      - [递归的实现、特性以及思维要点](#递归的实现特性以及思维要点)
      - [实战题目解析](#实战题目解析)
      - [每日一课](#每日一课)
    - [第 8 课 | 分治、回溯](#第-8-课--分治回溯)
      - [分治、回溯的实现和特性](#分治回溯的实现和特性)
        - [分治](#分治)
        - [回溯](#回溯)
      - [实战题目解析](#实战题目解析-1)

## 第三周

### 第 7 课 | 泛型递归、树的递归

#### 递归的实现、特性以及思维要点

- 递归（Recursion）

  - 递归 - 循环
  - 通过函数体来进行的循环
  - [递归代码模板](https://shimo.im/docs/EICAr9lRPUIPHxsH/)

    ```Python
    # Python
    def recursion(level, param1, param2, *args):
        # recursion terminator
        if level > MAX_LEVEL:
            process_result
            return

        # process logic in current level
        process(level, data, *args)

        # drill down
        recursion(level + 1, p1, *args)

        # reverse the current level status if needed
    ```

    ```JAVA
    // Java
    public void recur(int level, int param) {
      // terminator
      if (level > MAX_LEVEL) {
        // process result
        return;
      }
      // process current logic
      process(level, param);
      // drill down
      recur( level: level + 1, newParam);
      // restore current status

    }
    ```

- 思维要点
  1. 不要人肉进行递归（最大误区）
  2. 找到最近最简方法、将其拆解成可重复解决的问题（重复子问题）
  3. 数学归纳法思维

#### 实战题目解析

1. [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)
2. [括号生成](https://leetcode-cn.com/problems/generate-parentheses/)
3. [翻转二叉树](https://leetcode-cn.com/problems/invert-binary-tree/description/)
4. [验证二叉搜索树](https://leetcode-cn.com/problems/validate-binary-search-tree)
5. [二叉树的最大深度](https://leetcode-cn.com/problems/maximum-depth-of-binary-tree)
6. [二叉树的最好深度](https://leetcode-cn.com/problems/minimum-depth-of-binary-tree)
7. [二叉树的序列化与反序列化](https://leetcode-cn.com/problems/serialize-and-deserialize-binary-tree/)

#### 每日一课

- [如何优雅地计算斐波那契数列](https://time.geekbang.org/dailylesson/detail/100028406)

### 第 8 课 | 分治、回溯

#### 分治、回溯的实现和特性

> 分治和回溯本质上都是递归，可以把它们认为是递归的一种新的分类

##### 分治

- [分治代码模板](https://shimo.im/docs/zvlDqLLMFvcAF79A/read)

  ```Python
  # Python
  def divide_conquer(problem, param1, param2, ...):
      # recursion terminator
      if problem is None:
        print_result
        return
      # prepare data
      data = prepare_data(problem)
      subproblems = split_problem(problem, data)
      # conquer subproblems
      subresult1 = self.divide_conquer(subproblems[0], p1, ...)
      subresult2 = self.divide_conquer(subproblems[1], p1, ...)
      subresult3 = self.divide_conquer(subproblems[2], p1, ...)
      …
      # process and generate the final result
      result = process_result(subresult1, subresult2, subresult3, …)

      # revert the current level states
  ```

##### 回溯

- 回溯法采用试错的思想，它尝试分布的去解决一个问题。在分步解决问题的过程中，当它通过尝试发现现有的分步答案不能得到有效的正确的解答的时候，它将取消上一步甚至是上几步的计算，在通过其他的可能的分布解答再次尝试寻找问题的答案。
- 回溯法通常用最简单的递归方法来实现，在反复重复上述的步骤后可能出现两种情况：
  1. 找到一个可能存在的正确答案。
  2. 在尝试了所有可能的分布方法后宣告该问题没有答案。
     **在最坏的情况下，回溯法会导致一次复杂为指数时间的计算。**

#### 实战题目解析

1. [Pow(x, n) ](https://leetcode-cn.com/problems/powx-n/)
2. [子集](https://leetcode-cn.com/problems/subsets/)
3. [多数元素](https://leetcode-cn.com/problems/majority-element/description/)
4. [电话号码的字母组合](https://leetcode-cn.com/problems/letter-combinations-of-a-phone-number/)
5. [N 皇后](https://leetcode-cn.com/problems/n-queens/)
