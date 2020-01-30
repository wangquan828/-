## 题目

给定一个包含红色、白色和蓝色，一共 n 个元素的数组，原地对它们进行排序，使得相同颜色的元素相邻，并按照红色、白色、蓝色顺序排列。

此题中，我们使用整数 0、 1 和 2 分别表示红色、白色和蓝色。

注意:
不能使用代码库中的排序函数来解决这道题。

###  **示例:** 

> ```
> 输入: [2,0,2,1,1,0]
> 输出: [0,0,1,1,2,2]
> ```

## 思路

用left记录第一个非较小数字的位置

用right记录第一个非较大数字的位置

当i<=right终止循环

如果nums[i]为较小值与nums[left]交换，left++

如果nums[i]为较大值时，与nums[right]交换，right--

## 代码

```c++
class Solution {
public:
    void sortColors(vector<int>& nums) {
        int left=0;
        int right= nums.size()-1;
        int i=0;
        int temp=0;
        while(i<=right){
            if(nums[i]==1){
                i++;
                    }
            else if(nums[i]==0){
                if(left==i){
                    left++;
                    i++;
                }
                else{
                    temp=nums[i];
                    nums[i]=nums[left];
                    nums[left]=temp;
                    left++;
                }

            }
            else if(nums[i]==2){
                temp=nums[i];
                nums[i]=nums[right];
                nums[right]=temp;
                right--;
            }
        }
    }
};
```

