# leetcode 64 最小路径和

## 题目描述
一个矩阵，求从左上角移动到右下角(每一步只能向右或下移动)的最小累加和

## 题目思路
+ 简单dp，每个位置的最小和来自于上面或者左边最小和加上当前位置的数

## 代码
```
class Solution {
public:
    int minPathSum(vector<vector<int>>& grid) {
        int m = grid.size();
        int n = grid[0].size();
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                if(i>0&&j>0) grid[i][j] += min(grid[i-1][j], grid[i][j-1]);
                else if(i>0) grid[i][j] += grid[i-1][j];
                else if(j>0) grid[i][j] += grid[i][j-1];
            }
        }
        return grid[m-1][n-1];
    }
};
```