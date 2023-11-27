# 方法一、快慢指针
在一个数组中查找重复的元素。因为元素的个数少于数组长度，所以可以形成元素的值与下标的映射关系。例如对于数组[1,3,4,2,2]，下标为[0,1,2,3,4]，nums[0] = 1, nums[1] = 3, nums[3] = 2, nums[2] = 4, nums[4] = 2, nums[2] = 4。就会形成1->3->2->4->2->4>

因此可以生成类似链表的环形结构，因此可以考虑使用快慢指针来查找重复的元素。快慢指针的原理可以通过画图便于理解，快指针一次走两步，慢指针一次走一步，当快慢指针在环中相遇时，设环外长度为a， 慢指针在环中走的长度为b，则快指针走的长度为2(a + b)。快指针的另一种表达方式是a + b + kL（k倍的环长）。则b = kL - a or a + b = kL再次相遇的时候就是环的起点。

Version:python
~~~python
class Solution:
    def findDuplicate(self, nums: List[int]) -> int:
        slow, fast = 0, 0
        slow, fast = nums[slow], nums[nums[fast]]
        while slow != fast:
            slow = nums[slow]
            fast = nums[nums[fast]]
        pre1 = 0
        pre2 = slow
        while pre1 != pre2:
            pre1 = nums[pre1]
            pre2 = nums[pre2]
        return pre1
~~~
