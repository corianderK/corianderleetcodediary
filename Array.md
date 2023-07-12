Binary search

Binary Search is defined as a searching algorithm used in a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(log N). 

https://www.geeksforgeeks.org/binary-search/#

for leetcode 704

solution 1: [left,right)
```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l=0
        r=len(nums)
        while l<r:
            mid=l+(r-l)//2
            if nums[mid]>target:
                r=mid
            elif nums[mid]<target:
                l=mid+1
            else:
                return mid
          
        return -1
```

solution 2:[left,right]
```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l=0
        r=len(nums)-1
        while l<=r:
            mid=l+(r-l)//2
            if nums[mid]>target:
                r=mid-1
            elif nums[mid]<target:
                l=mid+1
            else:
                return mid
          
        return -1
```
