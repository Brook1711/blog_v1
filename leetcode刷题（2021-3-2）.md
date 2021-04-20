---
title: leetcode刷题（2021.3.2）
date: 2021-03-02 16:39:26
tags: [leetcode-cn, algrithom, go]
categories:
    - coding
    - leetcode
	- go
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210302164231292.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210302164333448.png
---

# 第三题

## 原题：

题目地址： [重复字符的最长子串](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

给定一个字符串，请你找出其中不含有重复字符的 **最长子串** 的长度。

示例 1:

```
输入: s = "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```


示例 2:

```
输入: s = "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```


示例 3:

```
输入: s = "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。
```


示例 4:

```
输入: s = ""
输出: 0
```

**提示：**

- `0 <= s.length <= 5 * 104`
- `s` 由英文字母、数字、符号和空格组成

## 解法

原文[地址](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/solution/zhi-zeng-da-bu-jian-xiao-de-hua-dong-chuang-kou-10/)

```go
func lengthOfLongestSubstring(s string) int {
	start,end := 0,0
	//start和end是开头和结尾两个信标，每一次循环查找信标内是否含有s[i]
	for i := 0; i < len(s); i++ {
		//这里的循环妙就妙在不是围绕着start和end两个自由度，
		//而是遍历i是否破坏了"单个字符不重复"的条件
		//第i位元素表示即将被纳入start和end之中的预备军
		index := strings.Index(s[start:i],string(s[i]))
		if index==-1{
			//当index==-1时，表示第i位元素不会破坏信标内（只有信标的[start:i]部分）
			//的"单个字符不重复"的条件
			//如果想要拓展必须保证[start:end]内都没有重复字符
			if i+1>end{
				end=i+1
				//此时如果i==end也能表示[start:end]内都没有重复字符
				//此时可以将end进行拓展
			}
		}else{
			//这里表示第i位元素和start到i之间（不包含第i位）的第index位（以start为0）
			//在这种情况下将窗口整体移动到第index+1位，跳过重复元素
			start+=index+1
			end+=index+1
		}
	}
	//另一个比较巧妙的地方是，由于窗口只增不减，最后当循环结束时end-start就是最后的结果
	return end-start
}
```

`strings.Index`的[官方解释](https://golang.org/pkg/strings/#Index)

> Index returns the index of the first instance of substr in s, or -1 if substr is not present in s.

关于切片：

>s := "abc"
>
>s[1:2]为“b”，可以概括为“左闭右开”。

# 第四题

原题：[寻找两个正序数组的中位数](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)

给定两个大小分别为 `m` 和 `n` 的正序（从小到大）数组 `nums1` 和 `nums2`。请你找出并返回这两个正序数组的 **中位数** 。

示例 1：

```
输入：nums1 = [1,3], nums2 = [2]
输出：2.00000
解释：合并数组 = [1,2,3] ，中位数 2
```


示例 2：

```
输入：nums1 = [1,2], nums2 = [3,4]
输出：2.50000
解释：合并数组 = [1,2,3,4] ，中位数 (2 + 3) / 2 = 2.5
```


示例 3：

```
输入：nums1 = [0,0], nums2 = [0,0]
输出：0.00000
```


示例 4：

```
输入：nums1 = [], nums2 = [1]
输出：1.00000
```


示例 5：

```
输入：nums1 = [2], nums2 = []
输出：2.00000
```


提示：

nums1.length == m
nums2.length == n
0 <= m <= 1000
0 <= n <= 1000
1 <= m + n <= 2000
-106 <= nums1[i], nums2[i] <= 106

## 解法

[原文地址](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/solution/xun-zhao-liang-ge-you-xu-shu-zu-de-zhong-wei-s-114/)

