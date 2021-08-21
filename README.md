# Path Sum II

## https://leetcode.com/problems/path-sum-ii

Given the root of a binary tree and an integer targetSum, return all root-to-leaf paths where the sum of the node values in the path equals targetSum. Each path should be returned as a list of the node values, not node references.

A root-to-leaf path is a path starting from the root and ending at any leaf node. A leaf is a node with no children.

# Implementation : DFS
```java
/**
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
    public List<List<Integer>> pathSum(TreeNode root, int targetSum) {
        List<List<Integer>> result = new ArrayList<>();
        if(root == null)
            return result;
        List<Integer> path = new ArrayList<>();
        traverse(root, targetSum, result, path);
        return result;
    }
    
    private void traverse(TreeNode node, int targetSum, List<List<Integer>> result, List<Integer> path) {
        path.add(node.val);
        if(node.left == null && node.right == null && node.val == targetSum) {
             result.add(path);
             return;
        }
        if(node.left != null) {
            traverse(node.left, targetSum - node.val, result, new ArrayList<Integer>(path));
        }
        if(node.right != null)
            traverse(node.right, targetSum - node.val, result, new ArrayList<Integer>(path));
            
    }
}

```


