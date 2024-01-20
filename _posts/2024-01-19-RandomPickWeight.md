---
layout: post
title:  "Random Pcik with Weight LeetCode"
date:   2024-01-19
excerpt: "Coding prep."

tag:
- LeetCode
- CrackingFAANG
comments: false
---

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
You are given a 0-indexed array of positive integers w where w[i] describes the weight of the ith index.

You need to implement the function pickIndex(), which randomly picks an index in the range [0, w.length - 1] (inclusive) and returns it. The probability of picking an index i is w[i] / sum(w).

For example, if w = [1, 3], the probability of picking index 0 is 1 / (1 + 3) = 0.25 (i.e., 25%), and the probability of picking index 1 is 3 / (1 + 3) = 0.75 (i.e., 75%).
 

Example 1:

Input
["Solution","pickIndex"]
[[[1]],[]]
Output
[null,0]

Explanation
Solution solution = new Solution([1]);
solution.pickIndex(); // return 0. The only option is to return 0 since there is only one element in w.
Example 2:

Input
["Solution","pickIndex","pickIndex","pickIndex","pickIndex","pickIndex"]
[[[1,3]],[],[],[],[],[]]
Output
[null,1,1,1,1,0]

Explanation
Solution solution = new Solution([1, 3]);
solution.pickIndex(); // return 1. It is returning the second element (index = 1) that has a probability of 3/4.
solution.pickIndex(); // return 1
solution.pickIndex(); // return 1
solution.pickIndex(); // return 1
solution.pickIndex(); // return 0. It is returning the first element (index = 0) that has a probability of 1/4.

Since this is a randomization problem, multiple answers are allowed.
All of the following outputs can be considered correct:
[null,1,1,1,1,0]
[null,1,1,1,1,1]
[null,1,1,1,0,0]
[null,1,1,1,0,1]
[null,1,0,1,0,0]
......
and so on.
 

Constraints:

1 <= w.length <= 104
1 <= w[i] <= 105
pickIndex will be called at most 104 times.

# Approach
<!-- Describe your approach to solving the problem. -->
Culmulative Sum : creating buckets
Binary Search : To find the best buckets

![image.png](https://assets.leetcode.com/users/images/2a5b3a0c-d3c6-41ed-88fc-b4e717d82f67_1705728383.0958092.png)

ref: https://www.youtube.com/watch?v=7x7Ydq2Wfvw&t=382s&ab_channel=CrackingFAANG

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->


- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution(object):

    def __init__(self, w):
        """
        :type w: List[int]
        """
        self.prefix_sums =[]
        total =0
        
        #Culmulative Sum
        for weight in w:
            total += weight
            self.prefix_sums.append(total)
        
        self.total = total

    def pickIndex(self):
        """
        :rtype: int
        """
        #[1,2,4] -->(CulmulativeSum) [1,3,7] --> 4
        target =random.uniform(0, self.total)

        # binary search
        left = 0
        right = len(self.prefix_sums)
        
        while left <right:
            mid = (left + right) //2

            if self.prefix_sums[mid] < target:
                left = mid + 1
            else:
                right = mid

        return left

    #INIT --> Time O(N), Store: O(N)
    #pickIndex --> Time: log(N) bc binary search, Store O(1) bc target, left and right 
        


# Your Solution object will be instantiated and called as such:
# obj = Solution(w)
# param_1 = obj.pickIndex()
```
