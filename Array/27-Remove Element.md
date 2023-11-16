双指针法，一个指向要保存的位置，一个指向当前元素。

对于数组中的每一个元素，如果不是指定删除的值，就把当前指针的值赋值给要保存的位置，之后让该位置移动。

Version:python
~~~python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        n = len(nums)
        if n == 0: return 0
        left = 0
        for right in range(n):
            if nums[right] != val:
                nums[left] = nums[right]
                left = left + 1
        return left
~~~
