## 题目

给定由一些正数（代表长度）组成的数组 A，返回由其中三个长度组成的、面积不为零的三角形的最大周长。

如果不能形成任何面积不为零的三角形，返回 0。

 

示例 1：

输入：[2,1,2]
输出：5

示例 2：

输入：[1,2,1]
输出：0

示例 3：

输入：[3,2,3,4]
输出：10

## 思路

按降序排列，如果i小于后两数和，返回三数之和

## 代码

```c++
class Solution {
public:
    int largestPerimeter(vector<int>& A) {
      int n=A.size();
      if(n<3)
        return 0;
      sort(A.begin(),A.end());
      reverse(A.begin(),A.end());
      for(auto i=A.begin();i!=A.end()-2;i++){
          if(*i<*(i+1)+*(i+2))
          return *i+*(i+1)+*(i+2);
      }
      return 0;
    }
};
```

