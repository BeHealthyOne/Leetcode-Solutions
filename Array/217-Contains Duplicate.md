# 方法一、哈希表
Version:python
~~~python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        hashtable = dict()
        n = len(nums)
        for i, num in enumerate(nums):
            if num in hashtable:
                return True
            hashtable[num] = i
        return False
~~~
