# 方法一、暴力
先遍历，找到和大于target的情况，然后再从开始之后的元素重复运算。

# 方法二、滑动窗口
因为需要保存满足所有和大于target的最小长度，也就是说当和大于target时，需要判断丢弃当前序列的左边部分这个条件能否成立。这样的情况就可以使用滑动窗口。

Version:python
~~~python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        n = len(nums)
        start, end = 0, 0
        cnt, temp = n + 1, 0
        while end < n:
            temp = temp + nums[end]
            while temp >= target:
                cnt = min(cnt, end - start + 1)
                temp = temp - nums[start]
                start = start + 1
            end = end + 1
        if cnt == n + 1:
            return 0
        else:
            return cnt
~~~
