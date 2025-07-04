# Graphs

## BFS on Graphs

```python
def bfs(root):
    queue = deque([root])
    visited = set([root])
    while len(queue) > 0:
        node = queue.popleft()
        for neighbor in get_neighbors(node):
            if neighbor in visited:
                continue
            queue.append(neighbor)
            visited.add(neighbor)
```

## DFS on Graphs

```python
def dfs(root, visited):
    for neighbor in get_neighbors(root):
        if neighbor in visited:
            continue
        visited.add(neighbor)
        dfs(neighbor, visited)
```



## * Number of Islands

DFS is more preferred for this question

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        # bfs
        directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]
        m = len(grid)
        n = len(grid[0])
        count = 0

        def dfs(i, j):
            if not (0 <= i < m and 0 <= j < n):
                return
            if grid[i][j] != '1':
                return
            grid[i][j] = '0'    
            for dx, dy in directions:
                dfs(i + dx, j + dy)
            return
        
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    dfs(i, j)
                    count += 1
        
        return count
```

BFS

```python
class Solution:
    def numIslands(self, grid: List[List[str]]) -> int:
        #adjacent horizontally and vertically
        #notice it is char instead of int
        #m,n is greater than 1
        #can only be 0 and 1, char

        m = len(grid)
        n = len(grid[0])

        edges = [(-1,0),(1,0),(0,-1),(0,1)]

        def bfs(grid,i,j):
            queue = deque([(i,j)])
            
            while queue:
                r,c = queue.popleft()
                #check 4 directions
                for dr,dc in edges:
                    n_r,n_c = r+dr,c+dc
                    if 0 <= n_r < len(grid) and 0 <= n_c < len(grid[0]) and grid[n_r][n_c] == '1':
                        grid[n_r][n_c] = '0' #mark as visited
                        queue.append((n_r,n_c))
            # print(grid)

        count = 0
        #bfs constantly checking the grid
        for i in range(m):
            for j in range(n):
                if grid[i][j] == '1':
                    count += 1
                    bfs(grid,i,j)

        return count
```

## Max Area of Island (Bottom up)

```python
class Solution:
    def maxAreaOfIsland(self, grid: List[List[int]]) -> int:
        max_area = 0
        m = len(grid)
        n = len(grid[0])
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]

        def dfs(x, y) -> int:
            if not (0 <= x < m and 0 <= y < n and grid[x][y] == 1):
                return 0
            area = 1
            grid[x][y] = 0
            for dx, dy in directions:
                area += dfs(x + dx, y + dy)
            return area

        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    max_area = max(dfs(i, j), max_area)

        return max_area
```



## Clone Graph

```python
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        # hashmap [oldNode, newNode]
        old_to_new = {}

        def dfs(node):
            if node in old_to_new:
                return old_to_new[node]
            
            copy = Node(node.val)
            old_to_new[node] = copy
            for neighbour in node.neighbors:
                copy.neighbors.append(dfs(neighbour))

            return copy
        
        return dfs(node) if node else None
```

## Islands and Treasure - Multi source BFS

The term **multi-source BFS** refers to the fact that **you are starting your breadth-first search (BFS) from multiple sources simultaneously**, rather than just one. In this question, we start the bfs from mutiple treasures at the same time interval.

```python
class Solution:
    def islandsAndTreasure(self, grid: List[List[int]]) -> None:
        m, n = len(grid), len(grid[0])
        INF = 2147483647
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        q = deque()

        # Add all treasures (0s) to the queue
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 0:
                    q.append((i, j))

        # Multi-source BFS
        while q:
            x, y = q.popleft()
            for dx, dy in directions:
                nx, ny = x + dx, y + dy
                if 0 <= nx < m and 0 <= ny < n and grid[nx][ny] == INF:
                    grid[nx][ny] = grid[x][y] + 1
                    q.append((nx, ny))

```



## * Rotting Fruit -  Multisource BFS

```python
class Solution:
    def orangesRotting(self, grid: List[List[int]]) -> int:
        directions = [(0, 1), (0, -1), (1, 0), (-1, 0)]
        m = len(grid)
        n = len(grid[0])
        fresh = 0
        q = deque()

        for i in range(m):
            for j in range(n):
                if grid[i][j] == 2:
                    q.append((i, j))
                elif grid[i][j] == 1:
                    fresh += 1

        minute = 0
        while q and fresh > 0:
            for _ in range(len(q)):
                x, y = q.popleft()

                for dx, dy in directions:
                    nx, ny = x + dx, y + dy
                    if 0 <= nx < m and 0 <= ny < n and grid[nx][ny] == 1:
                        grid[nx][ny] = 2
                        fresh -= 1
                        q.append((nx, ny))
            minute += 1

        return minute if fresh == 0 else -1
```



## * Course Schedule

```python
class Solution:
    def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
        indegree = [0] * numCourses
        adj = [[] for i in range(numCourses)]
        for src, dst in prerequisites:
            indegree[dst] += 1
            adj[src].append(dst)

        q = deque()
        for n in range(numCourses):
            if indegree[n] == 0:
                q.append(n)
        
        finish = 0
        while q:
            node = q.popleft()
            finish += 1
            for nei in adj[node]:
                indegree[nei] -= 1
                if indegree[nei] == 0:
                    q.append(nei)
                
        return finish == numCourses
```

## * Number of Connected Components in an Undirected Graph

DFS, Union find is more preferred for this problem

```python
class Solution:
    def countComponents(self, n: int, edges: List[List[int]]) -> int:
        adj = [[] for _ in range(n)]
        visit = [False] * n
        for u, v in edges:
            adj[u].append(v)
            adj[v].append(u)

        def dfs(node):
            for nei in adj[node]:
                if not visit[nei]:
                    visit[nei] = True
                    dfs(nei)
        
        res = 0
        for node in range(n):
            if not visit[node]:
                visit[node] = True
                dfs(node)
                res += 1
        return res
```

