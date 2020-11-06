# Leetcode 303 区域和检索(数组不可变)

### 题目
给定一个整数数组  nums，求出数组从索引 i 到 j  (i ≤ j) 范围内元素的总和，包含 i,  j 两点。

示例：
```
给定 nums = [-2, 0, 3, -5, 2, -1]，求和函数为 sumRange()
sumRange(0, 2) -> 1
sumRange(2, 5) -> -1
sumRange(0, 5) -> -3
```
说明:
```
你可以假设数组不可变。
会多次调用 sumRange 方法。
```
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/range-sum-query-immutable
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。


### 解题思路
部分和(前缀和)的题目，先将数组改成每个位置表示前面所有数的和的形式，即i代表1到i的数的和：
```
[1, 2, 2, 3, 3]->[1, 3, 5, 8, 11]
```
那么一个区间的和可由区间结尾位置减去区间开始前一位得出：
```
第2个位置到第3个位置的和(下标从0开始)，可以由8-3得到
```
这样第一次求和时间复杂度为```O(n)```,之后每次询问的时间复杂度为```O(1)```

### 代码

```cpp
class NumArray {
public:
    vector<int> sums;
    NumArray(vector<int>& nums) {
        int su = 0;
        for(auto x:nums){
            su += x;
            sums.push_back(su);
        }
    }
    
    int sumRange(int i, int j) {
        if(i==0)
            return sums[j];
        else
            return sums[j]-sums[i-1];
    }
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray* obj = new NumArray(nums);
 * int param_1 = obj->sumRange(i,j);
 */
```