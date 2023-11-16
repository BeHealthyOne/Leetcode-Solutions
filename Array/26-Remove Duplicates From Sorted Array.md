双指针法，一个指针指向要保存位置的元素，一个指针指向当前的元素。后者用for循环遍历

当当前指针指向元素与要保存位置元素的值不同时，因为第一个元素肯定会保留，就把当前指针指向元素的值赋给下一个要保存位置的元素，之后让要保存位置的元素下标加1。最后返回的是保存位置的下标+1。

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
