## 题目

给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

示例:

> 输入: [-2,1,-3,4,-1,2,1,-5,4],
> 输出: 6
> 解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。

## 思路

从左向右遍历，挨个数字相加，如果sum＜0就重新找字序串。

## 代码

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int result=INT_MIN;
        int n=int(nums.size());
        int sum=0;
        for(int i=0;i<n;i++)
        {
            sum+=nums[i];
            result=max(result,sum);
            if(sum<0)
            {
                sum=0;
            }
        }
        return result;
    }
};
```

