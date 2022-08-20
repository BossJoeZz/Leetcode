# 二叉搜索树(BST)

二叉搜索树的特点： 
                * 若左子树非空，则所有左子树值均小于节点的值；
                * 若右子树非空，则所有右子树的值均大于节点的值；

二叉搜索树的中序遍历得到的数组为排序数组

涉及二叉搜索树的一些leetcode问题

Easy:
* 235 Lowest Common Ancestor of a Binary Search Tree

##  235. Lowest Common Ancestor of a Binary Search Tree (Easy)
[https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-search-tree/](https://leetcode-cn.com/problems/lowest-common-ancestor-of-a-binary-search-tree/)
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: TreeNode, p: TreeNode, q: TreeNode) -> TreeNode:
        ancestor = root
        while True:
            if p.val < ancestor.val and q.val < ancestor.val:
                ancestor = ancestor.left
            elif p.val > ancestor.val and q.val > ancestor.val:
                ancestor = ancestor.right
            else:
                break
        return ancestor
