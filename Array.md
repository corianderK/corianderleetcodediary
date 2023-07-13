# Binary search

Binary Search is defined as a searching algorithm used in a sorted array by repeatedly dividing the search interval in half. The idea of binary search is to use the information that the array is sorted and reduce the time complexity to O(log N). 

[leetcode 704](https://www.geeksforgeeks.org/binary-search/#)


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

****
# delete element

[leetcode 27](https://leetcode.cn/problems/remove-element/)

fast slow index method
```
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        fast,slow=0,0
        l=len(nums)
        while fast<l:
            if nums[fast]!=val:
                nums[slow]=nums[fast]
                slow+=1
            fast+=1
        return slow
```

# delete element & sort

[leetcode 977](https://leetcode.cn/problems/squares-of-a-sorted-array/)

Two index method
```
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:

        l, r, i = 0, len(nums)-1, len(nums)-1
        res = [float('inf')] * len(nums) # 需要提前定义列表，存放结果 #也可这样定义a=[0]*len(nums)
        while l <= r:
            if nums[l] ** 2 < nums[r] ** 2: # 左右边界进行对比，找出最大值
                res[i] = nums[r] ** 2
                r -= 1 # 右指针往左移动
            else:
                res[i] = nums[l] ** 2
                l += 1 # 左指针往右移动
            i -= 1 # 存放结果的指针需要往前平移一位
        return res
```

Sort funtion method

```
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        for i in range(len(nums)):
            nums[i]=nums[i]**2
        nums.sort()
        return nums
```
