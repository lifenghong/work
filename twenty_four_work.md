## 问题：
```
Given an integer array with no duplicates. A maximum tree building on this array is defined as follow:

The root is the maximum number in the array.
The left subtree is the maximum tree constructed from left part subarray divided by the maximum number.
The right subtree is the maximum tree constructed from right part subarray divided by the maximum number.
Construct the maximum tree by the given array and output the root node of this tree.

Example 1:
Input: [3,2,1,6,0,5]
Output: return the tree root node representing the following tree:

      6
    /   \
   3     5
    \    / 
     2  0   
       \
        1
  ```
  ## 分析：
  ##### 这是我第三次做二叉树类似的题，还是用了老方法，递归，这道题主要是在构造二叉树那块我不太懂，其实就是将对一个数组处理的问题分解成对两个子数组处理的过程。 
##### 大致的做法如下：先对整个数组进行一次扫描，找出最大的数及其对应的坐标，将此最大值当成根节点的值。根据这个最大数对应的坐标，将原数组分成左右两个子数组，分别递归调用构建最大二叉树的函数。左数子组生成的最大二叉树作为原来根节点的左子树，右子数组生成的最大二叉树作为原来根节点的右子树。 
##### 递归函数的终止状态是当传进来的数组小于等于1时。若等于1，直接构造一棵只有一个节点的树，节点的值为该数组中唯一的数的值；若小于1，直接返回NULL。
## 代码：
```cpp
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
    TreeNode* constructMaximumBinaryTree(vector<int>& nums) {
       if(nums.size()<1)
           return NULL;
        if(nums.size()==1){
            
         TreeNode*node=new TreeNode(nums[0]);
        return node;
        }
        if(nums.size()>1)
        {
            int max_sit=0;
            int max=nums[0];
            for(int i=0;i<nums.size();i++)
            {
                if(nums[i]>max)
                {
                    max_sit=i;
                    max=nums[i];
                }
            }
            TreeNode*node=new TreeNode(max);
            vector<int>left,right;
            for(int i=0;i<max_sit;i++)
                left.push_back(nums[i]);
            for(int i=max_sit+1;i<nums.size();i++)
                right.push_back(nums[i]);
            TreeNode *left_node, *right_node;
            left_node = constructMaximumBinaryTree(left); 
            right_node = constructMaximumBinaryTree(right);  
            node->left=left_node;
            node->right=right_node;
            return node;
            
        }
        }
};
```
