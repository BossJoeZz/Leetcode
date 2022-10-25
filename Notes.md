## Words
splice - 拼接

non-decreasing - 非递减，是为了严谨，可能会有相同的元素，这时候用递增也不太合适

Custom Judge - 自定义评测

palindrome - 回文，就是对称链表

inorder traversal - 中序遍历，即按照左子树-根节点-右子树的顺序来遍历

## Code
python开头def的含义
```python
class Solution: # 括号里面的list1和list2代表输入，箭头后面代表输出，都是自动的
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
```

现在不能用了true了？总之以后尽量用None和not None吧

对于一个linked list a，题目给了heada或者lista都是指开头第一个node，但是当我们return的时候return出来的是整个linked list
如果node迭代，我们return出我们自己定义的中间一个node，这时候就是单node，不是整个linked list
