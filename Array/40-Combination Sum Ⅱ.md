类似39题

不同的是不能有重复数组。采用先排序，然后在递归过程中进行判断continue掉重复的元素。

Version:python
~~~python
class Solution:
    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        candidates.sort()

        def dfs(candidates, size, path, res, begin, target):
            if target < 0: 
                return 
            if target == 0:
                res.append(path)
                return 
            for index in range(begin, size):
                if index > begin and candidates[index] == candidates[index - 1]: continue
                temp = index + 1
                dfs(candidates, size, path + [candidates[index]], res, temp, target - candidates[index])

        
        res = []
        size = len(candidates)
        if size == 0: return res
        path = []
        dfs(candidates, size, path, res, 0, target)
        return res
~~~
