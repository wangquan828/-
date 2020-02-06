## 题目

给定一个整数数组，判断数组中是否有两个不同的索引 i 和 j，使得 nums [i] 和 nums [j] 的差的绝对值最大为 t，并且 i 和 j 之间的差的绝对值最大为 ķ。

示例 1:

> 输入: nums = [1,2,3,1], k = 3, t = 0
> 输出: true

示例 2:

> 输入: nums = [1,0,1,1], k = 1, t = 2
> 输出: true

示例 3:

> 输入: nums = [1,5,9,1,5,9], k = 2, t = 3
> 输出: false

## 思路

找到大于或等于nums[i]-t的数且不比nums[i]+t大，则说明符合条件，i-j的最大值为K说明插入的窗口record的最大值为K

## 代码

```c++
class Solution {
public:
    bool containsNearbyAlmostDuplicate(vector<int>& nums, int k, int t) {
        // 活动窗口
        set<int> record;
        for(int i=0; i<nums.size(); i++){
            // 找到大于或等于nums[i]-t的数中最小的数
            auto s = record.lower_bound((double)nums[i]-t); // 防溢出
            // 存在大于或等于nums[i]-t的数 && 这个数不比nums[i]+t大
            if(s != record.end() && *s <= (double)nums[i]+t)
                return true;
            // i-j的最大值是k, 也就是record的最大长度可以是k+1
            // 将当前元素插入record
            // insert放在这里而是不在上个if之前, 是为了防止lower_bound取到的元素和nums[i]一样
            record.insert(nums[i]);
            // record.size保持<=k+1
            // 当record达到k+1时, 马上要删去一个, 为下一个元素腾出空间
            if(record.size() == k+1)
                record.erase(nums[i-k]);
        }
        return false;
    }
};
```

