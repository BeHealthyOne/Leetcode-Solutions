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

# 方法二、滑动窗口
用哈希集合存储滑动窗口中的数。

Version:python
~~~python
class Solution:
    def containsNearbyDuplicate(self, nums: List[int], k: int) -> bool:
        hashtable = set()
        for i, num in enumerate(nums):
            if i > k:    # 滑动窗口需要右移
                hashtable.remove(nums[i - k - 1])
            if num in hashtable:
                return True
            hashtable.add(num)
        return False
~~~
