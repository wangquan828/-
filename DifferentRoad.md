## 题目

一个机器人位于一个 m x n 网格的左上角 （起始点在下图中标记为“Start” ）。

机器人每次只能向下或者向右移动一步。机器人试图达到网格的右下角（在下图中标记为“Finish”）。

问总共有多少条不同的路径？

 ![img](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/10/22/robot_maze.png) 

说明：m 和 n 的值均不超过 100。

示例 1:

> 输入: m = 3, n = 2
> 输出: 3
> 解释:
> 从左上角开始，总共有 3 条路径可以到达右下角。

1. 向右 -> 向右 -> 向下
2. 向右 -> 向下 -> 向右
3. 向下 -> 向右 -> 向右

示例 2:

> 输入: m = 7, n = 3
> 输出: 28

## 思路

从起点出发，下一步只能向右或向下，一直到最后结束，所以所有路径总和为两个第二个点到终点的路径数总和。同时用一个二维数组储存已经计算过的路径数。

## 代码

```c++
static int a[101][101]={0};//记录已经计算过的路径，大大提高效率
class Solution{
	public:
		int uniquePaths(int m, int n){
		    if(m<=0||n<=0)
             return 0;
            else if(m==1||n==1)
             return 1;
            else if(m==2&&n==2)
             return 2;
            if(a[m][n]>0)
             return a[m][n];
            a[m-1][n]=uniquePaths(m-1,n);
            a[m][n-1]=uniquePaths(m,n-1);
            a[m][n]=a[m-1][n]+a[m][n-1];
            return a[m][n];
    }
};
```

