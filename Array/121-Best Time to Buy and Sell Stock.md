# 方法一、动态规划
类似于最大子序列，可以采用动态规划的算法。

动态规划的关键：状态的定义、状态转移方程和状态的初值定义。这里状态可以定义为dp[i]表示第i天的最大利润，状态转移方程为dp[i] = max(dp[i - 1], prices[i] - minprice)。初值定义为dp[0] = 0

Version:python
~~~python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        days = len(prices)
        dp = [0] * days
        dp[0] = 0
        minprice = prices[0]
        for i in range(1, days):
            minprice = min(minprice, prices[i])
            dp[i] = max(dp[i - 1], prices[i] - minprice)
        return dp[-1]
~~~

因为只用了数组中相邻的位置，所以可以不用定义一个空的数组，能够节省空间复杂度。
