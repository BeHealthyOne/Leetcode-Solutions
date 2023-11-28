# 方法一、回溯
找所有解决方案的经典思路：回溯。本体需要建立字典，然后对字典中的元素进行遍历。

Version:python
~~~python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if len(digits) == 0:
            return []  

        phoneMap = {
            "2":"abc",
            "3":"def",
            "4":"ghi",
            "5":"jkl",
            "6":"mno",
            "7":"pqrs",
            "8":"tuv",
            "9":"wxyz",
        }

        def dfs(index):
            if index == len(digits):
                combinations.append("".join(combination))
                return
            else:
                digit = digits[index]    # 获取对应下标的元素
                for letter in phoneMap[digit]:
                    combination.append(letter)
                    dfs(index + 1)    # 深一层遍历
                    combination.pop()    # 弹出列表尾部的元素
        combination = list()
        combinations = list()
        dfs(0)
        return combinations
~~~
