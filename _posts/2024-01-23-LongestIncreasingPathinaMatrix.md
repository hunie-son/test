# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Given an m x n integers matrix, return the length of the longest increasing path in matrix.

From each cell, you can either move in four directions: left, right, up, or down. You may not move diagonally or move outside the boundary (i.e., wrap-around is not allowed).

![image.png](https://assets.leetcode.com/users/images/cd0ce8fe-1448-46b6-9787-e2074a3e4118_1706082111.5256217.png)


# Approach
<!-- Describe your approach to solving the problem. -->
DFS and create Longest Increasing path (LIP)
![image.png](https://assets.leetcode.com/users/images/2bc3d30b-6dfa-429e-acda-da43e34eb4c1_1706082204.4098816.png)

ref: https://www.youtube.com/watch?v=wCc_nd-GiEc&ab_channel=NeetCode

# Complexity
- Time complexity: O(n,m)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity:O(n,m)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```python
class Solution(object):
    def longestIncreasingPath(self, matrix):
        """
        :type matrix: List[List[int]]
        :rtype: int
        """

        Rows, Cols = len(matrix), len(matrix[0])
        HMap = {} # LIP (r,c)

        def dfs (r,c, preV):
            if (r<0 or r==Rows or c <0 or c==Cols or matrix[r][c] <= preV):
                return 0
            
            if (r,c) in HMap:
                return HMap[(r,c)]

            result = 1 # Default rank of every space
            result = max(result, 1 + dfs(r+1,c, matrix[r][c]))
            result = max(result, 1 + dfs(r-1,c, matrix[r][c]))
            result = max(result, 1 + dfs(r,c+1, matrix[r][c]))
            result = max(result, 1 + dfs(r,c-1, matrix[r][c]))
            HMap[(r,c)] = result
            return result

        
        for r in range (Rows):
            for c in range (Cols):
                dfs(r,c,-1)
        
        return max(HMap.values())
```
