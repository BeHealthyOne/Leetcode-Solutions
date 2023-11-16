要求时间复杂度为O(n)， 空间复杂度为O(1)，就使用置换法。

假如排好序，则数组中的元素是1，2，3，4，……这样的顺序。那么，下标为i的数组中对应的值为i+1。排序后nums[i]-1对应的值就等于i的值。

Version:python
~~~python
class Solution:
    def firstMissingPositive(self, nums: List[int]) -> int:
        n = len(nums)
        for i in range(n):
            while 1 <= nums[i] <= n and nums[nums[i] - 1] != nums[i]:
                nums[nums[i] - 1], nums[i] = nums[i], nums[nums[i] - 1]    # can not exchange
        for i in range(n):
            if nums[i] != i + 1:
                return i + 1
        return n + 1
~~~
