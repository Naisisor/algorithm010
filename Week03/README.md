# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第三周](#第三周)
    - [第 7 课 | 泛型递归、树的递归](#第-7-课--泛型递归树的递归)
      - [递归的实现、特性以及思维要点](#递归的实现特性以及思维要点)

## 第三周

### 第 7 课 | 泛型递归、树的递归

#### 递归的实现、特性以及思维要点

- 递归（Recursion）

  - 递归 - 循环
  - 通过函数体来进行的循环
  - 递归代码模板

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
        self.recursion(level + 1, p1, *args)

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
