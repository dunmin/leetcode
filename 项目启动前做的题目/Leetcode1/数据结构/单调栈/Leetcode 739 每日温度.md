# Leetcode 739 每日温度

### 题目描述
根据每日 气温 列表，请重新生成一个列表，对应位置的输出是需要再等待多久温度才会升高超过该日的天数。如果之后都不会升高，请在该位置用 0 来代替。
例如，给定一个列表 temperatures = [73, 74, 75, 71, 69, 72, 76, 73]，你的输出应该是 [1, 1, 4, 2, 1, 1, 0, 0]。
提示：气温 列表长度的范围是 [1, 30000]。每个气温的值的均为华氏度，都是在 [30, 100] 范围内的整数。

提示:
```
nums1和nums2中所有元素是唯一的。
nums1和nums2 的数组大小都不超过1000。
```

### 解题思路
单调栈的题目

### 代码

```cpp
class Solution {
public:
    vector<int> dailyTemperatures(vector<int>& T) {
        stack<int> des_stack;
        // 先假设全部没有结果即为0，就不用处理最后栈剩余的元素了
        vector<int> result(T.size(), 0);
        for(int i=0;i<T.size();i++){
            while(!des_stack.empty()&&T[i]>T[des_stack.top()]){
                int top = des_stack.top();
                des_stack.pop();
                result[top] = i - top;
            }
            des_stack.push(i);
        }
        return result;
    }
};
```

### 其他人的思路
+ 记忆化数组+逆序遍历(没有单调栈快):因为温度范围是从```[30,100]```，因此逆序遍历时，
将当前温度出现的位置作记录在记忆化数组中，例如温度```20```， 出现在第3个位置，则```re[20] = 3```，
每到一个位置，则遍历当前温度到```100度```之间的温度，并将得到的最小下标作为结果
