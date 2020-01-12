# leetCode
## Tips:
### String:
#### Reverse the string in Python:
```python
a = 'abc'
a[::-1] is cba
```
#### How to count a frequency of a character in a string: count()
```python
## Count '1' in a binary string:
'{:032b}'.format(n).count("1")
```

### Number:
#### Converting the int --> 32-bit binary:
```Python
'{:032b}'.format(n)
```
#### Converting the 32-bit binary --> Int:
```Python
int(n,2)
```
#### How to reverse a number using Mathematics:
```Python
p =35433
res = 0      
while(p):
  res = res*10 + p%10
  p = p//10
```

### Palindrome
#### 680. Valid Palindrome II
Given a non-empty string s, you may delete at most one character. Judge whether you can make it a palindrome.

Example 1:
```
Input: "aba"
Output: True
```
Example 2:
```
Input: "abca"
Output: True
Explanation: You could delete the character 'c'.
```
##### Solution: 
We can use the standard two-pointer approach that starts at the left and right of the string and move inwards. Whenever there is a mismatch, we can either exclude the character at the left or the right pointer. We then take the two remaining substrings and compare against its reversed and see if either one is a palindrome.
```Python
class Solution(object):
    def validPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        left, right = 0, len(s)-1
        while(left < right):
            if s[left] != s[right]:
                one, two = s[left:right], s[left+1:right+1]
                return one == one [::-1] or two == two[::-1]
            else:
                left, right = left+1, right-1
        return True
                
```
