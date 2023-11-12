# 方法一、逐列求

python比较容易超时。

思路：对于每一列找到该列左边和右边列最高的值，比较出两者中最小的值。如果最小的列高度高于当前列的高度，就用最小列高度减去当前列高度。

Version:Java
~~~java
class Solution {
    public int trap(int[] height) {
        int sum = 0;
        //最两端的列不用考虑，因为一定不会有水。所以下标从 1 到 length - 2
        for (int i = 1; i < height.length - 1; i++) {
            int max_left = 0;
            //找出左边最高
            for (int j = i - 1; j >= 0; j--) {
                if (height[j] > max_left) {
                    max_left = height[j];
                }
            }
            int max_right = 0;
            //找出右边最高
            for (int j = i + 1; j < height.length; j++) {
                if (height[j] > max_right) {
                    max_right = height[j];
                }
            }
            //找出两端较小的
            int min = Math.min(max_left, max_right);
            //只有较小的一段大于当前列的高度才会有水，其他情况不会有水
            if (min > height[i]) {
                sum = sum + (min - height[i]);
            }
        }
        return sum;
    }
}
~~~

# 方法二、动态规划

注意到方法一中对于每一列都重复地计算了列左边和列右边的高度，所以可以用动态规划的思想，**将列左边和列右边的最大高度存储到一个数组中**。

Version:python

~~~python
class Solution:
    def trap(self, height: List[int]) -> int:
        sum = 0
        n = len(height)
        max_left = [0] * n    # apply for n size space
        max_right = [0] * n
        for j in range(1, n - 1):
            max_left[j] = max(max_left[j - 1], height[j - 1])    # compare left & max_left
        j = n - 2
        while j >= 0:
            max_right[j] = max(max_right[j + 1], height[j + 1])
            j = j - 1
        for i in range(1, n - 1):
            minof2 = min(max_left[i], max_right[i])
            if minof2 > height[i]: sum = sum + minof2 - height[i]
        return sum
~~~

# 方法三、双指针

对于方法二，注意到max_left和max_right数组均只使用了1次，所以可以用临时变量来代替。但是一个是从左到右，一个是从右到左，只能用双指针

Version:python
~~~python
class Solution:
    def trap(self, height: List[int]) -> int:
        sum = 0
        n = len(height)
        max_left, max_right = 0, 0
        left, right = 1, n - 2
        for i in range(1, n - 1):    # (1, n - 2)
            if height[left - 1] < height[right + 1]:
                # 此时左边的列较低
                max_left = max(max_left, height[left - 1])
                minH = max_left
                if minH > height[left]: sum = sum + minH - height[left]
                left = left + 1
            else:
                max_right = max(max_right, height[right + 1])
                minH = max_right
                if minH > height[right]: sum = sum + minH - height[right]
                right = right - 1
        return sum
~~~





