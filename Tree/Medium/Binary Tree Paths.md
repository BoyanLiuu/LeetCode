 ``` Java
 class Solution {
    // Time complexity: O(n)
  public void helper(TreeNode root, String path, LinkedList<String> paths) {
    if (root != null) {
      path += root.val;
      // We only add into list if it is a path to leaf
      if ((root.left == null) && (root.right == null))  
        paths.add(path);  // update paths
      else {
        path += "->";  // extend the current path
        helper(root.left, path, paths);
        helper(root.right, path, paths);
      }
    }
  }

  public List<String> binaryTreePaths(TreeNode root) {
    LinkedList<String> paths = new LinkedList();
    helper(root, "", paths);
    return paths;
  }
}
 ```
