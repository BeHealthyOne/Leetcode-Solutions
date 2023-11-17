思路：首先进行按照间隔的第一个元素排序。创建结果数组，对间隔数组进行遍历，如果结果数组为空或者，结果数组中倒数第一个元素的第二个元素小于间隔的第一个元素就将该间隔存储到结果数组中。

Version:python
~~~python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        intervals.sort(key=lambda x: x[0])    # sort by the first element
        res = []
        for interval in intervals:
            if not res or res[-1][1] < interval[0]:
                res.append(interval)
            else:
                res[-1][1] = max(res[-1][1], interval[1])
        return res
~~~
