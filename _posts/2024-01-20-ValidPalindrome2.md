# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
Given a string s, return true if the s can be palindrome after deleting at most one character from it.

 

Example 1:

Input: s = "aba"
Output: true
Example 2:

Input: s = "abca"
Output: true
Explanation: You could delete the character 'c'.
Example 3:

Input: s = "abc"
Output: false
 

Constraints:

1 <= s.length <= 105
s consists of lowercase English letters.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Using two pointers and check each charatcter.
2. If its not same, we cut either right or left and check again
 
ref : https://www.youtube.com/watch?v=JrxRYBwG6EI&ab_channel=NeetCode
# Complexity
- Time complexity: O(2*N) = O(N)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code
```
class Solution(object):
    def validPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        # This len(s) -1 is important 
        left_ptr, right_ptr = 0, len(s)-1

        while left_ptr < right_ptr:
            if s[left_ptr] != s[right_ptr]:
                cut_left, cut_right = s[left_ptr+1: right_ptr+1], s[left_ptr:right_ptr]
                #return (cut_left == cut_left[::-1] or cut_right == cut_right[::-1])
                
                
                if cut_left == cut_left[::-1] or cut_right == cut_right[::-1]:
                    return True
                else:
                    return False
            left_ptr, right_ptr = left_ptr +1, right_ptr -1

        return True
```
