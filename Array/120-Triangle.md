# 方法一、迭代

最容易想到的是迭代方法，也就是dfs。但是会超出时间限制

注意想要通过函数修改python变量，可以使用数组来存储。

Version:python
~~~python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        res = [100000]
        rows = len(triangle)
        path = triangle[0][0]

        if rows == 1: return path

        def dfs(triangle, row, col, path, res):
            nrow, ncol1, ncol2 = row + 1, col, col + 1
            if nrow >= rows:
                res[0] = min(path, res[0])
                return 
            else:
                left = path + triangle[nrow][ncol1]
                right = path + triangle[nrow][ncol2]
                dfs(triangle, nrow, ncol1, left, res)
                dfs(triangle, nrow, ncol2, right, res)

        dfs(triangle, 0, 0, path, res)
    
        return res[0]
~~~

# 方法二、动态规划
如果要求出某种方案的值，应该首先想到动态规划。

动态规划的核心是状态的定义和状态转移方程。状态可以定义为dp[i]，其中dp[i]表示从第i个元素到结尾的路径之和。状态转移方程为dp[i] = min(dp[i], dp[i + 1]) + triangle[i]

Version:python
~~~python
class Solution:
    def minimumTotal(self, triangle: List[List[int]]) -> int:
        n = len(triangle)
        dp = [0] * (n + 1)
        for i in range(n - 1, -1, -1):
            for j in range(i + 1):
                dp[j] = min(dp[j], dp[j + 1]) + triangle[i][j]
        return dp[0]
~~~
