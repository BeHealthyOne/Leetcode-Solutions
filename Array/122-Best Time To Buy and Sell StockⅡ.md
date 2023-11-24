# 方法一、动态规划

类似于121题，只不过这题可以多次买卖股票，因此需要对状态的定义做修改。因为买股票会支出，而卖股票有收入，结合之前的滚动数组。可以求解

Version:python
~~~python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        days = len(prices)
        money = 0    # 手中无股票时的现金数目
        stock = -prices[0]    # 手中持有股票时的现金数目
        for i in range(1, days):
            money = max(money, stock + prices[i])    # 卖出股票后现金数目的最大值
            stock = max(stock, money - prices[i])    # 买入股票后现金数目的最大值
        return money    # 因为最后肯定是卖出股票增加手中的现金，所以返回的是money
~~~
