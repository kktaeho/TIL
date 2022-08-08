# 오늘 배운 내용 작성
## leetcode 15 3sum

```python
- 내풀이 
ans = []
        # i 반복문 설정
        for i in range(len(nums)-2):
            # j, k 값 지정
            j, k = i+1, len(nums)-1
            # 반복문으로 j가 k보다 작을때 까지
            while j < k:
                if nums[i]+nums[j]+nums[k] == 0:
                    break
                elif nums[i]+nums[j]+nums[k] < 0 :
                    k -= 1
                else : 
                    i += 1
            if i != j and j != k and i != k:
                return ans

- 2차 수정 풀이
class Solution:
    def threeSum(self, nums: List[int]) -> List[List[int]]:
        nums = sorted(nums)
        ans = []
        # i 반복문 설정
        for i in range(len(nums)-2):
            # j, k 값 지정
            j, k = i+1, len(nums)-1
            # 반복문으로 j가 k보다 작을때 까지
            while j < k:
                if nums[i]+nums[j]+nums[k] == 0:
                    break
                elif nums[i]+nums[j]+nums[k] < 0 :
                    j += 1
                else : 
                    k -= 1
            if i != j and j != k and i != k:
                ans.append([nums[i],nums[j],nums[k]])
        return ans
```

## 16 3sum closest
```python
- 시도
# 타겟이랑 더해서 근접값 3개 뽑으면 될듯
        ans = 0
        for num in nums:
            if target == num :
                return ans += num
            elif target 
- 2차 시도
    class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        # 타겟이랑 더해서 근접값 3개 뽑으면 될듯
        ans = 0
        diff = lambda nums : abs(nums - target)
        res = min(nums, key = diff)
        if res >=1 :
            ans+=1
        for num in nums:
            if target == num :
                res.append(num)
- 3차 시도

- 정답
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        # 타겟이랑 더해서 근접값 3개 뽑으면 될듯
        nums.sort()
        anssum = 999999
        
        for i in range(len(nums)-2):
            # j, k 값 지정
            j, k = i+1, len(nums)-1
            # 반복문으로 j가 k보다 작을때 까지
            while j < k:
                currentsum = nums[i]+nums[j]+nums[k]
                if abs(currentsum - target) < abs(anssum -target):
                    anssum = currentsum
                if currentsum > target :
                    k -= 1
                elif currentsum < target:
                    j +=1
                else : 
                    return currentsum
        return anssum
- 정답

16. 3sum closet
class Solution:
    def threeSumClosest(self, nums: List[int], target: int) -> int:
        nums.sort()
        AnswerSum = 999999
        for i in rangee(0, len(nums)-2):
            j, k = i+1, len(nums)-1
            while j < k:
                # 현재 답 구하기
                CurrentSum = nums[i] + nums[j] + nums[k]
                # 현재 답이 지금까지의 최적(AnswerSum)보다 close한가? 그렇다면 AnswerSum에 저장
                if abs(CurrentSum - target) < abs(AnswerSum - target):
                    AnswerSum = CurrentSum
                # 전형적인 Two-pointer
                if CurrentSum > target:
                    k -= 1
                elif CurrentSum < target:
                    j += 1
                else CurrentSum == target:
                    return CurrentSum
        return AnswerSum
```

## 11 container water
```python
- 1차 시도
class Solution:
    def maxArea(self, height: List[int]) -> int:
        # i j 더한거랑 ij-1 더한 거 비교 또 비교 비교하면 될듯 
        
        
        for i in height:
            j = len(height)-1
            
            if i + j <= i + len(height)-2:
                j -= 1
            elif i + j >= i + len(height)-1:
                i += 1
        return i+j
- 2차 시도
class Solution:
    def maxArea(self, height: List[int]) -> int:
        # i j 더한거랑 ij-1 더한 거 비교 또 비교 비교하면 될듯 
                
        for i in height:
            for j in range(len(height)-1) :            
                if i + j < i + len(height)-2:
                    j -= 1
                elif i + j >= i + len(height)-1:
                    i += 1
        return i*j


- 정답
class Solution:
    def maxArea(self, height: List[int]) -> int:
        i, j = 0, len(height)-1
        MaxWater = -9999
        while i < j:
            Water = (j-i) * min(height[i], height[j])
            if Water > MaxWater:
                MaxWater = Water
            if height[i] > height[j]:
                j -= 1
            else:
                i += 1
        return MaxWater
```