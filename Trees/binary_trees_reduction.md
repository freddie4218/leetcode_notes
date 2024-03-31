# Tree Reductions:

### Using In-Order and Pre-Order:
```
class Solution:
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        def createTree(preorder: List[int], inorder: List[int]):
            if not preorder:
                return None
            curr_val = preorder[0]
            node = TreeNode(curr_val)
            idx = inorder.index(curr_val)
            node.left = createTree(preorder[1: idx + 1], inorder[:idx])
            node.right = createTree(preorder[idx + 1:], inorder[idx + 1:])
            return node
        
        return createTree(preorder, inorder)

```

### Using In-Order and Post-Order:
```
class Solution:
    def buildTree(self, inorder: List[int], postorder: List[int]) -> Optional[TreeNode]:
        def createTree(inorder: List[int], postorder: List[int]) -> Optional[TreeNode]:
            if not inorder:
                return None
            curr_val = postorder[-1]
            node = TreeNode(curr_val)
            idx = inorder.index(curr_val)
            node.left = createTree(inorder[:idx], postorder[:idx])
            node.right = createTree(inorder[idx + 1:], postorder[idx:-1])
            return node
        return createTree(inorder, postorder)
```