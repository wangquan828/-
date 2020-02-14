## 题目

给定一个没有重复数字的序列，返回其所有可能的全排列。

示例:

> 输入: [1,2,3]
> 输出:
> [
>   [1,2,3],
>   [1,3,2],
>   [2,1,3],
>   [2,3,1],
>   [3,1,2],
>   [3,2,1]
> ]

## 思路

在枚举第一位的时候有三种情况，枚举第二位的时候只有两种情况，那第三位就只有一种情况了。所以在枚举一种结果后要回头恢复原来的状态枚举第二种情况。可以用栈保存所需的状态。当数选够的时候就停止递归。

```c++
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) 
    {
        vector<vector<int>> res;
        backtrack(nums,res,0);
        return res;
    }
    void swap(int &a,int &b)
    {
        int temp;
        temp=a;
        a=b;
        b=temp;
    }
    
    void backtrack(vector<int> &nums,vector<vector<int>> &res,int i){
        if(i==nums.size())
         res.push_back(nums);
        for(int j=i;j<nums.size();j++){
            swap(nums[i],nums[j]);
            backtrack(nums,res,i+1);
            swap(nums[i],nums[j]);
        }
    }
};
```

