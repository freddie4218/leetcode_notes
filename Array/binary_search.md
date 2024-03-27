# Binary Search

>In its simplest form, Binary Search operates on a contiguous sequence with a specified left and right index. This is called the Search Space. <mark>Binary Search maintains the left, right, and middle indicies of the search space and compares the search target or applies the search condition to the middle value of the collection; if the condition is unsatisfied or values unequal, the half in which the target cannot lie is eliminated and the search continues on the remaining half until it is successful. </mark> If the search ends with an empty half, the condition cannot be fulfilled and target is not found.

```
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        left, right = 0, len(nums) - 1
        
        # 在区间 [left, right] 内查找 target
        while left < right:
            # 取区间中间节点
            mid = left + (right - left + 1) // 2
            # nums[mid] 大于目标值，排除掉不可能区间 [mid, right]，在 [left, mid - 1] 中继续搜索
            if nums[mid] > target:
                right = mid - 1 
            # nums[mid] 小于等于目标值，目标元素可能在 [mid, right] 中，在 [mid, right] 中继续搜索
            else:
                left = mid
        # 判断区间剩余元素是否为目标元素，不是则返回 -1
        return left if nums[left] == target else -1
```