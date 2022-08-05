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
# two pointer
        sort_num = sorted(nums)
        i, j = 0, len(nums)-1
        
        while i < j :
            sort_num[i] # 얘를 변수처리해야 제대로 작동하는듯
            sort_num[j]
            sum_num = sort_num[i] + sort_num[j] - target
            if sum_num > 0:
                j -= 1
            elif sum_num < 0:
                i += 1
            else : # sum_num = 0
                break
        if sort_num[i] != sort_num[j]:
            return nums.index(sort_num[i]), nums.index(sort_num[j])
        else:
            return [ i for i, num in enumerate(nums) if num == sort_num[i] ]
        
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

## 15 3sum

```python
- 풀이
i, j, k = 0, len(nums)-2, len(nums)-1
        while i<k :
            left = nums[i]
            centers = nums[j]
            right = nums[k]
            ans = left + centers + right
            if ans == 0:
                return ans
            elif ans > 0:
                j-=1
            else :
                i +=1
                
                return ans
```
- 답
```python
# Three num / Two-pointer를 활용한 해법
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        Answer = set()
        nums.sort()
        for i in range(len(nums)-2):
            nums[i] == nums[0]
            j, k = i + 1, len(nums)-1
            while j < k:
                if nums[i] + nums[j] + nums[k] == 0:
                    Answer.add( tuple([nums[i], nums[j], nums[k]] ))
                    j, k = j +1, k-1
                elif nums[i] + nums[j] + nums[k] > 0:
                    k -= 1
                else:
                    j += 1
        return list(Answer)
```