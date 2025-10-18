# Bst Inorder


## Introduction of BST

A binary search tree (BST) is defined as follows.

1. The left subtree of a node contains only nodes with keys less than the node's key.
2. The right subtree of a node contains only nodes with keys greater than the node's key.
3. Both the left and right subtrees must also be binary search trees.

## Inorder traversal

1. Recursively traverse the current node's left subtree.
2. Visit the current node (in the figure: position green).
3. Recursively traverse the current node's right subtree.

The implementation of this recurvise definition is as follows

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
def inorder_traversal(root):
  ans = []
  # helper function to traverse tree recursively
  def helper(root):
    if not root:
      return
    helper(root.left)
    ans.append(root.value)
    helper(root.right)
  helper(root)
  return ans
```

To implement the inorder traversal in iterative way, we use stack.

```python
def inorder_traversal(root):
  ans = []
  stack = []
  curr = root
  while stack or curr:
    while curr:
      stack.append(curr)
      curr = curr.left
    curr = stack.pop()
    ans.append(curr.val)
    curr = curr.right
  return ans
```

## Application problems
### leetcode 98
Validate Binary Search Tree
We can use the property of inorder traversal to check if the tree is a valid BST.
```python
def is_valid_bst_recursive(root):
  prev = float('-inf')
  def helper(root):
    if not root:
      return True
    if not helper(root.left):
      return False
    if root.val <= prev:
      return False
    self.prev = root.val
    return helper(root.right)
  return helper(root)

def is_valid_bst_iterative(root):
  # iterative inorder traversal
  stack = []
  prev = float('-inf')
  curr = root
  while stack or curr:
    while curr:
      stack.append(curr)
      curr = curr.left
    curr = stack.pop()
    if curr.val <= prev:
      return False
    prev = curr.val
    curr = curr.right
  return True
```
### leetcode 230
Kth Smallest Element in a BST
We can use the property of inorder traversal to find the kth smallest element in a BST.

```python
def kth_smallest(root, k):
  stack = []
  curr = root
  while stack or curr:
    while curr:
      stack.append(curr)
      curr = curr.left
    curr = stack.pop()
    k -= 1
    if k == 0:
      return curr.val
    curr = curr.right

```


---

> Author: Yeu-Chern Harn  
> URL: http://localhost:1313/bst-inorder/  

