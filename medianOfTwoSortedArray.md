### Median of Two Sorted Arrays
#### LeetCode - Level: HARD

There are two sorted arrays nums1 and nums2 of size m and n respectively.

Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).

You may assume nums1 and nums2 cannot be both empty.

**Example 1:**
```
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
```
**Example 2:**
```
nums1 = [1, 2]
nums2 = [3, 4]
```
The median is (2 + 3)/2 = 2.5

### What is mean/median of An array:

**Mean of an array** = (sum of all elements) /
                   (number of elements)

**Median of a sorted array** of size n is defined as below:
1. Sort the array (If array not sorted)
2. * If n is odd: => middle element
   * If n is even: => average of middle two elements when n is even.

**Solution**

```Python
class Solution(object):
    def findMedianSortedArrays(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: float
        """
        #Step 1: Merge Sorted 2 Arrays => O(nlogn)
        n = len(nums1) + len(nums2)
        nums1.append(float("inf"))
        nums2.append(float("inf"))
        
        
        arr = [None]*n
        
        i = j = 0
        
        for k in range (n):
            if i < len(nums1) and nums1[i] <= nums2[j]:
                arr[k] = nums1[i]
                i+=1
            elif j < len(nums2) and nums1[i] > nums2[j]:
                arr[k] = nums2[j]
                j+=1
        
        #Step 2: Determine median of combined and sorted array
        if (len(arr) % 2 != 0):
            return float(arr[len(arr)//2])
        else:
            return float(arr[len(arr)//2 - 1] + arr[len(arr)//2])/2

def main():
    nums1 = [1,3]
    nums2 = [2]
    print(Solution().findMedianSortedArrays(nums1, nums2))

if __name__ == '__main__':
    main()
```
