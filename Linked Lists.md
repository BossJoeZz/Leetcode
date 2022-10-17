# Linked Lists
splice - 拼接

Linked Lists Leetcode problems

Easy:
* 21 Merge Two Sorted Lists
* 160 Intersection of Two Linked Lists
* 206 Reverse Linked List
* 83 Remove Duplicates from Sorted List
* 234 Palindrome Linked List

Medium:
* 19. Remove Nth Node From End of List
* 

## 21 Merge Two Sorted Lists(Easy)
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
        if l1 is None: return l2 # not l1的意思就是l1 is None
        if l2 is None: return l1 
        
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
                
        prev.next = l1 if l1 is True else l2 # 更加简便的if else写法
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

## 160 Intersection of Two Linked Lists(Easy)
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
```

## 206 Reverse Linked List (Easy)
https://leetcode.com/problems/reverse-linked-list/

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# 1. 双指针

class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if head is None: return 
        
        before = None
        current = head
        
        while current: # while current is not None:
            after = current.next
            current.next = before
            before = current
            current = after
        return before

# 2. 递归

class Solution:
    def reverseList(self, head: ListNode) -> ListNode:
        if not head or not head.next:
            return head
        nextNode = self.reverseList(head.next)
        head.next.next = head
        head.next = None
        # print(nextNode)
        return nextNode
```        

## 83 Remove Duplicates from Sorted List (Easy)
https://leetcode.com/problems/remove-duplicates-from-sorted-list/)

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if not head:
            return head

        current = head
        while current.next:
            if current.val == current.next.val: 
                current.next = current.next.next // 也许这里原本重复的node就自动断开？or重叠？
            else:
                current = current.next

        return head
```

## 234 Palindrome Linked List (Easy)
https://leetcode-cn.com/problems/palindrome-linked-list/

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# 1. 对比反转
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        vals = []
        current = head
        while current:
            vals.append(current.val)
            current = current.next
        return vals == vals[::-1]
 
# 2. stack
class Solution:
    def isPalindrome(self, head: ListNode) -> bool:
        if not head: return True
        stack = []
        p = head
        while p:
            stack.append(p.val)
            p = p.next
        while head:
            if head.val != stack.pop():
                return False
            head = head.next
        return True        
```
