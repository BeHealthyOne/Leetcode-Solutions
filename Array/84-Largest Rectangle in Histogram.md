**基础模型**：在一维数组中对每一个数找到第一个比自己小的元素。在一维数组中找到第一个满足条件的情况是单调栈的典型应用。

# 方法一、单调栈

题目要求找出存在矩形的面积的最大值，通常的思路是以数组中的某个高度为基准，扩散到相邻高度。为了得到这个最大值，需要不停地遍历数组，比较数组中某个元素与相邻元素的大小，直到找到第一个高度小于当前高度的下标。将下标相减（画个例子便于理解），乘以较小的高度，得到的就是面积的值。

这个过程可以用单调栈来确定下标的边界。

注意，为了比较边界值，可以引入哨兵。

Version:python
~~~python
class Solution:
    def largestRectangleArea(self, heights: List[int]) -> int:
        heights = [0] + height + [0]    # 引入哨兵
        stack = []
        res = 0
        for i in range(len(heights)):
            # 当栈不为空，且当前高度小于栈顶下标对应高度时=>栈顶下标对应高度的右边界已经确定
            while stack && height[i] < height[stack[-1]]:
                r = stack.pop()    # 弹出栈顶元素（下标形式）
                w = i - 1 - stack[-1] if stack else i    # 因为栈弹出栈顶元素后，栈中最后一个元素就是左边界，根据递增栈，左边界的高度肯定小于当前高度，故-1
                h = height[r]
                area = w * h
                res = max(res, area)
            stack.append(i)    # 维护的是一个递增栈
        return res
~~~
