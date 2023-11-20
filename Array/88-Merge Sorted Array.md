# 方法一、内置函数（邪道）
先插入，后sort。

# 方法二、指针
从后面遍历，用两个指针比较大小，一个额外的指针存储当前的位置。

注意，当第一个数组只有一个元素时，需要考虑下标小于0的情况

Version:python
~~~python
class Solution:
    def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
        if n == 0: return
        rear1, rear2, rear = m - 1, n - 1, m + n - 1
        while rear2 >= 0 and rear >= 0:
            if rear1 < 0 or nums1[rear1] <= nums2[rear2]:
                nums1[rear] = nums2[rear2]
                rear2 = rear2 - 1
            else:
                nums1[rear], nums1[rear1] = nums1[rear1], nums1[rear]
                rear1 = rear1 - 1
            rear = rear - 1
        return 
~~~
