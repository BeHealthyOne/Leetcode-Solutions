# 方法一、栈
路径符号'/'不用管，所以用split进行分割。然后对分割后的进行讨论

Version:python
~~~python
class Solution:
    def simplifyPath(self, path: str) -> str:
        names = path.split('/')
        stack = list()
        for name in names:
            if name == '..':
                if stack:
                    stack.pop()
            elif name and name != '.':
                stack.append(name)
        return '/' + '/'.join(stack)
~~~
