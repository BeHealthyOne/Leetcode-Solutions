类似第63题

如果不改变原来的数组，需要辅助空间；改变原来的数组，空间复杂度就为O(1)。

Version:python
~~~python
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        h, w = len(grid), len(grid[0])
        # res = [[0 for _ in range(w)] for _ in range(h)]
        # res[0][0] = grid[0][0]
        res = grid.copy()
        for i in range(1, w):
            res[0][i] = res[0][i] + res[0][i - 1]
        for j in range(1, h):
            res[j][0] = res[j][0] + res[j - 1][0]
        for i in range(1, w):
            for j in range(1, h):
                res[j][i] = res[j][i] + min(res[j - 1][i], res[j][i - 1])
        return res[-1][-1]
~~~
