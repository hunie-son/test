# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
A phrase is a palindrome if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string s, return true if it is a palindrome, or false otherwise.

 

Example 1:

Input: s = "A man, a plan, a canal: Panama"
Output: true
Explanation: "amanaplanacanalpanama" is a palindrome.
Example 2:

Input: s = "race a car"
Output: false
Explanation: "raceacar" is not a palindrome.
Example 3:

Input: s = " "
Output: true
Explanation: s is an empty string "" after removing non-alphanumeric characters.
Since an empty string reads the same forward and backward, it is a palindrome.
 

Constraints:

1 <= s.length <= 2 * 105
s consists only of printable ASCII characters.

# Approach
<!-- Describe your approach to solving the problem. -->
1. Using functions (filtering w/ isalum(), coverting lower() and check reverse)

2. Two pointers

![image.png](https://assets.leetcode.com/users/images/d5101341-b9ee-4c28-ad2f-7febf0e3188b_1705788269.9442477.png)

ref: https://www.youtube.com/watch?v=jJXJ16kPFWg&ab_channel=NeetCode

# Complexity
- Time complexity: O(N)
<!-- Add your time complexity here, e.g. $$O(n)$$ -->

- Space complexity: O(1)
<!-- Add your space complexity here, e.g. $$O(n)$$ -->

# Code 1
```
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """

        newStr =""

        for c in s: 
            if c.isalnum():
                newStr += c.lower()

        #print (newStr)
        return newStr == newStr[::-1]

```

# Code 2
```
class Solution(object):
    def isPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        #Using two pointers
        left_ptr, right_ptr = 0, len(s)-1

        while left_ptr < right_ptr :
            while left_ptr < right_ptr and not self.isAlNum(s[left_ptr]):
                left_ptr += 1
            while left_ptr < right_ptr and not self.isAlNum(s[right_ptr]):
                right_ptr -= 1  
                
            #Check the this first wheater it is smame or not 
            if s[left_ptr].lower() != s[right_ptr].lower():
                return False
            
            left_ptr, right_ptr = left_ptr +1, right_ptr -1
        return True

    def isAlNum(self, c):
        # ASCII code base comparison
        return ('A'<=c<='Z' or 'a'<=c<='z' or '0'<=c<='9')
```
