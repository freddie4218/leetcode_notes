# Binary Tree

> A Binary Tree is one of the most typical tree structure. As the name suggests, a binary tree is a tree data structure in which each node has
> at most two children, which are referred to as the left child and the right child.

### Types of Binary Trees:
##### 1. Full Binary Tree:
In a full binary tree, each node has either 0 or 2 children.
There are no nodes with only one child.
All leaf nodes are at the same level.
Every non-leaf node has exactly two children.
##### 2.Complete Binary Tree:
In a complete binary tree, all levels except possibly the last level are fully filled, and the last level is filled from left to right.
It means every level, except possibly the last, is completely filled, and all nodes are as far left as possible.
This type of tree is efficient for storage in arrays.
##### 3. Perfect Binary Tree:
In a perfect binary tree, all internal nodes have exactly two children and all leaf nodes are at the same level.
It is both full and complete.
The number of nodes at each level doubles as you move down the tree from the root.
##### 4.Balanced Binary Tree:
In a balanced binary tree, the height of the left and right subtrees of any node differ by at most one.
It ensures that the height of the tree is minimized, leading to efficient operations such as insertion, deletion, and search.
Balanced binary trees can come in various forms such as AVL trees, Red-Black trees, etc.

### Visual Representations:

```
Full Binary Tree:
        1
      /   \
     2     3
    / \
   4   5    

Complete Binary Tree:
        1
      /   \
     2     3
    / \   /
   4   5 6

Perfect Binary Tree:
        1
      /   \
     2     3
    / \   / \
   4   5 6   7

Balanced Binary Tree:
        1
      /   \
     2     3
    / 
   4   


```