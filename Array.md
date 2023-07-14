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

[leetcode 209. minimum size subarray sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

how to build a matrix by python:

<img width="304" alt="image" src="https://github.com/corianderK/corianderleetcodediary/assets/65326195/fe82e8c1-c7a4-4989-9ca3-f088c4cbc4c2">

```
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        l=len(nums)
        left=0
        right=0
        min_len=float('inf')
        cur_sum=0

        while right < l:
            cur_sum+=nums[right]
            while cur_sum>=target:
                min_len=min(min_len,right-left+1)
                cur_sum-=nums[left]
                left+=1
            right+=1
        return min_len if min_len!=float('inf') else 0
```


[leetcode 59. sprial matrix ii](https://leetcode.cn/problems/spiral-matrix-ii/)

<img width="264" alt="Screenshot 2023-07-14 at 14 15 19" src="https://github.com/corianderK/corianderleetcodediary/assets/65326195/5450d7a1-9c13-44d3-99a7-42716a2ea401">

```
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        startx=0
        starty=0
        nums=[[0]*n for _ in range(n)]
        loop=n//2
        mid=n//2
        count=1

        for offset in range(1,loop+1):
            for i in range(starty,n-offset):
                nums[startx][i]=count
                count+=1
            for j in range(startx,n-offset):
                nums[j][n-offset]=count
                count+=1
            for i in range(n-offset,starty,-1):
                nums[n-offset][i]=count
                count+=1
            for j in range(n-offset,startx,-1):
                nums[j][starty]=count
                count+=1
            startx+=1
            starty+=1

        if n%2 !=0:
            nums[mid][mid]=count
        return nums
```
