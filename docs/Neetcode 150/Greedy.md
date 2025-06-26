## * Maximum Subarray - Kadane's Algorithm

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        largest = float('-inf')
        window_sum = 0
        for num in nums:
            # compare the sum so far with the current
            # if num > (num + window_sum):
            #     window_sum = num
            # else:
            #     window_sum += num    
            window_sum = max(num, num + window_sum)
            largest = max(largest, window_sum)
        return largest
```

## Jump Game

```python
class Solution:
    def canJump(self, nums: List[int]) -> bool:
        # we can go reverse order, check if goal index can get reduce to zero
        goal = len(nums) - 1 # notice reach the last index

        for i in range(len(nums) - 1, -1, -1): # len(nums) - 2, this also works and actually better
            print(goal, nums[i] + i)
            if nums[i] + i >= goal:
                goal = i

        return True if goal == 0 else False
```

