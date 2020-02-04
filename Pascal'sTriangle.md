## 题目

给定一个非负整数 *numRows，*生成杨辉三角的前 *numRows* 行。

![img](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

在杨辉三角中，每个数是它左上方和右上方的数的和。

示例:

> 输入: 5
> 输出:
> [
>      [1],
>     [1,1],
>    [1,2,1],
>   [1,3,3,1],
>  [1,4,6,4,1]
> ]

## 思路

杨辉三角的下一行左右两端都为1，中间的数为上一行左上和右上数之和。

## 代码

```c++
class Solution {
public:
    vector<vector<int>> generate(int numRows) {
        vector<vector<int>>ans(numRows);
            if(numRows==0)return ans;
            for(int i=0;i<numRows;++i){
                for(int j=0;j<=i;++j){
                    if(j==0||j==i)//边界赋值为1
                    ans[i].push_back(1);
                    else
                    ans[i].push_back(ans[i-1][j-1]+ans[i-1][j]);//等于左上右上和
                }
            }
            return ans;
        
    }
};
```

