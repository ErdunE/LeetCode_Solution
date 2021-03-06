## 200. Number of Islands 

#### 中文题目链接 [200. 岛屿数量](https://leetcode-cn.com/problems/number-of-islands/)

#### 英文题目链接 [200. Number of Islands](https://leetcode.com/problems/number-of-islands/)

Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return *the number of islands*.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

**Example 1:**

```
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

**Example 2:**

```
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
```

 

**Constraints:**

- `m == grid.length`
- `n == grid[i].length`
- `1 <= m, n <= 300`
- `grid[i][j]` is `'0'` or `'1'`.

---

## 解题思路

---

### 使用方法：深度优先搜索

---

###题目关键信息

二维网格 `m × n` 

`1`为陆地，`0`为海洋

竖直或者水平相邻的值如果有一个或一个以上的值为`1`即有相连的陆地

求出独立的小岛的数量

---

### 解题步骤

为了求出岛屿的数量，我们扫描整个 `m × n`

如果一个位置为`1`，则以该点为起始节点，进行深度优先搜索`DFS`

在深度优先搜索`DFS`的过程中，将每个搜索到的`1`都重新标记为`0`(这样不会重复记录，搞错搞乱)

最终我进行的深度优先搜索`DFS`的次数，就是岛屿的数量

----

### 图解

![image-20210606144058227](https://tva1.sinaimg.cn/large/008i3skNgy1gr956bjvdaj30ez05zweh.jpg)

![image-20210606144114089](https://tva1.sinaimg.cn/large/008i3skNgy1gr956hdqdlj30f0074q35.jpg)

![image-20210606144128895](https://tva1.sinaimg.cn/large/008i3skNgy1gr956mx45qj30f1071mxe.jpg)

![image-20210606144150666](https://tva1.sinaimg.cn/large/008i3skNgy1gr956r6fbbj30f007874j.jpg)

![image-20210606144200272](https://tva1.sinaimg.cn/large/008i3skNgy1gr956uwqnej30ey076t8z.jpg)

![image-20210606144211721](https://tva1.sinaimg.cn/large/008i3skNgy1gr9570izihj30ez07amxg.jpg)

![image-20210606144240717](https://tva1.sinaimg.cn/large/008i3skNgy1gr95757mvuj30ex074mxg.jpg)

![image-20210606144249487](https://tva1.sinaimg.cn/large/008i3skNgy1gr95781erpj30f306owej.jpg)

---

### 代码实现

#### 深度优先搜索`DFS`

```java
void dfs(char[][] grid, int row, int col){
  int nRow = grid.length; // 行的长度
  int nCol = gird[0].length; // 列的长度
  
  // 边界判定
  if(row < 0 || col < 0 || row >= nRow || col >= nCol || grid[row][col] == '0'){
    return;
  }
  
  grid[row][col] = '0'; // 重新标记为0
  dfs(grid, row-1, col); // 左侧
  dfs(grid, row+1, col); // 右侧
  dfs(grid, row, col-1); // 上方
  dfs(grid, row, col+1); // 下方
}
```

#### 主要代码

```java
public int numIslands(char[][],grid){
  // 特判
  if(grid == null || gird.length == 0){
    return 0;
  }
  
  int nRow = grid.length; // 行的长度
  int nCol = gird[0].length; // 列的长度
  int result = 0;
  for(int row = 0 ; row < nRow ; row++){
    for(int col = 0; col < nCol ; col++){
      // 如果一个位置为1，则以该点为起始节点，进行深度优先搜索DFS
      if(grid[row][col] == '1'){
        result++; // 每进行一次DFS result++
        dfs(grid,row,col);
      }
    }
  }
  return result;
}
```

#### 最终代码

```java
class Solution {
    void dfs(char[][] grid, int row, int col){
      int nRow = grid.length; // 行的长度
      int nCol = grid[0].length; // 列的长度

      // 边界判定
      if(row < 0 || col < 0 || row >= nRow || col >= nCol || grid[row][col] == '0'){
        return;
      }

      grid[row][col] = '0'; // 重新标记为0
      dfs(grid, row-1, col); // 左侧
      dfs(grid, row+1, col); // 右侧
      dfs(grid, row, col-1); // 上方
      dfs(grid, row, col+1); // 下方
    }
    public int numIslands(char[][] grid) {
        // 特判
      if(grid == null || grid.length == 0){
        return 0;
      }

      int nRow = grid.length; // 行的长度
      int nCol = grid[0].length; // 列的长度
      int result = 0;
      for(int row = 0 ; row < nRow ; row++){
        for(int col = 0; col < nCol ; col++){
          // 如果一个位置为1，则以该点为起始节点，进行深度优先搜索DFS
          if(grid[row][col] == '1'){
            result++; // 每进行一次DFS result++
            dfs(grid,row,col);
          }
        }
      }
      return result;
    }
}
```

