# Leetcode 496 下一个更大元素1

### 题目描述
给定两个 没有重复元素 的数组 nums1 和 nums2 ，其中nums1 是 nums2 的子集。找到 nums1 中每个元素在 nums2 中的下一个比其大的值。
nums1 中数字 x 的下一个更大元素是指 x 在 nums2 中对应位置的右边的第一个比 x 大的元素。如果不存在，对应位置输出 -1 。

示例 1:
```
输入: nums1 = [4,1,2], nums2 = [1,3,4,2].
输出: [-1,3,-1]
解释:
    对于num1中的数字4，你无法在第二个数组中找到下一个更大的数字，因此输出 -1。
    对于num1中的数字1，第二个数组中数字1右边的下一个较大数字是 3。
    对于num1中的数字2，第二个数组中没有下一个更大的数字，因此输出 -1。
```
示例 2:
```
输入: nums1 = [2,4], nums2 = [1,2,3,4].
输出: [3,-1]
解释:
    对于 num1 中的数字 2 ，第二个数组中的下一个较大数字是 3 。
    对于 num1 中的数字 4 ，第二个数组中没有下一个更大的数字，因此输出 -1 。
```

提示:
```
nums1和nums2中所有元素是唯一的。
nums1和nums2 的数组大小都不超过1000。
```

### 解题思路
单调栈+哈希的简单题吗，首先用```map```记录```nums1```中每个元素出现的位置。
之后，对```nums2```维护一个单调递减栈，从左至右遍历一次```nums2```，出现一个比栈顶小的元素，则```push```到栈当中，
如果出现比栈顶大的元素，栈顶的右边第一个比它大的元素出现了，则栈顶元素出栈，看看栈定元素是否对应着```nums1```某次询问，有就
把当前运算作为```nums1```对应的询问位置的结果。之后继续比较当前元素与栈顶，重复该过程直到比栈顶小或者栈为空则当前元素
入栈，继续```nums2```的遍历过程。遍历完后，```nums1```所有没求的结果的位置都是右边没有比他大的元素的，结果都是-1(所以可以在一开始把结果全部设为-1)
### 代码

```cpp
class Solution {
public:
    vector<int> nextGreaterElement(vector<int>& nums1, vector<int>& nums2) {
        vector<int> result(nums1.size(), -1);                       //开始结果全部为-1
        stack<int> des_stack;
        map<int, int> pos_map;
        for(int i=0;i<nums1.size();i++)
            pos_map[nums1[i]] = i;
        for(auto x:nums2){
            if(des_stack.empty() || x<des_stack.top()){
                des_stack.push(x);
            }
            else{
                while(!des_stack.empty()&&x>=des_stack.top()){
                    int mid = des_stack.top();
                    des_stack.pop();
                    if(pos_map.count(mid)){
                        result[pos_map[mid]] = x;
                    }
                }
                des_stack.push(x);
            }
        }
        return result;
    }
};
```

### 其他人的思路
+ 两遍遍历暴力法：不太优雅