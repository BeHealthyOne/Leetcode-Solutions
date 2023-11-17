经典动态规划问题

动态规划问题的关键是**状态和状态转移方程**。

状态的定义：因为每次遇到一个元素就要比较，所以选择状态dp[i]表示以nums[i]为结尾。状态转移方程为dp[i - 1] > 0时，dp[i] = dp[i - 1] + nums[i]或dp[i] = max(dp[i - 1] + nums[i], nums[i])。后者可以不用数组节省空间复杂度。

Version:python
~~~python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        n = len(nums)
        # create a new array, thus spatial O(n)
        dp = [0 for _ in range(n)]
        dp[0] = nums[0]
        res = dp[0]
        for i in range(1, n):
            if dp[i - 1] >= 0:
                dp[i] = dp[i - 1] + nums[i]
            else:
                dp[i] = nums[i]
        return max(dp)
~~~
