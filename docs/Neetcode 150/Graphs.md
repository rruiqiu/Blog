## Graph

### DFS

### BFS



## Number of Islands

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

## Clone Graph

```python
class Solution:
    def cloneGraph(self, node: Optional['Node']) -> Optional['Node']:
        oldToNew = {}

        def dfs(node):
            if node in oldToNew:
                return oldToNew[node]

            copy = Node(node.val)
            oldToNew[node] = copy
            for nei in node.neighbors:
                copy.neighbors.append(dfs(nei))
            return copy

        return dfs(node) if node else None
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

