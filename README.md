# Binary-Search-Tree-to-Greater-Sum-Tree

Given the root of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.

As a reminder, a binary search tree is a tree that satisfies these constraints:

The left subtree of a node contains only nodes with keys less than the node's key.
The right subtree of a node contains only nodes with keys greater than the node's key.
Both the left and right subtrees must also be binary search trees.
 

Example 1:

Input: root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
Output: [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]
Example 2:

Input: root = [0,null,1]
Output: [1,null,1]
 
Constraints:

The number of nodes in the tree is in the range [1, 100].
0 <= Node.val <= 100
All the values in the tree are unique.

# SOLUTION #

Intuition
The idea is to traverse the BST in reverse in-order (right-root-left) and update the value of each node by adding the sum of all the nodes greater than or equal to the current node.

Approach
Initialize a global variable val to keep track of the running sum.
Perform a reverse in-order traversal of the BST:
Recursively call the bstToGst function on the right subtree.
Update the current node's value by adding the val to it.
Recursively call the bstToGst function on the left subtree.
Return the modified root of the BST.


Complexity
Time complexity:O(n),where n is the number of nodes in the BST.
Space complexity:O(h),where h is the height the BST.


# JAVA CODE #

**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    int val =0;
   
    public TreeNode bstToGst(TreeNode root) {
   
        if(root.right!=null)bstToGst(root.right);
   
        val=root.val=val+root.val;
   
        if(root.left!=null)bstToGst(root.left);
   
        return root;
        
    }
}
