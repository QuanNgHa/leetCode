You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

<img width="552" alt="Screenshot 2019-07-29 at 12 38 44 AM" src="https://user-images.githubusercontent.com/47073386/62010133-46f3b480-b199-11e9-9cbe-fa69623fde04.png">

**Example:**
```
Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 0 -> 8
Explanation: 342 + 465 = 807.
```
**Code**

```Python
# Definition for singly-linked list.
class ListNode(object):
    def __init__(self, x):
       self.val = x
       self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        result = ListNode(0)
        #Current Node of "result" ListNode
        curr = result
        totalSum = 0
        carry = 0
        
        while l1 or l2 or carry:
            if (l1):
                totalSum += l1.val
                l1 = l1.next
            if (l2):
                totalSum += l2.val
                l2 = l2.next
            totalSum += carry
            carry = totalSum // 10
            curr.next = ListNode(totalSum % 10)
            
            curr = curr.next
            totalSum = 0
        #since result.head = 0 => return result.next    
        return result.next
```
