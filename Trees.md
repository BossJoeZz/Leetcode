# 二叉搜索树(BST)

二叉搜索树的特点： 
                * 若左子树非空，则所有左子树值均小于节点的值；
                * 若右子树非空，则所有右子树的值均大于节点的值；

inorder - 中序，二叉搜索树的中序遍历得到的数组为排序数组

# leetcode problems

Easy:
* 94. Binary Tree Inorder Traversal

94. Binary Tree Inorder Traversal
https://leetcode.com/problems/binary-tree-inorder-traversal/

```python
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root == None: return []
        res,stack = [],[]
        node = root 

        while node or stack:
            if node:
                stack.append(node)
                node = node.left
            else:
                node = stack.pop()
                res.append(node.val)
                node = node.right
        return res
```
