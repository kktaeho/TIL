# 오늘 배운 내용 작성
## leetcode 01 two for
```python
# 1. Two-sum N^2 알고리즘
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
```

- hash table two sum

```python
- 1차 시도
nums_list = list(set(nums))
        counts = collections.Counter(nums_list)
        ans = []
        for key, value in counts.items():
            if value + value == target:
                ans.append(key, key)
        return ans

- 해쉬테이블을 이해하고자하는 구조
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        print(nums)
        Pairs = [target - num for num in nums]
        for i, Pair in enumerate(Pairs):
            if Pair in nums and i != nums.index(Pair):
                return [i, nums.index(Pair)]
- 2차 시도


- 정답
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        HashTable = dict()
        for i, value in enumerate(nums):
            HashTable[value] = i
        Pairs = [target - num for num in nums ]
        for i, Pair in enumerate(Pairs):
            if Pair in HashTable and i != HashTable[Pair]:
                return [i, HashTable[Pair]]
        #print(Pairs)

- two pointer 사용

- 정답
# two pointer
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        nums_sorted = sorted(nums)
        print(nums_sorted)
        i, j = 0, len(nums)-1
        while i < j:
            Left = nums_sorted[i]
            Right = nums_sorted[j]
            Difference = Left + Right - target
            if Difference > 0:
                j -= 1
            elif Difference < 0:
                i += 1
            else: # Difference == 0
                break
        if Left != Right:
            return nums.index(Left), nums.index(Right)
        else:
            return [ i for i, num in enumerate(nums) if num == Left ]
```