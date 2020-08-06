# Table of Contents

- [Table of Contents](#table-of-contents)
  - [第 9 周](#第-9-周)
    - [第 19 课 | 高级动态规划](#第-19-课--高级动态规划)
      - [动态规划、状态转移方程串讲](#动态规划状态转移方程串讲)
      - [高级动态规划题目详解](#高级动态规划题目详解)
    - [第 20 课 | 字符串算法](#第-20-课--字符串算法)
      - [字符串基础知识和引申问题](#字符串基础知识和引申问题)
      - [高级字符串算法](#高级字符串算法)
      - [字符串匹配算法](#字符串匹配算法)
        - [Rabin-Karp 算法](#rabin-karp-算法)
        - [KMP 算法](#kmp-算法)
        - [参考链接](#参考链接)
    - [作业](#作业)
      - [简单](#简单)
      - [中等](#中等)
      - [困难](#困难)

## 第 9 周

### 第 19 课 | 高级动态规划

#### 动态规划、状态转移方程串讲

#### 高级动态规划题目详解

### 第 20 课 | 字符串算法

#### 字符串基础知识和引申问题

#### 高级字符串算法

#### 字符串匹配算法

##### Rabin-Karp 算法

在朴素算法中，我们需要挨个比较所有字符，才知道目标字符串中是否包含 子串。那么， 是否有别的方法可以用来判断目标字符串是否包含子串呢?
答案是肯定的，确实存在一种更快的方法。为了避免挨个字符对目标字符串 和子串进行比较， 我们可以尝试一次性判断两者是否相等。因此，我们需 要一个好的哈希函数(hash function)。 通过哈希函数，我们可以算出子 串的哈希值，然后将它和目标字符串中的子串的哈希值进行比较。 这个新 方法在速度上比暴力法有显著提升。

Rabin-Karp 算法的思想:

1. 假设子串的长度为 M (pat)，目标字符串的长度为 N (txt)
2. 计算子串的 hash 值 hash_pat
3. 计算目标字符串 txt 中每个长度为 M 的子串的 hash 值(共需要计算 N-M+1 次)
4. 比较 hash 值:如果 hash 值不同，字符串必然不匹配; 如果 hash 值相同， 还需要使用朴素算法再次判断

##### KMP 算法

KMP 算法(Knuth-Morris-Pratt)的思想就是，当子串与目标字符串不匹配时， 其实你已经知道了前面已经匹配成功那 一部分的字符(包括子串与目标字符 串)。以阮一峰的文章为例，当空格与 D 不匹配时，你其实 知道前面六个字符是 “ABCDAB”。KMP 算法的想法是，设法利用这个已知信息，不要把“搜索位
置” 移回已经比较过的位置，继续把它向后移，这样就提高了效率。

##### 参考链接

1. [KMP 字符串匹配算法 1](https://www.bilibili.com/video/av11866460?from=search&seid=17425875345653862171)
2. [字符串匹配的 KMP 算法](http://www.ruanyifeng.com/blog/2013/05/Knuth%E2%80%93Morris%E2%80%93Pratt_algorithm.html)

### 作业

#### 简单

1. [字符串中的第一个唯一字符](https://leetcode-cn.com/problems/first-unique-character-in-a-string/)

   ```Python
   class Solution:
       def firstUniqChar(self, s: str) -> int:
           d = collections.defaultdict(int)
           for char in s:
               d[char] += 1
           for i, char in enumerate(s):
               if d[char] != 1:
                   continue
               return i
           return -1

       def firstUniqChar1(self, s: str) -> int:
           d = collections.Counter(s)
           for i, char in enumerate(s):
               if d[char] != 1:
                   continue
               return i
           return -1

       def firstUniqChar3(self, s: str) -> int:
           d = collections.Counter(s)
           for k, v in d.items():
               if v != 1: continue
               return s.index(k)
           return -1
   ```

2. [反转字符串 II ](https://leetcode-cn.com/problems/reverse-string-ii/)

```Python
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        if len(s) <= k:
            return s[::-1]
        l, r = 0, len(s)
        ans = ''
        while l <= r:
            ans += s[l:l + k][::-1] + s[l + k:l + 2 * k]
            l += 2 * k
        return ans

    def reverseStr1(self, s: str, k: int) -> str:
        s = list(s)
        for i in range(0, len(s), 2 * k):
            s[i:i + k] = reversed(s[i:i + k])
        return ''.join(s)
```

3. [翻转字符串里的单词](https://leetcode-cn.com/problems/reverse-words-in-a-string/)
4. [反转字符串中的单词 III ](https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/)
5. [仅仅反转字母](https://leetcode-cn.com/problems/reverse-only-letters/)

   ```Python
   class Solution:
       def reverseOnlyLetters(self, S: str) -> str:
           l, r = 0, len(S) - 1
           s = [char for char in S]
           while l < r:
               while l < r and not s[l].isalpha(): l += 1
               while l < r and not s[r].isalpha(): r -= 1
               s[l], s[r] = s[r], s[l]
               l += 1
               r -= 1
           return ''.join(s)
   ```

6. [同构字符串](https://leetcode-cn.com/problems/isomorphic-strings/)
7. [验证回文字符串 Ⅱ](https://leetcode-cn.com/problems/valid-palindrome-ii/)

   ```Python
   class Solution:
       def validPalindrome(self, s: str) -> bool:
           l, r = 0, len(s) - 1
           while l <= r:
               if s[l] != s[r]:
                   return s[l + 1:r + 1] == s[l + 1:r + 1][::-1] or s[l:r] == s[l:r][::-1]
               l += 1
               r -= 1
           return True
   ```

#### 中等

1. 在学习总结中，写出不同路径 2 这道题目的状态转移方程。
2. [最长上升子序列](https://leetcode-cn.com/problems/longest-increasing-subsequence/)
3. [解码方法](https://leetcode-cn.com/problems/decode-ways/)
4. [字符串转换整数 (atoi) ](https://leetcode-cn.com/problems/string-to-integer-atoi/)
5. [找到字符串中所有字母异位词](https://leetcode-cn.com/problems/find-all-anagrams-in-a-string/)
6. [最长回文子串](https://leetcode-cn.com/problems/longest-palindromic-substring/)

#### 困难

1. [最长有效括号](https://leetcode-cn.com/problems/longest-valid-parentheses/)

   ```Python
   class Solution:
       def longestValidParentheses(self, s: str) -> int:
           dp, stack = [0] * (len(s) + 1), []
           for i, p in enumerate(s):
               if p == '(':
                   stack.append(i)
               else:
                   if stack:
                       k = stack.pop()
                       dp[i + 1] = dp[k] + i - k + 1
           return max(dp)

       def longestValidParentheses(self, s: str) -> int:
           ans, stack = 0, [-1]
           for i, p in enumerate(s):
               if p == '(':
                   stack.append(i)
               elif len(stack) > 1:
                   stack.pop()
                   ans = max(ans, i - stack[-1])
               else:
                   stack[0] = i
           return ans
   ```

2. [赛车](https://leetcode-cn.com/problems/race-car/)
3. [通配符匹配](https://leetcode-cn.com/problems/wildcard-matching/)
4. [不同的子序列](https://leetcode-cn.com/problems/distinct-subsequences/)
