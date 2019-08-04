Given a string, find the length of the longest substring without repeating characters.

**Examples:**
```
Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 
Example 2:

Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.
Example 3:

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
**Solution**

```Python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        #print(type(s))
        maxLength  = 0 
        
        startIndex = 0
        usedChar = {}
        for i in range(len(s)):
            if s[i] in usedChar and startIndex <= usedChar[s[i]]:
                startIndex = usedChar[s[i]] +1
            else:
                maxLength = max(maxLength, i - startIndex +1)

            usedChar[s[i]] = i    
            
        return maxLength


def main():
    #s = "abcabcbb"
    #s = "pwwkew"
    #s = "abba"
    s = "tmmzuxt"
    print(Solution().lengthOfLongestSubstring(s))

if __name__ == '__main__':
    main()
```



Common question about the code: why startIndex <= usedChars[s[i]].

1) Imagine next string:

**abcdbac**

First occurrence on not unique character bill be “b”: abcdbac. That means that last string with all unique characters before this b — will be abcdbac. So, we are pointing start pointer to the element with index 2.
Since we are not saving here elements counts in hashtable, once we will find second a — we will see, that this is not unique char again, however its position was before even first b, so we kindly ignoring that, since 0 ( which is index of a ) is less then value of start.

2) We want to ensure that startIndex is updated with the Latest position:

**s = "tmmzuxt"**

In this case, m occured first, then startIndex already moved to position 2. But then, the second t occured lastly, and usedChars['t'] is still in position 0 only. If dont add the condition, startIndex will be lower to position 1, which is not true. 
