牺牲空间换时间，用哈希表来解决**查找的问题**。

时间复杂度为O(n)，空间复杂度为O(n)。

Version: python
~~~python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        hashtable = dict()
        for i, num in enumerate(nums):
            if target - num in hashtable:
                return [hashtable[target - num], i]
            hashtable[nums[i]] = i
        return []
~~~
