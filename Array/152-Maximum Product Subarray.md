# 方法一、动态规划
有点类似第53题，但是不完全相同。因为存在负数。需要考虑之前的负数越小，当前的元素也是负数时，乘积得到的值也就越大。因此这道题目需要维护两个数组，一个记录以nums[i]为结尾的最大值，一个记录以nums[i]为结尾的最小值，这个最小值当然要为负数形式。

然后就是经典的滚动数组优化存储空间。

注意，需要额外维护一个res存放每次遍历过程中的最大值。

Version:python
~~~python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        res = maxn = minn = nums[0]
        n = len(nums)
        for i in range(1, n):
            t = nums[i]
            mx, mn = maxn, minn    # 需要暂存数据
            maxn = max(mx * t, max(t, mn * t))
            minn = min(mn * t, min(t, mx * t))
            res = max(res, maxn)
        return res
~~~

