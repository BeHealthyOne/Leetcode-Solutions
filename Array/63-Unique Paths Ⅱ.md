# 方法一、动态规划

存在一定的递推形式，或者当前问题的解决方案取决于子问题的解决方案时，动态规划通常会起作用。动态规划的核心是状态的定义和状态转移方程。在本题中，可以先判断起点和终点的位置是否可行，然后再对起点、第1行和第1列进行初始化。

注意，因为矩阵不一定是n*n的方阵，需要注意矩阵的行数和列数。python生成器生成的二维数组是[[列]行]

Version:python
~~~python
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        m, n = len(obstacleGrid), len(obstacleGrid[0])    # stand for row, col
        if obstacleGrid[-1][-1] == 1 or obstacleGrid[0][0] == 1: return 0
        res = [[0 for _ in range(n)] for _ in range(m)]
        res[0][0] = 1
        for i in range(1, n):
            if obstacleGrid[0][i] == 0:
                res[0][i] = res[0][i - 1]
            else:
                res[0][i] = 0

        for i in range(1, m):
            if obstacleGrid[i][0] == 0:
                res[i][0] = res[i - 1][0]
            else:
                res[i][0] = 0

        for i in range(1, m):
            for j in range(1, n):
                if obstacleGrid[i][j] == 0:
                    res[i][j] = res[i - 1][j] + res[i][j - 1]
                else:
                    res[i][j] = 0

        return res[-1][-1]
~~~

# 方法二、滚动数组

由于动态规划的状态转移方程只用到了临近的值，且用过后就不会用到，可以选择滚动数组的方法减少空间复杂度。

Version:python
~~~python

~~~



