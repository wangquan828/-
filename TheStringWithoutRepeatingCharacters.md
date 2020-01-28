## 问题

 给定一个字符串，请你找出其中不含有重复字符的 **最长子串** 的长度。 

## 示例

示例 1:

输入: "abcabcbb"
输出: 3 
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。

示例 2:

输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。

示例 3:

输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。

​     请注意，你的答案必须是 子串 的长度，"pwke" 是一个子序列，不是子串。

## 思路

通过两次遍历，用i的值调k的值，如果遇到相通字符，直接跳过，如果没有遇到计算j-i的值与max比较，直到遍历到最后。

### 代码

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
         int size,i=0,j,k,max=0;
        size=s.size();
        for(j=0;j<size;j++){
            for(k=i;k<j;k++)
                if(s[k]==s[j]){
                    i=k+1;
                    break;
                }
           if(j-i+1 > max)
               max = j-i+1;
        }
    return max;
    }
};
```

## 思路plus--滑动窗口

滑动窗口是数组/字符串问题中常用的抽象概念。 窗口通常是在数组/字符串中由开始和结束索引定义的一系列元素的集合，即 [i,j)[i, j)[i,j)（左闭，右开）。而滑动窗口是可以将两个边界向某一方向“滑动”的窗口。例如，我们将 [i,j)[i, j)[i,j) 向右滑动 111 个元素，则它将变为 [i+1,j+1)[i+1, j+1)[i+1,j+1)（左闭，右开）。

我们需要记录的其实是之前出现过的字符。而实际上，我们先前模拟的其实是一个sliding window（滑动窗口），窗口内是没有出现过的字符，我们需要尽可能的扩展窗口的大小。窗口在向右滑动的过程中，我们只要知道每个字符最后出现的位置，以此建立映射。 最后这个滑动窗口的大小size就是我们的result。

为了求出这个result，我们需要一个left变量来指向滑动窗口的左边界，如果遍历到的字符没有出现过，我们扩大右边界，如果出现过，分两种情况讨论。一是当前字符已经出现在滑动窗口内，我们需要把已在滑动窗口内的字符去掉，再加进来。去掉的方法是通过移动left指针，因为之前的Hashmap已经保存了该重复字符最后出现的位置，所以我们只要移动left指针的位置即可。第二种情况是该字符已经存储在Hashmap内但没有在滑动窗口内，这时我们可以直接加到滑动窗口内。最后，我们只维护一个res结果，每次用出现的窗口大小和res 本身比较，就可以得到最终结果。

我们这里建的Hashmap，是建立每个字符和其最后出现位置之间的映射。变量res是用来记录最长无重复字串的长度，left是指向该无重复字串左边起始位置的前一个。

Hashmap我们可以用一个256 或128位大小的整型数组来代替。因为ASCii表只有256个字符，然而键盘只能表示128个，所以用128也行。将所有位置初始为-1，然后遍历字符串。

### 代码

```c++
class Solution {
public:
    int lengthOfLongestSubstring(string s) {
        vector<int>m(256,-1);
        int left=-1;
        int res=0;
        int len=s.size();
        for(int i=0;i<len;i++)
        {
            left=max(left,m[s[i]]);
            m[s[i]]=i;
            res=max(res,i-left);
        }
        
        return res;
    }
};


```
