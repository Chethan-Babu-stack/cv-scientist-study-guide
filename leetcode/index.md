# LeetCode Practice Questions

---

## 1. Merge Sorted Array

**Problem Statement**  
You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.  
Merge `nums1` and `nums2` into a single array sorted in non-decreasing order.

**Example**  
Input  
`nums1 = [1,2,3,0,0,0], m = 3`  
`nums2 = [2,5,6], n = 3`  

Output  
`[1,2,2,3,5,6]`

**Python Solution**

```python
from typing import List

class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        """
        Do not return anything, modify nums1 in-place instead.
        """
        i, j, k = m - 1, n - 1, m + n - 1

        while j >= 0:
            if i >= 0 and nums1[i] > nums2[j]:
                nums1[k] = nums1[i]
                i -= 1
            else:
                nums1[k] = nums2[j]
                j -= 1
            k -= 1
```

## 2. Remove Element

**Problem Statement**  
Given an integer array `nums` and an integer `val`, remove **all** occurrences of `val` from `nums` **in-place**.  
The order of the remaining elements may change.  
Return the number of elements in `nums` that are **not** equal to `val`.

**Requirements**  
Let `k` be the count of values in `nums` different from `val`.  
To satisfy the problem constraints, your algorithm must:

1. Modify `nums` so that its first `k` positions contain the elements not equal to `val`.  
2. Ignore the remaining positions of `nums`; their values and the overall array length beyond `k` do **not** matter.  
3. Return `k`.

**Python Solution**

```python
from typing import List

class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        j = 0                     # position to overwrite
        for i in range(len(nums)):
            if nums[i] != val:    # keep elements not equal to val
                nums[j] = nums[i]
                j += 1
        return j                  # number of kept elements
```

## 3. Remove Duplicates from Sorted Array

**Problem Statement**  
Given an integer array `nums` sorted in non-decreasing order, remove the duplicates **in-place** such that each unique element appears only once.  
The relative order of the elements should be kept the same. Then return the number of unique elements in `nums`.

Consider the number of unique elements of `nums` to be `k`.  
To get accepted, you need to do the following things:

1. Change the array `nums` such that the first `k` elements of `nums` contain the unique elements in the order they were present in `nums` initially.  
2. The remaining elements of `nums` are not important, as well as the size of `nums`.  
3. Return `k`.

**Python Solution 1: Using two pointers**

```python
class Solution:
    def removeDuplicates(self, nums):
        k = 0 # slow
        for i in range(1, len(nums)): # fast
            if nums[i] != nums[k]:
                k += 1
                nums[k] = nums[i]
        return k + 1
```
**Python Solution 2: Using `prev` and `duplicates`**

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:

        prev = None
        duplicates = 0

        for i, num in enumerate(nums):

            if num == prev:
                # duplicates
                duplicates += 1
            
            else:
                # not duplicates
                nums[i-duplicates] = num

            prev = num

        return len(nums) - duplicates
```

## 4. Remove Duplicates from Sorted Array II

**Problem Statement**  
Given an integer array nums sorted in non-decreasing order, remove some duplicates in-place such that each unique element appears at most twice. The relative order of the elements should be kept the same.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.

Return k after placing the final result in the first k slots of nums.

Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.

Example:
Input: nums = [1,1,1,2,2,3]
Output: 5, nums = [1,1,2,2,3,_]

**Python Solution: Using two pointers**

```python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        k = 2
        for i in range(2, len(nums)):
            if nums[i] != nums[k-2]:
                nums[k] = nums[i]
                k += 1

        return k
```

## 5. Majority Element

**Problem Statement**  
Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

Example:
Input: nums = [3,2,3]
Output: 3

**Python Solution: Boyer-Moore Voting Algorithm**

```python
class Solution:
    def majorityElement(self, nums: List[int]) -> int:
        count = 0
        candidate = None

        for num in nums:
            if count == 0:
                candidate = num
            count += (1 if num == candidate else -1)

        return candidate
```

## 6. Rotate Array

**Problem Statement**  
Given an integer array nums, rotate the array to the right by k steps, where k is non-negative.

Example:
Input: nums = [1,2,3,4,5,6,7], k = 3
Output: [5,6,7,1,2,3,4]

**Python Solution**

```python
class Solution:
    def rotate(self, nums: List[int], k: int) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        k %= len(nums)
        def reverse(left, right):
            while left < right:
                nums[left], nums[right] = nums[right], nums[left]
                left += 1
                right -= 1

        reverse(0, len(nums)-1)
        reverse(0, k-1)
        reverse(k, len(nums)-1)
```

## 7. Best Time to Buy and Sell Stock

**Problem Statement**  
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Example:
Input: prices = [7,1,5,3,6,4]
Output: 5

**Python Solution**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        buy_price = prices[0]
        for i in range(1, len(prices)):
            if buy_price > prices[i]:
                buy_price = prices[i]
            profit = max(profit, prices[i]-buy_price)
        return profit
```

## 8. Best Time to Buy and Sell Stock II

**Problem Statement**  
You are given an integer array prices where prices[i] is the price of a given stock on the ith day.

On each day, you may decide to buy and/or sell the stock. You can only hold at most one share of the stock at any time. However, you can buy it then immediately sell it on the same day.

Find and return the maximum profit you can achieve.

Example:
Input: prices = [7,1,5,3,6,4]
Output: 7

**Python Solution**

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        profit = 0
        for i in range(1, len(prices)):
            if prices[i] > prices[i-1]:
                profit += (prices[i] - prices[i-1])
        return profit
```

## 9. Jump Game

**Problem Statement**  
You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

Example:
Input: nums = [2,3,1,1,4]
Output: true

**Python Solution 1**

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        farthest = 0
        for i in range(len(nums)):
            if i > farthest:
                return False
            farthest = max(farthest, i+nums[i])
        return True
```

**Python Solution 2**

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        gas_in_car = 0
        for fuel in nums:
            if gas_in_car < 0:
                return False
            elif fuel > gas_in_car:
                gas_in_car = fuel
            gas_in_car -= 1
        return True
```