# leetcode 1025 除数博弈

## 题目描述
简单题，求二叉树的最大深度

## 解法
### 递归
```
/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
 * };
 */
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if(root==NULL) return 0;
        else {
            return max(maxDepth(root->left), maxDepth(root->right))+1;
        }
    }
};
```

## 别人的解法
### BFS
+ 我们也可以用「广度优先搜索」的方法来解决这道题目，但需要对其进行一些修改，使其每次只遍历当前层(**不错的BFS改进**)
```
class Solution {
public:
    int maxDepth(TreeNode* root) {
        if (root == nullptr) return 0;
        queue<TreeNode*> Q;
        Q.push(root);
        int ans = 0;
        while (!Q.empty()) {
            int sz = Q.size();
            while (sz > 0) {
                TreeNode* node = Q.front();Q.pop();
                if (node->left) Q.push(node->left);
                if (node->right) Q.push(node->right);
                sz -= 1;
            }
            ans += 1;
        } 
        return ans;
    }
};
```