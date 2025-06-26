## 1D Dynamic Programming







## Climbing Stairs

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        # 1,1,1
        # 1,2
        # 2,1

        # i feel like sometimes is hard to find the recursion function
        # dp = [0] * n

        # for i in range(n):
        #     dp[]

        # n = 2, 2
        # n =3, 3
        # if u find the state function, then it will come eaisly
        if n == 1:
            return 1
        first = 1
        second = 2
        
        for i in range(3,n+1):
            third = first + second
            first = second
            second = third
        
        return second

        # def recursion(n, i):
        #     if i == n:
        #         print()
        #         return 1
        #     if i > n:
        #         return 0
            
        #     return recursion(n, i+1) + recursion(n, i +2)
        
        # return recursion(n,0)
```

## House Robber

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        n = len(nums)
        if n == 0:
            return 0
        if n == 1:
            return nums[0]
        if n == 2:
            return max(nums[0], nums[1])
        
        # dp = [0] * n
        # dp[0] = nums[0]
        # dp[1] = max(nums[0], nums[1])
        prev2, prev1 = 0,0
        prev2 = nums[0]
        prev1 = max(nums[0], nums[1])

        for i in range(2,n):
            # dp[i] = max(dp[i-1], dp[i-2]+nums[i])
            temp = max(prev1, nums[i] + prev2)
            prev2 = prev1
            prev1 = temp
        return prev1
```

## House Robber II

```python
class Solution:
    def rob(self, nums: List[int]) -> int:
        #just treat this as either nums[:-1], not include the last number to end or nums[1:]
        n = len(nums)
        if n == 1:
            return nums[0]
        if n == 2:
            return max(nums[0], nums[1])
        def houserobber(arr):
            # print(arr)
            first,second = arr[0], max(arr[1], arr[0])
            for i in range(2,n - 1):
                temp = max(second, first + arr[i])
                first = second
                second = temp
            return second
        
        return max(houserobber(nums[:n-1]), houserobber(nums[1:]))
```

## Longest Palindromic Substring

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        def expandAroundCenter(left: int, right: int) -> str:
            while left >= 0 and right < len(s) and s[left] == s[right]:
                left -= 1
                right += 1
            return s[(left + 1):right]  # The valid palindrome window, cuz left and right would go one step too far when condition fails

        res = ""
        for i in range(len(s)):
            # Odd-length
            odd = expandAroundCenter(i, i)
            # Even-length
            even = expandAroundCenter(i, i + 1)
            # Pick the longer one
            if len(odd) > len(res):
                res = odd
            if len(even) > len(res):
                res = even
        return res
```

## Palindromic Substrings

```python
class Solution:
    def countSubstrings(self, s: str) -> int:
        #similar to the expansion,
        count = 0
        n = len(s)
        def expansion(left,right):
            temp_count = 0
            while left >= 0 and right < n and s[left] == s[right]:
                left -= 1
                right += 1
                temp_count += 1
            return temp_count

        for i in range(n):
            count += expansion(i,i) #expansion from center
            count += expansion(i,i+1) #even

        return count
```

## Decode Ways

```python
class Solution:
    def numDecodings(self, s: str) -> int:
        # 2236, 2,2,3,6,  
        n = len(s)
        dp = [0] * (n+1)
        dp[0] = 1
        if s[0] != '0':
            dp[1] = 1
        else:
            dp[1] = 0

        for i in range(2,n+1):
            one_digit = int(s[i - 1])
            two_digits = int(s[i - 2:i])

            if one_digit != 0:
                dp[i] = dp[i - 1]

            if 10 <= two_digits <= 26:
                dp[i] += dp[i - 2]
        print(dp)
        return dp[n]
```

