**求所有可行解的问题，一般需要用到dfs**。

以target值为树的根结点，减去数组中的值，生成子树。依次进行，直到根结点的值为0，中间的路径就是生成的结果。其中dfs的参数包括数组，数组长度，结果，目标值（改变），开始（改变，从数组中的哪个元素开始遍历），路径（改变，用于保存中途结点）

Version:python
~~~python
class Solution:
    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        def dfs(candidates, begin, size, path, res, target):
            if target < 0:
                return
            if target == 0:
                res.append(path)
                return

            for index in range(begin, size):
                dfs(candidates, index, size, path + [candidates[index]], res, target - candidates[index])
        res = []
        size = len(candidates)
        if size == 0: return res
        path = []
        dfs(candidates, 0, size, path, res, target)
        return res
~~~
