## 题目

给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

示例 1:

> 输入: [1,2,3]
> 输出: [1,2,4]
> 解释: 输入数组表示数字 123。

示例 2:

> 输入: [4,3,2,1]
> 输出: [4,3,2,2]
> 解释: 输入数组表示数字 4321。

## 思路

最简单的情况直接在最后一位加一，如果最后一位是9，最后一位变成零，前一位加一以此类推，如果都是9，最后补位0，第一位变1、

## 代码

```c++
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
       int n=(int)digits.size();
       for(int i=n-1;i>=0;i--){
           if(digits[i]==9){
               digits[i]=0;
           }
           else{
               digits[i]++;
               return digits;
           }
       }
       digits.push_back(0);
       digits[0]=1;
       return digits;
    }
};
```

