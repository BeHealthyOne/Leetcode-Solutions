# 方法一、回溯
生成所有解决方案就想到回溯。注意剪枝，剪掉不符合条件的情况

Version:python
~~~python
class Solution:
    def generateParenthesis(self, n: int) -> List[str]:
        res = []
        def dfs(num, left, right, temp): # 参数表示临时数组长度，左括号和右括号的个数
            if num == 2 * n and left == right == n:
                res.append(temp)
                return 
            if right > left:
                return
            if num > 2 * n:
                return
            dfs(num + 1, left + 1, right, temp + '(')
            dfs(num + 1, left, right + 1, temp + ')')

        dfs(0, 0, 0, '')
        return res    
~~~
