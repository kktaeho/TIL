# 오늘 배운 내용 작성
## 어제 풀던 greedy 1561
```python
class Solution:
    def maxCoins(self, piles: List[int]) -> int:
        piles.sort()
        i, j = 0, len(piles) - 1
        Answer = 0
        while i < j:
            j-=1 # Alice
            Answer += piles[j] # Me
            j-=1
            i+=1 # Bob
        return Answer
```
## 234 linkedlist palindrome
```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def isPalindrome(self, head: Optional[ListNode]) -> bool:
        
        Node = head
        
        anslist = list()
        while Node:
            anslist.append(Node.val)
            Node = Node.next
        
        i, j = 0, len(anslist)-1
        ans = True
        
        while i<j:
            if anslist[i] != anslist[j]:
                ans = False
                break
            else:
                i += 1
                j -= 1
        return ans
        
```
## 21 merge two sorted lists
```python
- 1차 시도
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        
        first = list1
        first_list = list()
        second = list2
        sec_list = list()
        ans_list = list()
        
        while first:
            ans_list.append(first.val)
            first = first.next
            ans_list = sorted(ans_list)
        while second:
            ans_list.append(second.val)
            second = second.next
            ans_list = sorted(ans_list)
        print(ans_list)
```