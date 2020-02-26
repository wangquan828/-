## 题目

给定一个未排序的整数数组，找出其中没有出现的最小的正整数。

示例 1:

> 输入: [1,2,0]
> 输出: 3

示例 2:

> 输入: [3,4,-1,1]
> 输出: 2

示例 3:

> 输入: [7,8,9,11,12]
> 输出: 1
>

## 思路

利用桶排序的方法，假如一个数字值为i+1，那它所处的位置就应是索引i的地方，如果是负数或者超出数组长度的数就先不管，按照这种方法排好序后，找到不处于该规律的数将其索引加一即为所求。

## 代码

```c++
class Solution {
public:
    int firstMissingPositive(vector<int>& nums) {
        for(int i=0;i<nums.size();i++){
            while(nums[i] !=i+1){
                if(nums[i]<=0||nums[i]>nums.size()||nums[i]==nums[nums[i]-1])
                   break;
                int idex=nums[i]-1;
                nums[i]=nums[idex];
                nums[idex]=idex+1;

            }
        }
        for(int i=0;i<nums.size();i++){
            if(nums[i]!=(i+1)){
                return (i+1);
            }
        }
        return (nums.size()+1);

    }
};
```

