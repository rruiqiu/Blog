## Insert Interval

```python

```

## Merge Intervals

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        # sort based on the first index first
        res = []
        if not intervals:
            return []
            
        intervals.sort()
        res.append(intervals[0])
        for i in range(1, len(intervals)):
            if intervals[i][0] <= res[-1][1]:
                res[-1][1] = max(res[-1][1], intervals[i][1])
            else:
                res.append(intervals[i])
        
        return res
```



## Meeting Rooms

```python
class Solution:
    def canAttendMeetings(self, intervals: List[Interval]) -> bool:
        intervals.sort(key = lambda i:i.start)
        for i in range(1, len(intervals)):
            if intervals[i].start >= intervals[i - 1].end:
                continue
            else:
                return False
        return True
```

## Meeting Rooms II

The core is we sort the given intervals first based on the start time then we loop each interval, compare the start time if is greater than the minimum end times in the heap. The reason to use a heap is that we could encounter several same start time but different end times, so we want to maintain the end time of each meeting room.

```python
class Solution:
    def minMeetingRooms(self, intervals: List[Interval]) -> int:
        intervals.sort(key=lambda x: x.start)
        min_heap = []

        for interval in intervals:
            if min_heap and min_heap[0] <= interval.start:
                heapq.heappop(min_heap)
            heapq.heappush(min_heap, interval.end)

        return len(min_heap)
```

