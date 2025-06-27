## Priority Queue (Heap)

- A **heap** is a binary tree where the parent node is smaller (`min-heap`) or larger (`max-heap`) than its children.
- Python’s `heapq` implements a **min-heap**.
- For **max-heap**, insert negative values.

![min_heap_and_max_heap](Priority Queue(Heap).assets/min_heap_and_max_heap-1750876649725-2.png)

### 🧮 Time Complexity

| Operation       | Time Complexity |
| --------------- | --------------- |
| `heappush()`    | O(log n)        |
| `heappop()`     | O(log n)        |
| `heapify()`     | O(n)            |
| `heapreplace()` | O(log n)        |
| `nsmallest()`   | O(n log k)      |

### Syntax

```python
import heapq

# Min-Heap, by default Python using min heap
min_heap = []
for num in [3, 1, 5]:
    heapq.heappush(min_heap, num)
print("Top of Min-Heap:", heap[0])  # → 1
print("Min-Heap pop:", heapq.heappop(min_heap))  # → 1

# Max-Heap using negation
max_heap = []
for num in [3, 1, 5]:
    heapq.heappush(max_heap, -num)
print("Top of Max-Heap:", -max_heap[0])  # → 5
print("Max-Heap pop:", -heapq.heappop(max_heap))  # → 5, notice the minus sign

# Heapify a list
arr = [4, 2, 7, 1]
heapq.heapify(arr)
print("Heapified array:", arr)  # → [1, 2, 7, 4] or similar heap order
```

## Find Median From Data Stream

![image-20250625165234530](Priority Queue(Heap).assets/image-20250625165234530.png)

```python
class MedianFinder:

    def __init__(self):
        # two heaps, heap should have equal size
        # 3 2 7 4
        # rebalance the heap, every elements in small heap < large_heap[0]
        self.small_heap = [] # max heap, default
        self.large_heap = [] # min heap

    def addNum(self, num: int) -> None:
        # when the length of the two heap difference > 1, rebalance the heap
        # check where to add
        # rebalance based on the 2 heap lengths
        if not self.small_heap:
            heapq.heappush(self.small_heap, -num)
        elif num > -self.small_heap[0]:
            heapq.heappush(self.large_heap, num)
            # balance
            if len(self.large_heap) - len(self.small_heap) > 1:
                val = heapq.heappop(self.large_heap)
                heapq.heappush(self.small_heap, -val)
        else:
            heapq.heappush(self.small_heap, -num)
            if len(self.small_heap) - len(self.large_heap) > 1:
                val = -heapq.heappop(self.small_heap)
                heapq.heappush(self.large_heap, val)

    def findMedian(self) -> float:
        # check the length
        if len(self.small_heap) == len(self.large_heap):
            res = (-self.small_heap[0] + self.large_heap[0]) / 2
            return res
        elif len(self.small_heap) > len(self.large_heap):
            return -self.small_heap[0]
        else:
            return self.large_heap[0]
```

