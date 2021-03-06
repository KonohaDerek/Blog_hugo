---
title: "一日一LeetCode 計畫"
subtitle: "C# - Add Two Numbers"
date: 2021-07-23T17:23:13Z
tags:
  - "C#"
  - "LeetCode"
---


今天開始來實行一日一 LeetCode 計畫，除了讓自己更熟悉語言外，也想多練習更多的演算法  
一開始也想不到要寫什麼side project  
那麼就來刷刷 LeetCode 吧  
從一開始註冊到現在也過了超久的(我就懶)  
接下來會利用各種不同的語言寫同一個題目  
目前計畫的有 `C#` , `golang` , `php` , `typescript`  
希望能持續進步這些語言  
話不多說我們就開始吧  

題目為  

```

You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
```

### Example 1 :
![](https://assets.leetcode.com/uploads/2020/10/02/addtwonumber1.jpg)

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807.
```

### Example 2 :
```
Input: l1 = [0], l2 = [0]
Output: [0]
```

### Example 3 :
```
Input: l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
Output: [8,9,9,9,0,0,0,1]
```

### 解法
---

1. 看到這題目很直覺得知道是 `LinkList` 的題目，又有規律性，看起來就是一個可以用遞迴簡單處理的東西

1. 實際解法
    ``` C#
    /**
    * Definition for singly-linked list.
    * public class ListNode {
    *     public int val;
    *     public ListNode next;
    *     public ListNode(int val=0, ListNode next=null) {
    *         this.val = val;
    *         this.next = next;
    *     }
    * }
    */
    public class Solution {
        public ListNode AddTwoNumbers(ListNode l1, ListNode l2) {
                return Calculation(l1,l2,0);

            }

            private ListNode Calculation(ListNode l1, ListNode l2 , int add) {
                if(l1 == null && l2 == null && add ==0) {
                    return null;
                }
                var result = (l1?.val ?? 0) + (l2?.val ?? 0) + add;
                var node_value = result % 10;
                var next_add_value = result /10;

                return new ListNode(node_value ,Calculation(l1?.next , l2?.next , next_add_value ) ) ;
            }

    }
    ```

1. 執行效能
![](./img/Performance.JPG)


