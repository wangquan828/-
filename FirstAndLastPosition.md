## 题目

给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。

你的算法时间复杂度必须是 O(log n) 级别。

如果数组中不存在目标值，返回 [-1, -1]。

示例 1:

> 输入: nums = [5,7,7,8,8,10], target = 8
> 输出: [3,4]

示例 2:

> 输入: nums = [5,7,7,8,8,10], target = 6
> 输出: [-1,-1]

## 思路

用二分法，分别寻找目标的起始位置和结束位置。起始位置如果mid大于目标值说明区间应向左去，否则向右。找结束为止同理。但找结束为止时由于计算中位数是向下取整的所以在找右中位数时应+1。



```c++
#include <iostream>
#include <vector>

using namespace std;


class Solution {
private:
    int findFitstPosition(vector<int> &nums, int target) {
        int size = nums.size();
        int left = 0;
        int right = size - 1;
        while (left < right) {
            int mid = (left + right)/2;
            if (nums[mid] < target) {
                left = mid + 1;
            } else {
                right = mid;
            }
        }
        if (nums[left] != target) {
            return -1;
        }
        return left;
    }

    int findLastPosition(vector<int> &nums, int target) {
        int size = nums.size();
        int left = 0;
        int right = size - 1;
        while (left < right) {
            int mid = (left + right + 1)/2;
            if (nums[mid] > target) {
                right = mid - 1;
            } else {
                left = mid;
    
            }
        }
        if (nums[left] != target) {
            return -1;
        }
        return left;
    }


public:
    vector<int> searchRange(vector<int> &nums, int target) {
        int size = nums.size();
        if (size == 0) {
            return {-1, -1};
        }
        int firstPosition = findFitstPosition(nums, target);

        if (firstPosition == -1) {
            return {-1, -1};
        }
        int lastPosition = findLastPosition(nums, target);
        return {firstPosition, lastPosition};
    }

};
```


