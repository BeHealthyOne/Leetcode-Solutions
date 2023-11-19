类似54题，需要对4个边界进行处理。

注意：python创建二阶矩阵的方法；

Version:python
~~~python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        matrix = [[0 for _ in range(n)] for _ in range(n)]
        num, target = 1, n * n
        upper, down, left, right = 0, n - 1, 0, n - 1
        while num <= target:
            for j in range(left, right + 1):
                matrix[upper][j] = num
                num = num + 1
            upper = upper + 1
            if upper > down: break

            for j in range(upper, down + 1):
                matrix[j][right] = num
                num = num + 1
            right = right - 1
            if right < left: break

            for j in range(right, left - 1, -1):
                matrix[down][j] = num
                num = num + 1
            down = down - 1
            if down < upper: break

            for j in range(down, upper - 1, -1):
                matrix[j][left] = num
                num = num + 1
            left = left + 1
            if left > right: break
        return matrix
~~~

