Linked Lists Leetcode problems

Easy:
* 21 Merge Two Sorted Lists

## 21 Merge Two Sorted Lists(easy)
https://leetcode.com/problems/merge-two-sorted-lists/

```python
# non-decreasing就是升序的意思？

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# 1. 迭代法

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1: return l2 # not l1的意思就是l1 is None
        if not l2: return l1 
        
        head = ListNode() # 这里ListNode()是创建了一个
        prev = head
        
        while l1 and l2: # while l1 and l2 就是l1 and l2 is not None
            if l1.val < l2.val:
                prev.next = l1
                l1 = l1.next
                prev = prev.next
            else:
                prev.next = l2
                l2 = l2.next
                prev = prev.next
                
        prev.next = l1 if l1 else l2 # 更加简便的if else写法
        return head.next
 
# 2. 递归法
 
class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if not l1: return l2 # 这里是终止条件，返回最后一个小圈，然后开始环环相链  
        if not l2: return l1
        if l1.val <= l2.val:  
            l1.next = self.mergeTwoLists(l1.next,l2)
            return l1 # 这里应有return，是为了返回整个大圈集合
        else:
            l2.next = self.mergeTwoLists(l1,l2.next)
            return l2
            # 每一次的递归都会return l1或l2，最后顺利链接上
```

## 160 Intersection of Two Linked Lists(easy)
https://leetcode.com/problems/intersection-of-two-linked-lists/

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        p1 = headA
        p2 = headB
        while p1 != p2:
            p1 = headB if p1 is None else p1.next
            p2 = headA if p2 is None else p2.next
        return p1
