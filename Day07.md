# 오늘 배운 내용 작성
## leetcode 1480


```python
class Solution:
    def runningSum(self, nums: List[int]) -> List[int]: #nums: list[int]는 nums가 int형태의 리스트라는 것을 설명해주는 것
        sumnums = []
        
        for i in range(len(nums)):
            sumnums.append(sum(nums[0:i+1]))
        return sumnums
```

## leetcode
1. list sum
   - list의 개념 (list.append, list.pop)
   - for loop 사용가능하냐
2. list of list(nested list)
   - nested list의 개념
   - 2중 for loop를 쓸 수 있냐
   - max를 구할 수 있느냐
```python
max = -1
for i in range(len(accounts)):
    currentSum=0
    for j in range(len(accounts[i])):
        currentSum+=accounts[i][j]
        if max<currentSum:
            max = sum(accounts[i])
    return max
```
3. 