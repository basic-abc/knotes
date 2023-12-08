### Application
- Approach binary tree questions by considering the operation order & traversal order - when to apply condition check, when to update answer with valid state

### Traversal
#### Preorder
- Root -> Left -> Right

#### Inorder
- Left -> Root -> Right
- Split at a given index, left of the index represents the left subtree; right of the index represents the right subtree.

#### Postorder
- Left -> Right -> Root

### Reconstruction from traversal
- Binary tree can be reconstructed with preorder & inorder traversal OR postorder & inorder.

#### Implementation
```
class Solution {
    int preorderIndex;
    Map<Integer, Integer> inorderIndexMap;

    public TreeNode buildTree(int[] preorder, int[] inorder) {
        preorderIndex = 0;
        // build a hashmap to store value -> its index relations
        inorderIndexMap = new HashMap<>();
        for (int i = 0; i < inorder.length; i++) {
            inorderIndexMap.put(inorder[i], i);
        }
        return arrayToTree(preorder, 0, preorder.length - 1);
    }

    private TreeNode arrayToTree(int[] preorder, int left, int right) {
        // if there are no elements to construct the tree
        if (left > right) return null;

        // select the preorder_index element as the root and increment it
        int rootValue = preorder[preorderIndex++];
        TreeNode root = new TreeNode(rootValue);

        // build left and right subtree
        // excluding inorderIndexMap[rootValue] element because it's the root
        root.left = arrayToTree(preorder, left, inorderIndexMap.get(rootValue) - 1);
        root.right = arrayToTree(preorder, inorderIndexMap.get(rootValue) + 1, right);
        return root;
    }
}
```

#### Examples
- [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/editorial/)