# Solution: time complexity: O(n)
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
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
      
  /*
    Our base cases.
    How our recursion stops.
    When we have an answer.
    1.) If the node we are holding is null then we can't search...just return null
    2.) If we find either value return ourselves to the caller
    Remember, we are "grabbing"/"holding" 'root' in this call.
  */
  if (root == null) return null;
  if (root.val == p.val || root.val == q.val) return root;
  
  /*
    'root' doesn't satisfy any of our base cases.
    Search left and then search right.
  */
  TreeNode leftSearchResult = lowestCommonAncestor(root.left, p, q);
  TreeNode rightSearchResult = lowestCommonAncestor(root.right, p, q);
  if(leftSearchResult != null && rightSearchResult != null){
      return root;
  }else{
        return (leftSearchResult == null )? rightSearchResult : leftSearchResult ;
  } 
}
}
```
