---
layout: post
title:  "Valid Word abbreviation LeetCode 408"
date:   2024-01-20
excerpt: "Coding prep."

tag:
- LeetCode
- CrackingFAANG
comments: false
---

# Intuition
<!-- Describe your first thoughts on how to solve this problem. -->
A string can be abbreviated by replacing any number of non-adjacent, non-empty substrings with their lengths. The lengths should not have leading zeros.

For example, a string such as "substitution" could be abbreviated as (but not limited to):

"s10n" ("s ubstitutio n")
"sub4u4" ("sub stit u tion")
"12" ("substitution")
"su3i1u2on" ("su bst i t u ti on")
"substitution" (no substrings replaced)
The following are not valid abbreviations:

"s55n" ("s ubsti tutio n", the replaced substrings are adjacent)
"s010n" (has leading zeros)
"s0ubstitution" (replaces an empty substring)
Given a string word and an abbreviation abbr, return whether the string matches the given abbreviation.

A substring is a contiguous non-empty sequence of characters within a string.

 

Example 1:

Input: word = "internationalization", abbr = "i12iz4n"
Output: true
Explanation: The word "internationalization" can be abbreviated as "i12iz4n" ("i nternational iz atio n").


Example 2:

Input: word = "apple", abbr = "a2e"
Output: false
Explanation: The word "apple" cannot be abbreviated as "a2e".
 

Constraints:

1 <= word.length <= 20
word consists of only lowercase English letters.

1 <= abbr.length <= 10
abbr consists of lowercase English letters and digits.
All the integers in abbr will fit in a 32-bit integer.

# Approach
<!-- Describe your approach to solving the problem. -->

![image.png](https://assets.leetcode.com/users/images/6dd8b9a5-72d7-48ed-8606-e938f643c6f9_1705785753.3775294.png)

ref: https://www.youtube.com/watch?v=Sut-F029biM&ab_channel=CrackingFAANG

Two pointers solution 
To track progress through word and abbreviation

# Complexity
- Time complexity:
<!-- Add your time complexity here, e.g. $$O(n)$$ -->
O(N), in worst case

- Space complexity:
<!-- Add your space complexity here, e.g. $$O(n)$$ -->
O(1), No data structure but storing variables.

# Code
```
class Solution(object):
    def validWordAbbreviation(self, word, abbr):
        """
        :type word: str
        :type abbr: str
        :rtype: bool
        """

        word_ptr = abbr_ptr = 0

        while word_ptr < len(word) and abbr_ptr < len(abbr):
            #Since the time of calling function makes Time constraints
            #if abbr[abbr_ptr].isdigit():
                # If it is leading zeros
            
            if abbr[abbr_ptr] == "0":
                return False
            step = 0
                
            # It could have two or more digits of abbreviation
            #while abbr_ptr < len (abbr) and abbr[abbr_ptr].isdigit():
            
            # For time constraints, we are not using idigit() 
            while abbr_ptr< len (abbr) and abbr[abbr_ptr] in '0123456789':
                step = step * 10 + int(abbr[abbr_ptr])
                #abbriviation pointer plus one
                abbr_ptr += 1

            if step > 0:
                word_ptr += step

            # word pointer shift to the step amount
            #word_ptr += step
            else:
                if word[word_ptr] != abbr[abbr_ptr]:
                    return False
            
                word_ptr += 1
                abbr_ptr += 1
        #Make sure that pointers reach the word length
        return word_ptr == len(word) and abbr_ptr == len(abbr)


        
```
