
Version:python
~~~python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        n = len(nums)
        if n == 0: return 0
        p, q = 0, 1
        while q < n:
            if nums[p] != nums[q]:
                nums[p + 1] = nums[q]
                p = p + 1
            q = q + 1
        return p + 1  
~~~
