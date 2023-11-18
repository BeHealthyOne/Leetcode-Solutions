# 方法一、迭代

思路：首先往包含空集的res结果数组中添加第一个元素，然后用res中的每个元素与第二个元素相组合存储到res中。之后类似上一步。

Version:python
~~~python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = [[]]
        for num in nums:
            res = res + [[num] + i for i in res]
        return res
~~~

# 方法二、DFS

深度优先搜索算法：

Version:python
~~~python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        res = []
        n = len(nums)
        def dfs(i, tmp):
            res.append(tmp)
            for j in range(i, n):
                dfs(j + 1, tmp + [nums[j]])
        dfs(0, [])
        return res
~~~
