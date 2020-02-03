## 题目

给定一个非负整数数组，你最初位于数组的第一个位置。

数组中的每个元素代表你在该位置可以跳跃的最大长度。

判断你是否能够到达最后一个位置。

示例 1:

> 输入: [2,3,1,1,4]
> 输出: true
> 解释: 我们可以先跳 1 步，从位置 0 到达 位置 1, 然后再从位置 1 跳 3 步到达最后一个位置。

示例 2:

> 输入: [3,2,1,0,4]
> 输出: false
> 解释: 无论怎样，你总会到达索引为 3 的位置。但该位置的最大跳跃长度是 0 ， 所以你永远不可能到达最后一个位置。

## 思路

如果第一个数是3那么后面三个数字都能够作为下一次的跳点，如果该点位置数加上该点数值大于数组长度，则说明能跳到最终，但如果i＞k说明无法跳到

## 代码

```c++
class Solution {
public:
    bool canJump(vector<int>& nums) {
   int k=0;
   for(int i=0;i<nums.size();i++){
       if(i>k)return false;
       k=max(k,i+nums[i]);
   }
   return true;
    }   
};
```

## 思路2

初始化zerocount为0，i为n-2，数组往前遍历，如果nums[i]=0就让zerocount++，最后如果zerocount不为0，说明前面跳跃时必有一步无法跳跃。

## 代码

```c
bool canJump(int* nums, int numsSize){
 int n = numsSize;
        if(n==0) return false;
        if(n==1) return true;

        int zeroCount = 0;
        for(int i=n-2; i>=0; i--){
            if(nums[i]==0) zeroCount++;
            else{
                if(nums[i]>zeroCount) zeroCount=0;
                else zeroCount++;
            }
        }
        if(zeroCount>0) return false;
        else return true;
}
```

