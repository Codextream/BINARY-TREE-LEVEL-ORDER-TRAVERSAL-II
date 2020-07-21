# BINARY TREE LEVEL ORDER TRAVERSAL II

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

For example:
Given binary tree [3,9,20,null,null,15,7],

<pre>
    3
   / \
  9  20
    /  \
   15   7

</pre>

return its bottom-up level order traversal as:
<pre>
[
  [15,7],
  [9,20],
  [3]
]
</pre>


### Solution:

```cpp

/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class Solution {
public:
    int depth(TreeNode* root){
        if(root==NULL) return 0;
        return max(depth(root->left),depth(root->right))+1;
    }
    
    void level(vector<vector<int>> &res,TreeNode*node,int h){
        if(node==NULL) return;
        res[h].push_back(node->val);
        level(res,node->left,h-1);
        level(res,node->right,h-1);
    }
    
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        int h=depth(root);
        vector<vector<int>> res(h,vector<int> {});   
        level(res,root,h-1);   
        return res;
    }
};

```
