# 方法一、回溯+剪枝

对于寻找解决方案的一类问题，最常用的就是回溯算法。但是回溯由于会有重复项，导致时间浪费，需要进行剪枝，在本题中，如何筛出已经查找过的元素就是剪枝。而回溯最常用的就是深度遍历算法。

* 深度遍历算法的参数：矩阵的行和列，word字符中的位置；
* 深度遍历算法的终止条件：如果下标越界，或者当前的元素不等于word字符中的值，或者访问的元素已经访问过


Version:python
~~~python
class Solution:
    def exist(self, board: List[List[str]], word: str) -> bool:
        h, w = len(board), len(board[0])
        def dfs(i, j, k):
            if not (0 <= i < h and 0 <= j < w) or board[i][j] != word[k]: return False
            if k == len(word) - 1: return True
            # 前面已经确定等于word[k]，所以可以暂时置空，筛除重复的元素
            board[i][j] = ''
            res = dfs(i - 1, j, k + 1) or dfs(i + 1, j, k + 1) or dfs(i, j - 1, k + 1) or dfs(i, j + 1, k + 1)
            board[i][j] = word[k]
            return res
        for i in range(h):
            for j in range(w):
                if dfs(i, j, 0):
                    return True
        return False
~~~
