# 오늘 배운 내용 작성
## 739

```python
class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        
        ans = [0 for i in range(len(temperatures))]
        stack = [ [-1, temperatures.pop(0) ]]
        
        for index, temp in enumerate(temperatures):
            while stack and stack[-1][1] < temp:
                stackIndex, stackTemp = stack.pop()
                ans[stackIndex] = index - stackIndex
              
            else :
                stack.append([index, temp])
                
        return ans
- 정답

class Solution:
    def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
        
        ans = [0 for i in range(len(temperatures))]
        stack = [ [-1, temperatures.pop(0) ]]
        
        for index, temp in enumerate(temperatures):
            while stack and stack[-1][1] < temp:
                stackIndex, stackTemp = stack.pop()
                ans[stackIndex+1] = index - stackIndex
                #stackIndex에 1 더하면 해결되는데 왜그러지
              
            else :
                stack.append([index, temp])
                
        return ans
```

## 23

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
        
        ans = []
        for i in lists:
            while i :
                heapq.heappush(ans, i.val)
                i = i.next
        ansnode = ListNode(0, None)
        pointer = ansnode
        
        while len(ans) != 0 :
            pointer.next = ListNode(heapq.heappop(ans), None)
            
            pointer = pointer.next
        return ansnode.next
```