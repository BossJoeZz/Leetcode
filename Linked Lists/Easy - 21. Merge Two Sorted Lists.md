# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

# 1. 迭代

class Solution:
    def mergeTwoLists(self, l1: ListNode, l2: ListNode) -> ListNode:
        if l1 is None: return l2
        if l2 is None: return l1
        
        head = ListNode()
        prev = head
        
        while l1 and l2:
            if l1.val < l2.val:
                prev.next = l1
                l1 = l1.next
                prev = prev.next
            else:
                prev.next = l2
                l2 = l2.next
                prev = prev.next
                
        prev.next = l1 if l1 else l2
        return head.next
 
# 2. 递归
 
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

