# Linked Lists Leetcode problems
Easy:
* 21 Merge Two Sorted Lists
* 160 Intersection of Two Linked Lists
* 206 Reverse Linked List
* 83 Remove Duplicates from Sorted List
* 234 Palindrome Linked List

Medium:
* 19 Remove Nth Node From End of List
* 

## 21 Merge Two Sorted Lists(Easy)
https://leetcode.com/problems/merge-two-sorted-lists/

```python

# 1. 迭代法

class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        if not list1: return list2
        if not list2: return list1

        head = ListNode()
        current = head # 看题，提前定义head

        while list1 and list2:
            if list1.val <= list2.val:
                current.next = list1
                list1 = list1.next
            
            else:
                current.next = list2
                list2 = list2.next
                
        p = p.next # 两次循环都要用这个语句，可以直接汇总

        current.next = list1 if list2 is not None else list2
        return head.next # 要return head的next
 
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
        node1 = headA
        node2 = headB
        while node1 != node2:
            node1 = headB if node1 is None else node1.next # 一定要写成None，这样才能触发终止条件
            node2 = headA if node2 is None else node2.next
        return node1
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
        
        if head is None: return None 
        
        previous = None
        current = head
        
        while current: # while current is not None:
            after = current.next
            current.next = previous
            previous = current
            current = after
        return previous

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
https://leetcode.com/problems/remove-duplicates-from-sorted-list/

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        if not head:
            return head # 必须要加，因为如果head为空，是没有next这个属性的

        current = head
        while current.next: 必须是current.next，否则会报错，因为current为空是没有val这个属性的
            if current.val == current.next.val: 
                current.next = current.next.next # 也许这里原本重复的node就自动断开？or重叠？
            else:
                current = current.next

        return head
```

## 234 Palindrome Linked List (Easy)
https://leetcode.com/problems/palindrome-linked-list/

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
