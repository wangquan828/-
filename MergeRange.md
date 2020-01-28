## 题目

给出一个区间的集合，请合并所有重叠的区间。

示例 1:

> 输入: [[1,3],[2,6],[8,10],[15,18]]
> 输出: [[1,6],[8,10],[15,18]]
> 解释: 区间 [1,3] 和 [2,6] 重叠, 将它们合并为 [1,6].

示例 2:

> 输入: [[1,4],[4,5]]
> 输出: [[1,5]]
> 解释: 区间 [1,4] 和 [4,5] 可被视为重叠区间。

## 思路

把所给区间看成二维数组，然后根据区间左端点进行排序，然后遍历比较如果下一个区间的左端点大于上一个区间的右端点，则说明两个区间可合并，否则不能合并直接输出。

## 代码

```c++
class Solution {
public:
    
    vector<vector<int>> merge(vector<vector<int>>& intervals) {
        vector<vector<int>> res;  //声明res
        if(intervals.empty()) return res;  

        sort(intervals.begin(),intervals.end());//左端点排序
        int index = 0;  
        res.push_back(intervals[0]);//先将第一个区间放到res里    
        for (int i = 1; i < intervals.size(); i++) //遍历res的其他区间
        {
            if(res[index][1] >= intervals[i][0]) //左端点大于上一区间右端点则可合并
            {                                   
                if(res[index][1] < intervals[i][1])
                {                                  
                    res[index][1] = intervals[i][1]; 
                }
            }
            else//不能合并直接放入res
            {
                index++;  
                res.push_back(intervals[i]);
            }
        }
        return res;
    }
};

```

