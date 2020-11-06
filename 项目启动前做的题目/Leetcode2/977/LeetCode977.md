# leetCode 977

## 题目描述：

给定一个按非递减顺序排序的整数数组 A，返回每个数字的平方组成的新数组，要求也按非递减顺序排序。
 

示例 1：
```
输入：[-4,-1,0,3,10]
输出：[0,1,9,16,100]
```

示例 2：
```
输入：[-7,-3,2,3,11]
输出：[4,9,9,49,121]
```

提示：

+ 1 <= A.length <= 10000
+ -10000 <= A[i] <= 10000
+ A 已按非递减顺序排序


## solution@dunmin:
C++:O(nlogn)
```
class Solution {
public:
    vector<int> sortedSquares(vector<int>& A) {
        for(int i=0;i<A.size();i++){
            A[i] = A[i] * A[i];
        }
        
        sort(A.begin(),A.end());
        return A;
    }
};
```

```
point:
(1)对vector快速排序：sort(A.begin(),A.end());
```

C++:O(n)(双指针法)
```
class Solution {
public:
    vector<int> sortedSquares(vector<int>& A) {
        vector<int>::iterator foreward = A.begin();
        vector<int>::iterator backward = A.end()-1;
        vector<int> B;
        while(foreward<=backward){
            int forevalue = pow((*foreward),2);
            int backvalue = pow((*backward),2);
            if(forevalue>backvalue){
                B.push_back(forevalue);
                foreward++;
            }
            else {
                B.push_back(backvalue);
                backward--;
            }
        }
        int siz = B.size();
        for(int i=0;i<siz;i++){
            A[i] = B[siz-1-i];
        }
        return A;
    }
};
```
```
point:
双指针，一个在最前面往后，一个在最后面往前，因为平方较大的不是靠前就是靠后，因此每次比较两个数就能得出当前最大的，放进新数组，移动该数的指针，比较中小的数指针不动，继续比较，以此类推
```

## 说明@dunmin:
```
简单题
```