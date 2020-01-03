## Solution 1 Run time:0 ms
```Java 
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        return inorderTraversal(p,q);
        
    }
    public boolean inorderTraversal(TreeNode p_cur, TreeNode q_cur){
        if(p_cur == null && q_cur == null)return true;
        if(p_cur == null && q_cur != null) return false;
        if(p_cur != null && q_cur == null) return false;
        
        if(p_cur.val !=q_cur.val)return false;
        return inorderTraversal( p_cur.left, q_cur.left) && inorderTraversal( p_cur.right, q_cur.right);
    
    }
}
```

