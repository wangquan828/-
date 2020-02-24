## 题目

给定一个偶数长度的数组，其中不同的数字代表着不同种类的糖果，每一个数字代表一个糖果。你需要把这些糖果平均分给一个弟弟和一个妹妹。返回妹妹可以获得的最大糖果的种类数。

示例 1:

> 输入: candies = [1,1,2,2,3,3]
> 输出: 3
> 解析: 一共有三种种类的糖果，每一种都有两个。
>      最优分配方案：妹妹获得[1,2,3],弟弟也获得[1,2,3]。这样使妹妹获得糖果的种类数最多。

示例 2 :

> 输入: candies = [1,1,2,3]
> 输出: 2
> 解析: 妹妹获得糖果[2,3],弟弟获得糖果[1,1]，妹妹有两种不同的糖果，弟弟只有一种。这样使得妹妹可以获得的糖果种类数最多。

## 思路

先对数组进行排序，然后每找出新元素就计数，用count计数，如果糖果种类数大于总数一半，，那姐姐可以拿到总数的一半，如果糖果种类数小于总数的一半那姐姐可以拿到每种糖果。

## 代码

```java
public class Solution {
    public int distributeCandies(int[] candies) {
        Arrays.sort(candies);
        int count = 1;
        for (int i = 1; i < candies.length && count < candies.length / 2; i++)
            if (candies[i] > candies[i - 1])
                count++;
        return count;
    }
}
```

