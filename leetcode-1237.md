---
description: Find Positive Integer Solution for a Given Equation - Easy
---

# Leetcode \#1237

## 题目

* 给定一个函数`f(x,y)`和一个`z`值，当`f(x,y) == z`的时候，return所有的正整数组合`x and y`
* **注意**：function是 **constantly increasing**
  * `f(x, y) < f(x + 1, y)`
  * `f(x, y) < f(x, y + 1)`
* Function Interface:
  * ```python
    interface CustomFunction {
    public:
      // Returns positive integer f(x, y) for any given positive integer x 
      // and y.
      int f(int x, int y);
    };
    ```

Example 1:

```python
Input: function_id = 1, z = 5
Output: [[1,4],[2,3],[3,2],[4,1]]
Explanation: function_id = 1 means that f(x, y) = x + y
```

Example 2:

```python
Input: function_id = 2, z = 5
Output: [[1,5],[5,1]]
Explanation: function_id = 2 means that f(x, y) = x * y
```

Constraints:

```python
1 <= function_id <= 9
1 <= z <= 100
It's guaranteed that the solutions of f(x, y) == z will be on the range 1 <= x, y <= 1000
It's also guaranteed that f(x, y) will fit in 32 bit signed integer if 1 <= x, y <= 1000
```

## 解题思路

* 二分法：
  * 经典的二分查找
  * ```python
    class Solution:
        def findSolution(self, customfunction: 'CustomFunction', z: int) -> List[List[int]]:
            res = []
            for i in range(1,1001):
                left = 1
                right = 1000

                while left <= right:
                    mid = (left + right)//2
                    temp = customfunction.f(i,mid)
                    if temp == z:
                        res.append([i,mid])
                        break
                    elif temp > z:
                        right = mid - 1
                    elif temp < z:
                        left = mid + 1
            return res
    ```

