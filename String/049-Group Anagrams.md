# 方法一、排序
因为每个字符串包含的字母都是一样的，所以对字符串排序后，相同的字符串可以用hash表来保存。

Version:python
~~~python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        mp = collections.defaultdict(list)    # 创建一个值为默认空列表的字典

        for str in strs:
            key = "".join(sorted(str))    # 将排序后的字符连接成字符串
            mp[key].append(str)
        return list(mp.values())
~~~

# 方法二、计数
因为每个字符串中每个字符的数目是固定的，所以用26个字符出现次数作为下标也可以记录对应的字符串。

Version:python
~~~python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        mp = collections.defaultdict(list)
        for str in strs:
            count = [0] * 26
            for st in str:
                count[ord(st) - ord('a')] += 1
            mp[tuple(count)].append(str)
        return list(mp.values()) 
~~~
