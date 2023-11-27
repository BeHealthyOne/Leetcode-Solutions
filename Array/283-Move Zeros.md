# 方法一、两次遍历
两次遍历，一次统计非0元素的个数，并放到左边，第二次将最右边的置为0

Version:python
~~~python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        n = len(nums)
        j = 0
        for i in range(n):
            if nums[i]:
                nums[j] = nums[i]
                j = j + 1
        for i in range(j, n):
            nums[i] = 0
~~~

# 方法二、快速排序
用类似快速排序的方式，枢轴作为0，不为0的放在左边。

Version:python
~~~python
class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        n = len(nums)
        j = 0
        for i in range(n):
            if nums[i]:
                nums[j], nums[i] = nums[i], nums[j]
                j = j + 1
~~~
