# Tree Traversal:
> Two types of tree traversal:
1. DFS
2. BFS

### Definition for a binary tree node
```
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
```
### DFS - Recursion
Pre-Order:
```
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
```
In-Order:
```
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
```
Post-Order:
```
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
```

### DFS - Iteration
Pre-Order:

```
class Solution:
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root is None:
            return []
        result = []
        stack = [root]
        while stack:
            root = stack.pop()
            result.append(root.val)
            if root.left:
                stack.append(root.left)
            if root.right:
                stack.append(root.right)
        return result
```
In-Order
```
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        
        stack = []
        res = []
        
        while stack or root:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            res.append(root.val)
            root = root.right
        return res
```
Post-Order:
```
class Solution:
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack = []
        res = []
        prev = None
        
        while stack or root:
            while root:
                stack.append(root)
                root = root.left
            root = stack.pop()
            if not root.right or prev == root.right:
                res.append(root.val)
                prev = root
                root = None
            else:
                stack.append(root)
                prev = root
                root = root.right
        return res
```
### BFS - Iteration:


```
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        queue = [root]
        res = []
        
        while queue:
            size = len(queue)
            level = []
            for _ in range(size):
                curr = queue.pop(0)
                if curr.left:
                    queue.append(curr.left)
                if curr.right:
                    queue.append(curr.right)
                level.append(curr.val)
            res.append(level)
        return res
```