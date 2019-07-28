Given an array of integers, return **indices** of the two numbers such that they add up to a specific target.

You may assume that each input would have **exactly** one solution, and you may not use the same element twice.

```
Given nums = [2, 7, 11, 15], target = 9,

Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```

**Solution**

```Python
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        hashTable = {}
        
        for i in range(len(nums)):
            hashTable[nums[i]] = i
        for i in range(len(nums)):
            if (target - nums[i]) in hashTable:
                #not use the same element twice
                if i == hashTable[target - nums[i]]:
                    continue
                else:
                    return [i, hashTable[target - nums[i]]]
        return None
```
