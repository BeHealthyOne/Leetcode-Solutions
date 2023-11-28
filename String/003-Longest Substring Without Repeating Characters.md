# 方法一、滑动窗口
在一个数组中查找最长长度的子数组，都可以使用滑动窗口方法。查找重复的元素可以使用hashtable（c++）， set（python）。如果遇到重复的元素，就不断弹出左边的元素，知道不发生重复为止。

Version:python
~~~python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        n = len(s)
        lookup = set()
        cnt, maxcnt = 0, 0
        left = 0
        for i in range(n):
            cnt = cnt + 1
            while s[i] in lookup:
                lookup.remove(s[left])
                cnt = cnt - 1
                left = left + 1  
            maxcnt = max(maxcnt, cnt)
            lookup.add(s[i])
        return maxcnt
~~~
