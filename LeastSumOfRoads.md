## 题目

给定一个包含非负整数的 m x n 网格，请找出一条从左上角到右下角的路径，使得路径上的数字总和为最小。

说明：每次只能向下或者向右移动一步。

示例:

输入:
[
  [1,3,1],
  [1,5,1],
  [4,2,1]
]
输出: 7
解释: 因为路径 1→3→1→1→1 的总和最小。

## 思路

先考虑第一行第一列的边界情况，用动态规划，用二维数组记录路径和，每次只能取左和上的最小值。

## 代码

```c++
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int n = grid.size();
        if(n==0)
            return 0;
        int m = grid[0].size();
        if(m==0)
            return 0;
        for(int i=1;i<m;i++)
        {
            grid[0][i] += grid[0][i-1];

        }
        for(int i=1;i<n;i++)
        {
            grid[i][0] += grid[i-1][0];
        }
        for(int i=1;i<n;i++)
        {
            for(int j=1;j<m;j++)
            {
                grid[i][j]+=min(grid[i-1][j],grid[i][j-1]);
            }
        }
        return grid[n-1][m-1];
    }

};
```

