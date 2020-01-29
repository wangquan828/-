## 题目

给定一个包括 n 个整数的数组 nums 和 一个目标值 target。找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。

> 例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.
>
> 与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).
>

## 思路

先对数组排序，然后用i对数组进行遍历，双指针从i+1到len-1开始，计算sum与target的距离，如果更近就得到新结果ans，如果sum＞target则右指针向左移，反之左指针向右移。

## 代码

```c++
class Solution {
public:
    int threeSumClosest(vector<int>& nums, int target) {
        int len=nums.size();
        if(len<3)
        return 0;
        sort(nums.begin(),nums.end());
        int i,low,high;
        int delta=0x7fffffff,sum,ans;
        for(int i=0;i<len-2;i++){
            low=i+1;
            high=len-1;
            while(low<high){
                sum=nums[i]+nums[low]+nums[high];
                if(sum==target){
                    return sum;
                }
                else if(sum<target){
                if(target-sum<delta){
                    delta=target-sum;
                    ans=sum;
                }
                low++;
                }
                else{
                    if(sum-target<delta){
                        delta=sum-target;
                        ans=sum;
                    }
                    high--;
                }
                                }
            }
            return ans;
        }
    
};
```

