---
description: Peak Index in a Mountain Array - Easy
---

# Leetcode \# 852

## 题目

* 给出的`arr`被称为 “mountain”,如果此`arr`满足下列条件：
  * `arr.length>= 3`
  * 存在一个`i`，`i`的范围是`0 < i < arr.length - 1`，这使得：
    * `arr[0] < arr[1] < .... < arr[i-1] < arr[i]`
    * `arr[i] > arr[i+1] > .... > arr[i+2] > arr[arr.length - 1]`
* 其次，能**保证**给出的整数列表是个mountain，并 return 山顶的那个数字的index，也就是 **i**

Example 1:

```python
Input: arr = [0,1,0]
Output: 1
```

Example 2:

```python
Input: arr = [0,2,1,0]
Output: 1
```

Example 3:

```python
Input: arr = [0,10,5,2]
Output: 1
```

Example 4:

```python
Input: arr = [3,4,5,1]
Output: 2
```

Example 5:

```python
Input: arr = [24,69,100,99,79,78,67,36,26,19]
Output: 2
```

Constraints:

```python
3 <= arr.length <= 104
0 <= arr[i] <= 106
arr is guaranteed to be a mountain array.
```

## 解题思路

* 二分法：
  * 经典的二分查找，首先定义`left`和`right`,找到`mid`,如果`A[mid] < A[mid + 1]`，意味着右边部分还有更大的数字，将`left`变成`mid + 1`,否则将在左边部分查找知道找到结果，附上代码:
  * ```python
    class Solution:
        def peakIndexInMountainArray(self, A):
            l, r = 0, len(A) - 1
            while l < r:
                m = (l + r) / 2
                if A[m] < A[m + 1]:
                    l = m + 1
                else:
                    r = m
            return l
    ```
* 暴力法：
  * 直接 for 循环遍历，当找到当前数字比它之后一个数字还大的时候，就说明找到这个mountain的顶点了，return index `i`，附上代码:
  * ```python
    class Solution:
        def peakIndexInMountainArray(self, arr: List[int]) -> int:
            for i in range(0,len(arr)):
                if arr[i] > arr[i+1]:
                    return i
    ```

