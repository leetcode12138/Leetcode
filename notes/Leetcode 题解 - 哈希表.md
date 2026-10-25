# Leetcode 题解 - 哈希表

> 原作者：[CyC2018](https://github.com/CyC2018) 及 CS-Notes 贡献者。来源：[CS-Notes 原文](https://github.com/CyC2018/CS-Notes/blob/9b262ea010f453d1d53088604ac472a7b7d6e957/notes/Leetcode%20%E9%A2%98%E8%A7%A3%20-%20%E5%93%88%E5%B8%8C%E8%A1%A8.md)。
> 本页保留原文分类、题目、示例和文字解析，移除了实现代码和图片；采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可。

<!-- GFM-TOC -->
* [Leetcode 题解 - 哈希表](#leetcode-题解---哈希表)
    * [1. 数组中两个数的和为给定值](#1-数组中两个数的和为给定值)
    * [2. 判断数组是否含有重复元素](#2-判断数组是否含有重复元素)
    * [3. 最长和谐序列](#3-最长和谐序列)
    * [4. 最长连续序列](#4-最长连续序列)
    * [5. 和为 K 的子数组](#5-和为-k-的子数组)
<!-- GFM-TOC -->


哈希表使用 O(N) 空间复杂度存储数据，并且以 O(1) 时间复杂度求解问题。

- Java 中的   **HashSet**   用于存储一个集合，可以查找元素是否在集合中。如果元素有穷，并且范围不大，那么可以用一个布尔数组来存储一个元素是否存在。例如对于只有小写字符的元素，就可以用一个长度为 26 的布尔数组来存储一个字符集合，使得空间复杂度降低为 O(1)。

- Java 中的   **HashMap**   主要用于映射关系，从而把两个元素联系起来。HashMap 也可以用来对元素进行计数统计，此时键为元素，值为计数。和 HashSet 类似，如果元素有穷并且范围不大，可以用整型数组来进行统计。在对一个内容进行压缩或者其它转换时，利用 HashMap 可以把原始内容和转换后的内容联系起来。例如在一个简化 url 的系统中 [Leetcdoe : 535. Encode and Decode TinyURL (Medium)

[Leetcode](https://leetcode.com/problems/encode-and-decode-tinyurl/description/)，利用 HashMap 就可以存储精简后的 url 到原始 url 的映射，使得不仅可以显示简化的 url，也可以根据简化的 url 得到原始 url 从而定位到正确的资源�) / [力扣](https://leetcode-cn.com/problems/encode-and-decode-tinyurl/description/)，利用 HashMap 就可以存储精简后的 url 到原始 url 的映射，使得不仅可以显示简化的 url，也可以根据简化的 url 得到原始 url 从而定位到正确的资源�)


## 1. 数组中两个数的和为给定值

1\. Two Sum (Easy)

[Leetcode](https://leetcode.com/problems/two-sum/description/) / [力扣](https://leetcode-cn.com/problems/two-sum/description/)

可以先对数组进行排序，然后使用双指针方法或者二分查找方法。这样做的时间复杂度为 O(NlogN)，空间复杂度为 O(1)。

用 HashMap 存储数组元素和索引的映射，在访问到 nums[i] 时，判断 HashMap 中是否存在 target - nums[i]，如果存在说明 target - nums[i] 所在的索引和 i 就是要找的两个数。该方法的时间复杂度为 O(N)，空间复杂度为 O(N)，使用空间来换取时间。


## 2. 判断数组是否含有重复元素

217\. Contains Duplicate (Easy)

[Leetcode](https://leetcode.com/problems/contains-duplicate/description/) / [力扣](https://leetcode-cn.com/problems/contains-duplicate/description/)


## 3. 最长和谐序列

594\. Longest Harmonious Subsequence (Easy)

[Leetcode](https://leetcode.com/problems/longest-harmonious-subsequence/description/) / [力扣](https://leetcode-cn.com/problems/longest-harmonious-subsequence/description/)

```html
Input: [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].
```

和谐序列中最大数和最小数之差正好为 1，应该注意的是序列的元素不一定是数组的连续元素。


## 4. 最长连续序列

128\. Longest Consecutive Sequence (Hard)

[Leetcode](https://leetcode.com/problems/longest-consecutive-sequence/description/) / [力扣](https://leetcode-cn.com/problems/longest-consecutive-sequence/description/)

```html
Given [100, 4, 200, 1, 3, 2],
The longest consecutive elements sequence is [1, 2, 3, 4]. Return its length: 4.
```

要求以 O(N) 的时间复杂度求解。


## 5. 和为 K 的子数组

560\. Subarray Sum Equals K (Medium)

[Leetcode](https://leetcode.com/problems/subarray-sum-equals-k/) / [力扣](https://leetcode.cn/problems/subarray-sum-equals-k/)

```text
Input: nums = [1, 1, 1], k = 2
Output: 2
```

题目描述：统计和为 k 的连续子数组个数，数组元素可能为负数。

用 sum 表示从数组开头到当前位置的前缀和，以当前位置结尾、和为 k 的子数组，对应前面某个位置的前缀和为 sum - k。遍历时用哈希表记录每个前缀和出现的次数即可。数组中有负数，窗口变大时和不一定变大，因此不能用滑动窗口。

### 我的笔记：前缀和 + 哈希表

> 以下为个人补充的解题思路和 Python 实现。

#### 什么时候想到前缀和？

遇到下面这些信号时，可以考虑前缀和：

- 题目涉及**连续子数组**或**区间的和**。
- 需要反复计算很多段区间的和。
- 需要判断某种区间和是否存在、统计区间个数，或者求符合条件的最长区间。
- 数组包含负数，窗口扩大时和不一定增大，不能直接套用依赖和的单调性的滑动窗口。

具体怎么记录前缀和，取决于题目：统计个数时记录**出现次数**，判断是否存在时可以记录是否出现，求最长长度时通常记录**最早出现的位置**。

#### 核心原理

**任意一段子数组的和 = 终点的前缀和 − 起点前一个位置的前缀和。**

为了避免下标混淆，定义 `prefix[t]` 为数组前 `t` 个元素的和，且 `prefix[0] = 0`。那么：

```text
nums[i] + ... + nums[j] = prefix[j + 1] - prefix[i]
```

因此，找一段和为 `k` 的子数组，就转化为：**找两个前缀和，它们的差是 `k`。**

#### 这道题怎么做？

遍历到当前位置时，设当前前缀和为 `pre_sum`：

```text
当前前缀和 - 之前的某个前缀和 = k
之前的某个前缀和 = pre_sum - k
```

所以，只需要查：**`pre_sum - k` 在之前的前缀和中出现过多少次？**

每出现一次，就对应一个以当前位置结尾、和为 `k` 的子数组。用字典 `sum_count` 保存「前缀和 → 出现次数」，将查到的次数加到答案中即可。

这里记录的是**从数组开头累加得到的和的出现次数**，不是数组元素本身的出现次数。

#### Python 实现

```python
from typing import List


class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        # 键：之前出现过的前缀和；值：这个前缀和出现的次数。
        # 初始的 0 表示空前缀，让从下标 0 开始的子数组也能被统计到。
        sum_count = {0: 1}
        pre_sum = 0  # 从数组开头到当前位置的累加和。
        ans = 0      # 和为 k 的连续子数组总个数。

        for num in nums:
            pre_sum += num

            # 之前每出现一次 pre_sum - k，就找到一个符合条件的子数组。
            # get 的第二个参数 0 表示：如果字典中没有这个键，就返回 0。
            ans += sum_count.get(pre_sum - k, 0)

            # 统计完答案后，再记录当前前缀和，供后续位置使用。
            sum_count[pre_sum] = sum_count.get(pre_sum, 0) + 1

        return ans
```

#### 两个关键细节

1. **为什么初始化为 `{0: 1}`？**

   空前缀的和是 `0`，在遍历前已经出现一次。如果当前 `pre_sum == k`，就能通过查询 `pre_sum - k == 0`，统计到从数组下标 `0` 开始的这段子数组。

2. **为什么先查询，再记录当前前缀和？**

   字典中只能包含当前位置之前的前缀和。如果先记录再查询，当 `k == 0` 时，会把当前前缀和与自身配对，错误地统计一个长度为 `0` 的空子数组。

#### 示例：`nums = [1, 1, 1]`，`k = 2`

初始状态：`sum_count = {0: 1}`，`pre_sum = 0`，`ans = 0`。

| 当前下标 | 当前数字 | 当前前缀和 | 查询 `pre_sum - k` | 之前出现次数 | 累计答案 |
| --- | --- | --- | --- | --- | --- |
| 0 | 1 | 1 | -1 | 0 | 0 |
| 1 | 1 | 2 | 0 | 1 | 1 |
| 2 | 1 | 3 | 1 | 1 | 2 |

最终找到两个子数组：`nums[0:2]` 和 `nums[1:3]`。它们的值都是 `[1, 1]`，但位置不同，因此分别计数。

**复杂度：**时间复杂度为 O(N)（哈希表查询和更新平均为 O(1)），空间复杂度为 O(N)。
