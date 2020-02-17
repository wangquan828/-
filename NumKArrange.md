## 题目

给出集合 [1,2,3,…,n]，其所有元素共有 n! 种排列。

按大小顺序列出所有排列情况，并一一标记，当 n = 3 时, 所有排列如下：

    "123"
    "132"
    "213"
    "231"
    "312"
    "321"

给定 n 和 k，返回第 k 个排列。

说明：

    给定 n 的范围是 [1, 9]。
    给定 k 的范围是[1,  n!]。

示例 1:

> 输入: n = 3, k = 3
> 输出: "213"
>
> 示例 2:
>

> 输入: n = 4, k = 9
> 输出: "2314"

## 思路

如果(i-1)*(n - 1)! < k <= i * (n - 1)!，那个第一个数字就应该为nums[i - 1]，将这个数剔除nums中:nums.erase(nums.begin() + (i - 1));，k = k - (i - 1) * ( n - 1)!

## 代码

```c++
class Solution {
public:
    string getPermutation(int n, int k) {
        string res="";
        vector<int>nums;
        for(int i=1;i<=n;i++)
        {
            nums.push_back(i);
        }
        for(int j=0;j<n;j++)
        {
            int len=nums.size();
            for(int i=1;i<=len;i++)
            {
                int n=getMul(len-1);
                if((i-1)*n<k&&k<=i*n){
                    char c='0'+nums[i-1];
                    res+=c;
                    nums.erase(nums.begin()+(i-1));
                    k-=(i-1)*n;
                    break;

                }
            }
        }
        return res;
    }
    //计算阶乘的函数
  int getMul(int n){
      int res=1;
      for(int i=2;i<=n;i++)
          res*=i;
      return res;
}      
};
```

