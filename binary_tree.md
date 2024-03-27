# Binary Tree

> A Binary Tree is one of the most typical tree structure. As the name suggests, a binary tree is a tree data structure in which each node has
> at most two children, which are referred to as the left child and the right child.

Two types of tree traversal:
1. DFS
2. BFS

### Definition for a binary tree node
'''
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
'''
### DFS - Recursion
Pre-order:
'''
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        def preOrder(root):
            if not root:
                return
            result.append(root.val)
            preOrder(root.left)
            preOrder(root.right)
        preOrder(root)
        return result
'''
In-order:
'''
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        def inOrder(root):
            if not root:
                return
            inOrder(root.left)
            result.append(root.val)
            inOrder(root.right)
        inOrder(root)
        return result
'''
Post-order:
'''
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        result = []
        def postOrder(root):
            if not root:
                return
            postOrder(root.left)
            postOrder(root.right)
            result.append(root.val)
        postOrder(root)
        return result
'''

### DFS - Iteration
Pre-order
