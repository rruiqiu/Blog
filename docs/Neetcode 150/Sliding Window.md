## Best Time to Buy and Sell Stock

```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        max_profit = 0
        min_price = prices[0]
        
        for price in prices[1:]:
            if price < min_price:
                min_price = price
            else:
                max_profit = max(max_profit, price - min_price)
        
        return max_profit
```

## Longest Substring Without Repeating Characters

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        charSet = set()
        l = 0
        res = 0

        for r in range(len(s)):
            while s[r] in charSet:
                charSet.remove(s[l])
                l += 1
            charSet.add(s[r])
            res = max(res, r - l + 1)
        return res
```

This is an optimize approach where we store the left pointer directly.

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        mp = {}
        l = 0
        res = 0
        
        for r in range(len(s)):
            if s[r] in mp:
                l = max(mp[s[r]] + 1, l)
            mp[s[r]] = r
            res = max(res, r - l + 1)
        return res
```

## Longest Repeating Character Replacement

O(26 n)

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        count = defaultdict(int)
        l = 0
        max_len = 0

        for r, char in enumerate(s):
            # print(char)
            count[char] += 1

            while r - l + 1 - max(count.values()) > k:
                count[s[l]] -= 1
                l += 1
            
            max_len = max(max_len, r - l + 1)
        
        return max_len
        

```

O(n)

```python
class Solution:
    def characterReplacement(self, s: str, k: int) -> int:
        count = defaultdict(int)
        l = 0
        max_len = 0
        maxf = 0

        for r, char in enumerate(s):
            # print(char)
            count[char] += 1
            maxf = max(maxf, count[s[r]]) # the most frequenct chars

            while r - l + 1 - maxf > k: 
                count[s[l]] -= 1
                l += 1

            max_len = max(max_len, r - l + 1)
        
        return max_len
```

## Minimum Window Substring

```python
class Solution:
    def minWindow(self, s: str, t: str) -> str:
        T = Counter(t)
        window = defaultdict(int) # Window only track the valid keys

        needed = len(T) # We compare the match dict keys
        haved = 0

        min_len = float('inf')
        l = 0
        res = [-1, -1] # Store the index of the returned

        for r,char in enumerate(s):
            if char in T: # If a match
                window[char] += 1
                if window[char] == T[char]: # If value matches
                    haved += 1

                while haved == needed: 
                    # Update result
                    if (r - l + 1) < min_len:
                        min_len = r - l + 1
                        res = [l, r]

                    # Try to shrink window
                    left_char = s[l]
                    if left_char in T:
                        if window[left_char] == T[left_char]:
                            haved -= 1
                        window[left_char] -= 1
                    l += 1
        l, r = res
        if l != -1:            
            return s[l:r + 1]
        else:
            return ""
```

