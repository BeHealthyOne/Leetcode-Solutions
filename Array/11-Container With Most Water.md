设置双指针

Version:python
~~~python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        sum = 0
        n = len(height)
        left, right = 0, n - 1
        while left < right:
            if height[left] < height[right]:
                minH = height[left]
                temp = minH * (right - left)
                if temp > sum: sum = temp
                left = left + 1
            else:
                minH = height[right]
                temp = minH * (right - left)
                if temp > sum: sum = temp
                right = right - 1
        return sum
~~~
