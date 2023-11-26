# 方法一、回溯+剪枝
**求解所有可能性，就应该想到回溯（dfs）。** 回溯结束的条件是和大于目标值，超出给定个数，超出1-9的范围。

Version:python
~~~python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        totalSolutions = []
        if k == n and k == 1: 
            totalSolutions.append([1])
            return totalSolutions
        if k > n // 2 or n > 9 * k or k == n: return totalSolutions
        
        def Search(num, Sum, oneSolution):
            if Sum == 0 and len(oneSolution) == k:
                totalSolutions.append(oneSolution[:])
                return 
            if num > 9:
                return 
            if Sum < 0:
                return 
            if len(oneSolution) > k:
                return 
            Search(num + 1, Sum - num, oneSolution + [num])    # 选中这个数
            Search(num + 1, Sum, oneSolution)    # 没选这个数

        Search(1, n, [])

        return totalSolutions
~~~
