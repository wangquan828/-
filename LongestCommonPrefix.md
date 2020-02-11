## 题目

编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

示例 1:

> 输入: ["flower","flow","flight"]
> 输出: "fl"

示例 2:

> 输入: ["dog","racecar","car"]
> 输出: ""
> 解释: 输入不存在公共前缀。

说明:

所有输入只包含小写字母 a-z 。

## 思路

通过双指针遍历字符串来寻找最长前缀，把第一个字符串看成最长公共前缀，然后遍历其他所有字符串来寻找最长公共前缀。

## 代码

```c++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size()==0)return string();
        else if(strs.size()==1)return strs[0];
        string result="";
        for(int i=0;i<strs[0].size();i++)
        {
            for(int j=1;j<strs.size();++j)
             if(strs[0][i]!=strs[j][i])
              return result;
            result+=strs[0][i];

        }
        return result;
    }
};
```

