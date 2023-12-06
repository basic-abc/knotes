### Applications

- Consider upper and lower limits for each subproblem, i.e. pass them as arguments in recursive implementations

### Reconstruction from traversal

- O(nlogn): Inorder traversal of BST is an array sorted in ascending order, so sorting the preorder can reuse implementation from Binary Tree
- O(n): Ensure the current preorder node is the right child of the node holding the "nearest smallest" value by utilizing a stack

#### Implementation

```
class Solution {
  public TreeNode bstFromPreorder(int[] preorder) {
    int n = preorder.length;
    if (n == 0) return null;

    TreeNode root = new TreeNode(preorder[0]);
    Deque<TreeNode> deque = new ArrayDeque<TreeNode>();
    deque.push(root);

    for (int i = 1; i < n; i++) {
      //Take the last element of the deque as a parent
      // and create a child from the next preorder element
      TreeNode node = deque.peek();
      TreeNode child = new TreeNode(preorder[i]);
      //Adjust the parent
      while (!deque.isEmpty() && deque.peek().val < child.val)
        node = deque.pop();

      // follow BST logic to create a parent-child link
      if (node.val < child.val) node.right = child;
      else node.left = child;
      // add the child into deque
      deque.push(child);
    }
    return root;
  }
}
```

#### Examples

- [1008. Construct Binary Search Tree from Preorder Traversal](https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/editorial/)
