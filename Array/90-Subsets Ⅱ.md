# 方法一、迭代

因为数组中的元素是任意顺序的，而且存在重复。可以先让数组排序，然后在迭代过程中排除重复的元素。具体实现类似第78题

Version:python
~~~python
class Solution:
    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        nums.sort()
        res = [[]]
        for num in nums:
            temp = [[num] + i for i in res if not [num] + i in res]
            res = res + [i for i in temp]
        return res
~~~
