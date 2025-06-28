# CodeSignal

Understand the question type through this [general-coding-assessment-framework.pdf](https://github.com/Leader-board/OA-and-Interviews/blob/main/media/general-coding-assessment-framework.pdf).

Recommend question order, Q1 -> Q2 > Q3 (look through the question) -> Q4 (brute force if not able to come up an optimal solution) -> Q3(finish) -> Q4(optimize)

## Q1 & Q2

For q1, straightforward, understand common used array and string manipulation methods. (5 - 10 lines of code)

For  q2, The question can be long, take time to understand the question and solve use the brute force way. (10 - 20 lines of code)

```python
# 2. String Indexing and Slicing
s = "AdvancedPython"
print(s[0])    # First character: 'A'
print(s[-1])   # Last character: 'n'
print(s[2:8])  # Substring from index 2 to 7: 'vanced'
print(s[:7])   # From beginning to index 6: 'Advance'
print(s[::2])  # Every 2nd character: 'Aaceyh'
print(s[::-1]) # Reverse the string
```

```python
# 3. Common String Methods
text = "  Hello, Python World!  "
print(text.strip())      # Remove leading and trailing whitespace
print(text.lower())      # Convert to lowercase
print(text.upper())      # Convert to uppercase
print(text.title())      # Capitalize each word
print(text.replace("Python", "C#"))  # Replace substring
print(text.find("Python"))           # Find index of substring (-1 if not found)
print(text.startswith("  Hello"))    # Check if starts with
print(text.endswith("World!  "))     # Check if ends with
print("123abc".isalnum())            # Check alphanumeric
print("123".isdigit())               # Check digits only
print("abc".isalpha())               # Check alphabetic only
```

```python
# 4. Joining and Splitting
words = ["Python", "is", "awesome"]
sentence = " ".join(words)    # Join list into a string with spaces
print(sentence)				 # Output: Python is awesome
split_words = sentence.split(" ")  # Split string back into list
print(split_words)

length = [3, 5, 7]
sentence = "#".join(length)  # ❌ TypeError: expected str, got int, join would always the iterable elements string
length = [3, 5, 7]
sentence = "#".join(map(str, length))  # ✅ "3#5#7"
sentence = "#".join([str(x) for x in length]) #Alternatively:
print(sentence)  # Output: 3#5#7

csv = "3#5#7"
split_numbers = csv.split("#") # Split a string using custom delimiter
print(split_numbers)  # Output: ['3', '5', '7']
```

## Q3 - Simulation

25 - 40 lines of code, aim to solve in 15 - 20 minutes

### [54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

```python
class Solution:
    def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
        #spiral order, from outer circle to inner circle
        #simulate boundary, use smth to record index
        res = []
        top,bottom = 0, len(matrix)-1
        left,right = 0, len(matrix[0])-1
        order_state = "right"
        while len(res) < (len(matrix) * len(matrix[0])):
            if order_state == "right":
                for i in range(left, right+1): # 123
                    res.append(matrix[top][i])
                order_state = "bottom"
                top += 1
            elif order_state == "bottom": # 69
                for j in range(top, bottom+1):
                    res.append(matrix[j][right])
                order_state = "left"
                right-=1
            elif order_state == "left":
                for i in range(right,left-1, -1): #8 7
                    res.append(matrix[bottom][i])
                order_state = "up"
                bottom -= 1
            elif order_state == "up":
                # print(bottom,top,left)
                for j in range(bottom, top-1, -1): # 4
                    res.append(matrix[j][left])
                order_state = "right"
                #increment the boundary
                left += 1
            # print(res)
        return res
```

### [59. Spiral Matrix II](https://leetcode.com/problems/spiral-matrix-ii/)

```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        #generate in spiral order

        # define the boundary
        res = [[0]*n for _ in range(n)]

        # print(res)
        left, right = 0, n
        top, bottom = 0, n
        count = 1
        state = "right"
        while count <= (n*n):
            if state == "right":
                for i in range(left, right):
                    res[top][i] = count
                    count += 1
                state = "bottom"
                top += 1
            elif state == "bottom":
                for i in range(top, bottom):
                    res[i][right-1] = count
                    count += 1
                right -= 1
                state = "left"
            elif state == "left":
                for i in range(right-1, left-1,-1):
                    res[bottom-1][i] = count
                    count += 1
                bottom -= 1
                state = "up"
            elif state == "up":
                for i in range(bottom-1, top-1,-1):
                    res[i][left] = count
                    count += 1
                left += 1
                state = "right"
            print(res)
        return res
```

### [* 48. Rotate Image](https://leetcode.com/problems/rotate-image/)

```python
class Solution:
    def rotate(self, matrix: List[List[int]]) -> None:
        """
        Do not return anything, modify matrix in-place instead.
        """
        #first transpose then mirror, also in place is hard
        n = len(matrix)
        def transpose(matrix):
            for i in range(len(matrix)):
                for j in range(i):
                    matrix[i][j], matrix[j][i] = matrix[j][i], matrix[i][j]

        transpose(matrix)
        # print(matrix)
        def mirror(matrix):
            for i in range(n):
                for j in range(n//2):
                    matrix[i][j],matrix[i][n-j-1] = matrix[i][n-j-1], matrix[i][j]
        mirror(matrix)
```

### * [498. Diagonal Traverse](https://leetcode.com/problems/diagonal-traverse/)

Got a similar one in the q3. Which request traverse 4 directions.

```python
class Solution:
    def findDiagonalOrder(self, mat: List[List[int]]) -> List[int]:
        # feel like just going through up and down ?
        res = []
        state = "up"
        r, c = 0, 0
        m = len(mat)
        n = len(mat[0])
        def isvalid(r, c):
            if 0 <= r < m and 0 <= c < n:
                return True
            else:
                return False
        #change each state based on the valid condition
        while len(res) < (m *n):
            if state == "up":
                while isvalid(r, c):
                    res.append(mat[r][c])
                    r -= 1
                    c += 1 
                r += 1
                c -= 1     
                state = "down"
                if c < (n-1):
                    c += 1
                else:
                    r += 1
            elif state == "down":
                while isvalid(r, c):
                    res.append(mat[r][c])
                    r += 1
                    c -= 1
                r -= 1
                c += 1
                state = "up"
                if r < (m-1):
                    r += 1
                else:
                    c += 1
            # print(res, r, c)
        return res
```

### [566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)

```python
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:
        #if legal
        m = len(mat)
        n = len(mat[0])
        if not m *n == r *c: return mat

        res = [[0] *c for _ in range(r)]

        # print(res)
        flat = []
        for i in range(m):
            for j in range(n):
                flat.append(mat[i][j])
        
        for i in range(len(flat)):
            # 12
            # if i:
            row = i // c
            col = i % c
            res[row][col] = flat[i]
            # print(res,row,col)
            # else:
            #     res[0][0] = flat[i]
            
        return res
```

[566. Reshape the Matrix](https://leetcode.com/problems/reshape-the-matrix/)

```python
class Solution:
    def matrixReshape(self, mat: List[List[int]], r: int, c: int) -> List[List[int]]:
        m, n = len(mat), len(mat[0])
        if not m *n == r *c: return mat

        res = [[0] *c for _ in range(r)]

        # print(res)
        flat = []
        for i in range(m):
            for j in range(n):
                flat.append(mat[i][j])
        
        for i in range(len(flat)):
            row = i // c
            col = i % c
            res[row][col] = flat[i]
        return res
```

### [766. Toeplitz Matrix](https://leetcode.com/problems/toeplitz-matrix/)

```python
class Solution:
    def isToeplitzMatrix(self, matrix: List[List[int]]) -> bool:
        m, n = len(matrix), len(matrix[0])
        
        for i in range(1, m):
            for j in range(1, n):
                if matrix[i][j] != matrix[i - 1][j - 1]:
                    return False
        
        return True
```

### [835. Image Overlap](https://leetcode.com/problems/image-overlap/)

```python
from collections import defaultdict
from typing import List

class Solution:
    def largestOverlap(self, img1: List[List[int]], img2: List[List[int]]) -> int:
        n = len(img1)
        ones1 = []
        ones2 = []

        # Step 1: Record positions of 1s
        for i in range(n):
            for j in range(n):
                if img1[i][j] == 1:
                    ones1.append((i, j))
                if img2[i][j] == 1:
                    ones2.append((i, j))

        # Step 2: Count all translation vectors from img1 -> img2
        vector_count = defaultdict(int)
        for x1, y1 in ones1:
            for x2, y2 in ones2:
                dx = x2 - x1
                dy = y2 - y1
                vector_count[(dx, dy)] += 1
            print(vector_count)
        # Step 3: Return the maximum overlap
        return max(vector_count.values() or [0])
```

### [2373. Largest Local Values in a Matrix](https://leetcode.com/problems/largest-local-values-in-a-matrix/)

```python
class Solution:
    def largestLocal(self, grid: List[List[int]]) -> List[List[int]]:
        n = len(grid)
        maxLocal = [[0] * (n - 2) for _ in range(n - 2)]

        for i in range(1, n - 1):
            for j in range(1, n - 1):
                tempMax = float('-inf')
                # Traverse the 3x3 subgrid centered at (i, j)
                for r in range(i - 1, i + 2):
                    for c in range(j - 1, j + 2):
                        tempMax = max(tempMax, grid[r][c])
                maxLocal[i - 1][j - 1] = tempMax

        return maxLocal

```

### [867. Transpose Matrix](https://leetcode.com/problems/transpose-matrix/)

```python
class Solution:
    def transpose(self, matrix: List[List[int]]) -> List[List[int]]:
        
        m, n = len(matrix), len(matrix[0])
        trans = [[0] * m for _ in range(n)]

        for i in range(m):
            for j in range(n):
                trans[j][i] = matrix[i][j]

        return trans
```

### [68. Text Justification](https://leetcode.com/problems/text-justification/) - Low chance

```python
class Solution:
    def fullJustify(self, words: List[str], maxWidth: int) -> List[str]:
        n = len(words)
        word_arr = []
        word_arr_len = []
        curr_len = 0
        temp = []
        temp_len = []
        
        for word in words:
            word_len = len(word)
            if word_len + curr_len + len(temp)-1 < maxWidth:
                temp.append(word)
                temp_len.append(len(word))
                curr_len += len(word)
            else:
                word_arr.append(temp)
                word_arr_len.append(temp_len)
                curr_len = len(word)
                temp = [word]
                temp_len = [len(word)]
        word_arr.append(temp)
        word_arr_len.append(temp_len)
        #now justify the length, handle the last row separately
        for i in range(len(word_arr)):
            remain_space = maxWidth - sum(word_arr_len[i])
            # print(remain_space)
            empty_slot = len(word_arr[i]) - 1
            if i != len(word_arr)-1 and empty_slot != 0:
                for j in range(remain_space): # add space after equally
                    insert_index = j % empty_slot
                    word_arr[i][insert_index] += ' '
            elif empty_slot == 0:
                for _ in range(remain_space):
                    word_arr[i][-1] += ' '
            
            else:
                for j in range(empty_slot):
                    word_arr[i][j] += ' '
                
                for _ in range(remain_space - empty_slot):
                    word_arr[i][-1] += ' '
        res = []
        for i in range(len(word_arr)):
            res.append(''.join(word_arr[i]))

        print(word_arr, word_arr_len)
        return res
```



## Q4 - Algorithm

20 - 35 lines of code.



