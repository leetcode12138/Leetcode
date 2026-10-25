# Leetcode 题解 - 栈和队列

> 原作者：[CyC2018](https://github.com/CyC2018) 及 CS-Notes 贡献者。来源：[CS-Notes 原文](https://github.com/CyC2018/CS-Notes/blob/9b262ea010f453d1d53088604ac472a7b7d6e957/notes/Leetcode%20%E9%A2%98%E8%A7%A3%20-%20%E6%A0%88%E5%92%8C%E9%98%9F%E5%88%97.md)。
> 本页保留原文分类、题目、示例和文字解析，移除了实现代码和图片；采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可。

<!-- GFM-TOC -->
* [Leetcode 题解 - 栈和队列](#leetcode-题解---栈和队列)
    * [1. 用栈实现队列](#1-用栈实现队列)
    * [2. 用队列实现栈](#2-用队列实现栈)
    * [3. 最小值栈](#3-最小值栈)
    * [4. 用栈实现括号匹配](#4-用栈实现括号匹配)
    * [5. 数组中元素与下一个比它大的元素之间的距离](#5-数组中元素与下一个比它大的元素之间的距离)
    * [6. 循环数组中比当前元素大的下一个元素](#6-循环数组中比当前元素大的下一个元素)
    * [7. 字符串解码](#7-字符串解码)
    * [8. 基本计算器](#8-基本计算器)
<!-- GFM-TOC -->


## 1. 用栈实现队列

232\. Implement Queue using Stacks (Easy)

[Leetcode](https://leetcode.com/problems/implement-queue-using-stacks/description/) / [力扣](https://leetcode-cn.com/problems/implement-queue-using-stacks/description/)

栈的顺序为后进先出，而队列的顺序为先进先出。使用两个栈实现队列，一个元素需要经过两个栈才能出队列，在经过第一个栈时元素顺序被反转，经过第二个栈时再次被反转，此时就是先进先出顺序。


## 2. 用队列实现栈

225\. Implement Stack using Queues (Easy)

[Leetcode](https://leetcode.com/problems/implement-stack-using-queues/description/) / [力扣](https://leetcode-cn.com/problems/implement-stack-using-queues/description/)

在将一个元素 x 插入队列时，为了维护原来的后进先出顺序，需要让 x 插入队列首部。而队列的默认插入顺序是队列尾部，因此在将 x 插入队列尾部之后，需要让除了 x 之外的所有元素出队列，再入队列。


## 3. 最小值栈

155\. Min Stack (Easy)

[Leetcode](https://leetcode.com/problems/min-stack/description/) / [力扣](https://leetcode-cn.com/problems/min-stack/description/)


对于实现最小值队列问题，可以先将队列使用栈来实现，然后就将问题转换为最小值栈，这个问题出现在 编程之美：3.7。

## 4. 用栈实现括号匹配

20\. Valid Parentheses (Easy)

[Leetcode](https://leetcode.com/problems/valid-parentheses/description/) / [力扣](https://leetcode-cn.com/problems/valid-parentheses/description/)

```html
"()[]{}"

Output : true
```


## 5. 数组中元素与下一个比它大的元素之间的距离

739\. Daily Temperatures (Medium)

[Leetcode](https://leetcode.com/problems/daily-temperatures/description/) / [力扣](https://leetcode-cn.com/problems/daily-temperatures/description/)

```html
Input: [73, 74, 75, 71, 69, 72, 76, 73]
Output: [1, 1, 4, 2, 1, 1, 0, 0]
```

在遍历数组时用栈把数组中的数存起来，如果当前遍历的数比栈顶元素来得大，说明栈顶元素的下一个比它大的数就是当前元素。


## 6. 循环数组中比当前元素大的下一个元素

503\. Next Greater Element II (Medium)

[Leetcode](https://leetcode.com/problems/next-greater-element-ii/description/) / [力扣](https://leetcode-cn.com/problems/next-greater-element-ii/description/)

```text
Input: [1,2,1]
Output: [2,-1,2]
Explanation: The first 1's next greater number is 2;
The number 2 can't find next greater number;
The second 1's next greater number needs to search circularly, which is also 2.
```

与 739. Daily Temperatures (Medium) 不同的是，数组是循环数组，并且最后要求的不是距离而是下一个元素。


## 7. 字符串解码

394\. Decode String (Medium)

[Leetcode](https://leetcode.com/problems/decode-string/) / [力扣](https://leetcode.cn/problems/decode-string/)

```text
Input: "3[a2[c]]"
Output: "accaccacc"
```

括号可以嵌套，用栈保存进入括号之前的状态：遇到 [ 时，把重复次数和当前已经得到的字符串分别压栈，然后从头开始记录括号内的字符串；遇到 ] 时弹出重复次数 k 和之前的字符串 prev，当前字符串变为 prev 加上括号内的字符串重复 k 次。


## 8. 基本计算器

227\. Basic Calculator II (Medium)

[Leetcode](https://leetcode.com/problems/basic-calculator-ii/) / [力扣](https://leetcode.cn/problems/basic-calculator-ii/)

```text
Input: " 3+5 / 2 "
Output: 5
```

题目描述：计算只包含非负整数、+、-、*、/ 和空格的表达式，整数除法向零截断。

乘除的优先级高于加减。读到一个数字之后，先不急着计算，等读到它后面的运算符时，再根据它前面的运算符处理：+ 把数字压栈，- 把相反数压栈，* 和 / 与栈顶元素计算后再放回。最后把栈中所有元素相加。
