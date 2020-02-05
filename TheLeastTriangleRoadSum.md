## 题目

给定一个三角形，找出自顶向下的最小路径和。每一步只能移动到下一行中相邻的结点上。

例如，给定三角形：

> [
>      [2],
>     [3,4],
>    [6,5,7],
>   [4,1,8,3]
> ]

自顶向下的最小路径和为 11（即，2 + 3 + 5 + 1 = 11）。

## 思路

自底而上考虑，由于要求的是相邻元素，所以只能考虑正上和左上方的元素，得出递推公式。

## 代码

```c++
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
       int rowSize=triangle.size();
       vector<vector<int>> dp(triangle);
       for(int i=rowSize-2;i>=0;i--){
           for(int j=0; j<triangle[i].size();j++){
               dp[i][j]=min(dp[i+1][j],dp[i+1][j+1]) +  triangle[i][j];
           }
       }
      return dp[0][0];}
    
};

```

