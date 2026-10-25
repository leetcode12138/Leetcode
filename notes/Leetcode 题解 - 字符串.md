# Leetcode 题解 - 字符串

> 原作者：[CyC2018](https://github.com/CyC2018) 及 CS-Notes 贡献者。来源：[CS-Notes 原文](https://github.com/CyC2018/CS-Notes/blob/9b262ea010f453d1d53088604ac472a7b7d6e957/notes/Leetcode%20%E9%A2%98%E8%A7%A3%20-%20%E5%AD%97%E7%AC%A6%E4%B8%B2.md)。
> 本页保留原文分类、题目、示例和文字解析，移除了实现代码和图片；采用 [CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/) 许可。

<!-- GFM-TOC -->
* [Leetcode 题解 - 字符串](#leetcode-题解---字符串)
    * [1. 字符串循环移位包含](#1-字符串循环移位包含)
    * [2. 字符串循环移位](#2-字符串循环移位)
    * [3. 字符串中单词的翻转](#3-字符串中单词的翻转)
    * [4. 两个字符串包含的字符是否完全相同](#4-两个字符串包含的字符是否完全相同)
    * [5. 计算一组字符集合可以组成的回文字符串的最大长度](#5-计算一组字符集合可以组成的回文字符串的最大长度)
    * [6. 字符串同构](#6-字符串同构)
    * [7. 回文子字符串个数](#7-回文子字符串个数)
    * [8. 判断一个整数是否是回文数](#8-判断一个整数是否是回文数)
    * [9. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数](#9-统计二进制字符串中连续-1-和连续-0-数量相同的子字符串个数)
    * [10. 最长回文子串](#10-最长回文子串)
    * [11. 字符串相乘](#11-字符串相乘)
    * [12. 比较版本号](#12-比较版本号)
<!-- GFM-TOC -->


## 1. 字符串循环移位包含

编程之美 3.1

```html
s1 = AABCD, s2 = CDAA
Return : true
```

给定两个字符串 s1 和 s2，要求判定 s2 是否能够被 s1 做循环移位得到的字符串包含。

s1 进行循环移位的结果是 s1s1 的子字符串，因此只要判断 s2 是否是 s1s1 的子字符串即可。

## 2. 字符串循环移位

编程之美 2.17

```html
s = "abcd123" k = 3
Return "123abcd"
```

将字符串向右循环移动 k 位。

将 abcd123 中的 abcd 和 123 单独翻转，得到 dcba321，然后对整个字符串进行翻转，得到 123abcd。

## 3. 字符串中单词的翻转

程序员代码面试指南

```html
s = "I am a student"
Return "student a am I"
```

将每个单词翻转，然后将整个字符串翻转。

## 4. 两个字符串包含的字符是否完全相同

242\. Valid Anagram (Easy)

[Leetcode](https://leetcode.com/problems/valid-anagram/description/) / [力扣](https://leetcode-cn.com/problems/valid-anagram/description/)

```html
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.
```

可以用 HashMap 来映射字符与出现次数，然后比较两个字符串出现的字符数量是否相同。

由于本题的字符串只包含 26 个小写字符，因此可以使用长度为 26 的整型数组对字符串出现的字符进行统计，不再使用 HashMap。


## 5. 计算一组字符集合可以组成的回文字符串的最大长度

409\. Longest Palindrome (Easy)

[Leetcode](https://leetcode.com/problems/longest-palindrome/description/) / [力扣](https://leetcode-cn.com/problems/longest-palindrome/description/)

```html
Input : "abccccdd"
Output : 7
Explanation : One longest palindrome that can be built is "dccaccd", whose length is 7.
```

使用长度为 256 的整型数组来统计每个字符出现的个数，每个字符有偶数个可以用来构成回文字符串。

因为回文字符串最中间的那个字符可以单独出现，所以如果有单独的字符就把它放到最中间。


## 6. 字符串同构

205\. Isomorphic Strings (Easy)

[Leetcode](https://leetcode.com/problems/isomorphic-strings/description/) / [力扣](https://leetcode-cn.com/problems/isomorphic-strings/description/)

```html
Given "egg", "add", return true.
Given "foo", "bar", return false.
Given "paper", "title", return true.
```

记录一个字符上次出现的位置，如果两个字符串中的字符上次出现的位置一样，那么就属于同构。


## 7. 回文子字符串个数

647\. Palindromic Substrings (Medium)

[Leetcode](https://leetcode.com/problems/palindromic-substrings/description/) / [力扣](https://leetcode-cn.com/problems/palindromic-substrings/description/)

```html
Input: "aaa"
Output: 6
Explanation: Six palindromic strings: "a", "a", "a", "aa", "aa", "aaa".
```

从字符串的某一位开始，尝试着去扩展子字符串。


## 8. 判断一个整数是否是回文数

9\. Palindrome Number (Easy)

[Leetcode](https://leetcode.com/problems/palindrome-number/description/) / [力扣](https://leetcode-cn.com/problems/palindrome-number/description/)

要求不能使用额外空间，也就不能将整数转换为字符串进行判断。

将整数分成左右两部分，右边那部分需要转置，然后判断这两部分是否相等。


## 9. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数

696\. Count Binary Substrings (Easy)

[Leetcode](https://leetcode.com/problems/count-binary-substrings/description/) / [力扣](https://leetcode-cn.com/problems/count-binary-substrings/description/)

```html
Input: "00110011"
Output: 6
Explanation: There are 6 substrings that have equal number of consecutive 1's and 0's: "0011", "01", "1100", "10", "0011", and "01".
```


## 10. 最长回文子串

5\. Longest Palindromic Substring (Medium)

[Leetcode](https://leetcode.com/problems/longest-palindromic-substring/) / [力扣](https://leetcode.cn/problems/longest-palindromic-substring/)

```text
Input: s = "babad"
Output: "bab"（"aba" 也是正确答案）
```

和第 7 题一样从中心扩展：回文串的中心可能是一个字符，也可能是两个字符之间，以每个位置为中心分别向两边扩展，记录最长的回文。时间复杂度为 O(N<sup>2</sup>)，空间复杂度为 O(1)。


## 11. 字符串相乘

43\. Multiply Strings (Medium)

[Leetcode](https://leetcode.com/problems/multiply-strings/) / [力扣](https://leetcode.cn/problems/multiply-strings/)

```text
Input: num1 = "123", num2 = "45"
Output: "5535"
```

题目描述：以字符串形式给出两个非负整数，返回它们的乘积，不能把字符串直接转换为整数。

模拟竖式乘法。乘积最多有 m + n 位，用数组 digits 按从高位到低位的顺序保存。num1[i] 与 num2[j] 相乘的结果落在 digits[i + j + 1] 上，先把所有乘积累加到对应位置，最后从低位到高位统一处理进位。


## 12. 比较版本号

165\. Compare Version Numbers (Medium)

[Leetcode](https://leetcode.com/problems/compare-version-numbers/) / [力扣](https://leetcode.cn/problems/compare-version-numbers/)

```text
Input: version1 = "1.01", version2 = "1.001"
Output: 0
Input: version1 = "1.0.1", version2 = "1"
Output: 1
```

题目描述：版本号由 . 分隔的修订号组成，从左到右依次比较修订号的整数值，前导 0 忽略，缺少的修订号视为 0。

用两个指针分别扫描两个字符串，每次各解析出一段修订号的整数值进行比较，不需要先把字符串分割成数组。
