
与15题类似

~~~python
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums.sort()
        best = 10**7
        lens = len(nums)

        # based on the abs of the absolute value of the difference update best
        def update(cur):
            nonlocal best
            if abs(cur - target) < abs(best - target):
                best = cur

        for i in range(lens):
            # skip duplicate elements
            if i > 0 and nums[i] == nums[i - 1]: continue
            L, R = i + 1, lens - 1
            while L < R:
                s = nums[i] + nums[L] + nums[R]
                if s == target:
                    return target
                update(s)
                if s > target:
                    R0 = R - 1
                    R = R0
                else:
                    L0 = L + 1
                    L = L0
        return best

~~~
