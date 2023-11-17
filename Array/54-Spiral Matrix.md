要输出螺旋的矩阵

基本思路：首先设置上下左右的边界。然后先从左往右遍历行，遍历完修改上边界；然后从上往下遍历列，遍历完修改右边界；然后从右往左遍历行，遍历完修改下边界；然后从下往上遍历列，遍历完修改左边界。越界条件是上下左右边界的值。

注意范围，左闭右开

Version:python
~~~python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        m, n = len(matrix), len(matrix[0])    # get row, col value
        res = []
        upper, down, left, right = 0, m - 1, 0, n - 1
        while True:
            for i in range(left, right + 1):
                res.append(matrix[upper][i])
            upper = upper + 1
            if upper > down: break
            for i in range(upper, down + 1):
                res.append(matrix[i][right])
            right = right - 1
            if right < left: break
            for i in range(right, left - 1, -1):
                res.append(matrix[down][i])
            down = down - 1
            if down < upper: break
            for i in range(down, upper - 1, -1):
                res.append(matrix[i][left])
            left = left + 1
            if left > right: break
        return res
~~~
