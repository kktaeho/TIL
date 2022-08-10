# 오늘 배운 내용 작성
## 21 merge linkedlist

```python
#         #방법1. 두개의 모든리스트를 담는 새로운 리스트를 생성하여 문제르 푸는 방법
#         head = None
#         while list1 and list2:
#             if  list1.val<list2.val
#                 newnode = listnode(list1.val, None)
#                 list1 = list1.next
                
        Header = listnode(0,None)
        Pointer = Header
        
        while list1:
            Pointer.next = listnode(list1.val,None)
            Pointer = Pointer.next
            list1 = list1.next
        while list2:
            Header.append(list1.val)
            Header.next
        
        #방법 2 근데 리스트1 혹은 2가 남아있음
        while list1:
            #list1이 list2보다 작을때, list1을 새로운 linkedlist에 추가
            if list1.val < list2.val:
                Pointer.next = listnode(list1.val,None)
                Pointer = Pointer.next
                list1 = list1.next
            else:
                Pointer.next = listnode(list2.val,None)
                Pointer = Pointer.next
                list2 = list2.next
        while list1:
            Pointer.next = listnode(list1.val,None)
            Pointer = Pointer.next
            list1 = list1.next
        while list2:
            Pointer.next = listnode(list2.val,None)
            Pointer = Pointer.next
            list2 = list2.next
        return Hedader.next

#or써도 가능
class Solution:
    def mergeTwoLists(self, list1, list2) -> Optional[ListNode]:
        Header = ListNode(0, None)
        Pointer = Header
        while list1 or list2:
            if list1 and list2:
            # list1이 list2보다 작을 때, list1을 새로운 LinkedList에 추가해준다.
                if list1.val < list2.val:
                    Pointer.next = ListNode(list1.val, None)
                    Pointer = Pointer.next
                    list1 = list1.next
                else:
                    Pointer.next = ListNode(list2.val, None)
                    Pointer = Pointer.next
                    list2 = list2.next
            else:
                if list1:
                    Pointer.next = ListNode(list1.val, None)
                    Pointer = Pointer.next
                    list1 = list1.next
                elif list2:
                    Pointer.next = ListNode(list2.val, None)
                    Pointer = Pointer.next
                    list2 = list2.next
        return Header.next
- 
class Solution:
    def mergeTwoLists(self, list1, list2) -> Optional[ListNode]:
        Header = Pointer = ListNode(0, None)
        while list1 and list2:
            if list1.val < list2.val:
                Pointer.next = list1
                Pointer = Pointer.next
                list1 = list1.next
            else:
                Pointer.next = list2
                Pointer = Pointer.next
                list2 = list2.next
        if list1:
            Pointer.next = list1
        if list2:
            Pointer.next = list2
        return Header.next
```

##206
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        
        Prev = None
        pointer = head
        
        while pointer:
            Next = pointer.next
            pointer.netx = Prev
            
            Prev = pointer
            pointer = Next
            
        return Prev
            
```
