# 方法一、栈
用栈的思想匹配括号。

注意，如果输入数组的长度为奇数，必然失败；如果遍历后栈不为空，也是失败。

Version:python
~~~python
class Solution:
    def isValid(self, s: str) -> bool:
        if len(s) % 2 != 0: return False
        kuohao = {
            ')': '(', 
            '}': '{',
            ']': '[' 
        }
        zhan = list()
        for i in range(len(s)):
            if s[i] in ['(', '[', '{']:
                zhan.append(s[i])
            else:
                if len(zhan) == 0 or zhan[-1] != kuohao[s[i]]:
                    return False
                else: 
                    zhan.pop()
        return len(zhan) == 0
~~~
