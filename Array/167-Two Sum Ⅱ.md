# 方法一、双指针

Version:python
~~~python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        n = len(numbers)
        left, right = 0, n - 1
        res = []
        while left < right:
            if numbers[left] + numbers[right] == target:
                res.append(left + 1)
                res.append(right + 1)
                return res
            elif numbers[left] + numbers[right] < target:
                left = left + 1
            else:
                right = right - 1
        return 
~~~
