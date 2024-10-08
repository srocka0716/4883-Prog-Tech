# 200 - Number of Islands

https://leetcode.com/problems/number-of-islands/description/

Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.

 

Example 1:

Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
Example 2:

Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
 

Constraints:

m == grid.length
n == grid[i].length
1 <= m, n <= 300
grid[i][j] is '0' or '1'.



```
 //straight ripped because its utility
void dfs(vector<vector<char>>& grid, int i, int j) {
    //This breaks out of the looking for water loop
    if (i < 0 || i >= grid.size() || j < 0 || j >= grid[0].size() || grid[i][j] == '0') {
        return;
    }

    //Makes the cell we are on become visited
    grid[i][j] = '0';

    // Call DFS in all four directions
    dfs(grid, i + 1, j); // down
    dfs(grid, i - 1, j); // up
    dfs(grid, i, j + 1); // right
    dfs(grid, i, j - 1); // left
}

class Solution {
public:
    int numIslands(vector<vector<char>>& grid) {
        //island counter
        int islands = 0;

        //Check if the grid is empty
        if (grid.empty()) {
            return 0;
        }
        for (int i = 0; i < grid.size(); ++i)
        {
            for (int j = 0; j < grid[0].size(); ++j)
            {
                //if its land
                if (grid[i][j] == '1')
                {   
                    //check and see if its an island
                    dfs(grid, i, j);
                    islands++;
                }
                //continue in the loop if its water
            }
        }
            return islands;
    }
};
```

