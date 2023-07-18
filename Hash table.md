202. 快乐数

https://leetcode.cn/problems/happy-number/

```
       seen = []
       while n != 1:
           n = sum(int(i) ** 2 for i in str(n))
           if n in seen:
               return False
           seen.append(n)
       return True
```



349. 两个数组的交集
     
https://leetcode.cn/problems/intersection-of-two-arrays/

```
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        # 使用哈希表存储一个数组中的所有元素
        table = {}
        for num in nums1:
            #dictionary.get(keyname, value)
            table[num] = table.get(num, 0) + 1
        
        # 使用集合存储结果
        res = set()
        for num in nums2:
            if num in table:
                res.add(num)
                del table[num]
        
        return list(res)
```



1. 两数之和

https://leetcode.cn/problems/two-sum/

本题其实有四个重点：

1.为什么会想到用哈希表: 

  当我们需要查询一个元素是否出现过，或者一个元素是否在集合里的时候，就要第一时间想到哈希法。
  
2.哈希表为什么用map: 
  
  因为本题，我们不仅要知道元素有没有遍历过，还要知道这个元素对应的下标，需要使用 key value结构来存放，key来存元素，value来存下标，那么使用map正合适。

  再来看一下使用数组和set来做哈希法的局限。

  数组的大小是受限制的，而且如果元素很少，而哈希值太大会造成内存空间的浪费。

  set是一个集合，里面放的元素只能是一个key，而两数之和这道题目，不仅要判断y是否存在而且还要记录y的下标位置，因为要返回x 和 y的下标。所以set 也不能用。

3.本题map是用来存什么的: 

  map目的用来存放我们访问过的元素，因为遍历数组的时候，需要记录我们之前遍历过哪些元素和对应的下标，这样才能找到与当前元素相匹配的（也就是相加等于target）

4.map中的key和value用来存什么的:

  给出一个元素，判断这个元素是否出现过，如果出现过，返回这个元素的下标。

  那么判断元素是否出现，这个元素就要作为key，所以数组中的元素作为key，有key对应的就是value，value用来存下标。

  所以 map中的存储结构为 {key：数据元素，value：数组元素对应的下标}。

```
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        
        records = dict()

        for index, value in enumerate(nums):  
            if target - value in records:   # 遍历当前元素，并在map中寻找是否有匹配的key
            #用减法，比如target为9，value为2，这里即查找是否有元素=7，有则返回
                return [records[target- value], index]
            records[value] = index    # 遍历当前元素，并在map中寻找是否有匹配的key
            #将value=7，再遍历，下一次查找是否有元素2
        return []
```

第454题.四数相加II

https://leetcode.cn/problems/4sum-ii/

```
class Solution:
    def fourSumCount(self, nums1: List[int], nums2: List[int], nums3: List[int], nums4: List[int]) -> int:
        # 使用字典存储nums1和nums2中的元素及其和
        hashmap=dict()
        for n1 in nums1:
            for n2 in nums2:
                hashmap[n1+n2]=hashmap.get(n1+n2,0)+1

        # 如果 -(n1+n2) 存在于nums3和nums4, 存入结果
        count=0
        for n3 in nums3:
            for n4 in nums4:
                key=-n3-n4
                if key in hashmap:
                    count += hashmap[key]
                
        return count
```
