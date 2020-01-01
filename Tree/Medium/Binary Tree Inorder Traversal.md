## Left root right, O(n), cause we have to traverse all the node no matter what
```Java
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> result =  new LinkedList<Integer>();
        return helper(result,root);
        
        
    }
    public List<Integer> helper(List<Integer> result,TreeNode root){
        if(root == null) return result;
        helper(result,root.left);
        result.add(root.val);
        helper(result,root.right);
        return result;
    }
}
```
