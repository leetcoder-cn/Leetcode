**思路**

方法一 :DFS,遍历所有人,对于每个人寻找他的好友,然后再找他好友的好友,这样深度优先遍历下去，通过 visited 数组记录是否已经遍历完这个人,遍历到相同朋友圈, visited[i] 则标识为已经遍历过,不再次纳入朋友圈个数统计中

方法二: 并查集,将有关系的人放在一个集合中

**解法**

解法一

```python
class Solution:
    def findCircleNum(self, M: List[List[int]]) -> int:
        len_m = len(M)
        visited = [0 for i in range(len_m)]
        friend_count = 0
        
        def dfs(M,i,visited,len_m):
            visited[i] = 1
            for j in range(len_m):
                if M[i][j] == 1 and visited[j] == 0:
                    dfs(M,j,visited,len_m)
            
        for i in range(len_m):
            if visited[i] == 0:
                friend_count += 1
                dfs(M,i,visited,len_m)
        return friend_count
```

解法二

```python
class Solution:
    def findCircleNum(self, M: List[List[int]]) -> int:
        len_m = len(M)
   
        self.parent = [i for i in range(len_m)] # init 
        
        def find_set(i):
            if i == self.parent[i]:
                return i
            return find_set(self.parent[i])
        
        def union(i,j):
            find_i, find_j = find_set(i),find_set(j)
            self.parent[find_j] = find_i
        
        for i in range(len_m):
            for j in range(len_m):
                if M[i][j]:
                    union(i,j)
        return len([i for i in range(len_m) if find_set(i) == i])
```