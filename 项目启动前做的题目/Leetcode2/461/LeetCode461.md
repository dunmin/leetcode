# leetCode 657

## 题目描述：

两个整数之间的汉明距离指的是这两个数字对应二进制位不同的位置的数目。

给出两个整数 x 和 y，计算它们之间的汉明距离。

注意：
0 ≤ x, y < 231.

示例:
```
输入: x = 1, y = 4

输出: 2

解释:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

上面的箭头指出了对应二进制位不同的位置。
```

## solution@dunmin:
C++:
```
class Solution {
public:
    int hammingDistance(int x, int y) {
        vector<int> xlist;
        vector<int> ylist;
        while(x||y){
            if(x){
                xlist.push_back(x%2);
                x/=2;
            }
            else {
                xlist.push_back(0);
            }
            if(y){
                ylist.push_back(y%2);
                y/=2;
            }
            else {
                ylist.push_back(0);
            }
        }
        int coun = 0;
        for(int i=0;i<xlist.size();i++){
            if(xlist[i]!=ylist[i])
                coun++;
        }
        return coun;
    }
};
```
## 说明@dunmin:
```
简单题:
十进制转二进制
```