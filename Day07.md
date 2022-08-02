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
max = -1 #max 0이 아닌 -1인 이유는 constraints를 봤을때 인자가 1~50까지라 0이나 -1이나 상관없지만 currentSum이랑 겹칠까봐 -1적은거 작게할수록 좋음
for i in range(len(accounts)):
    currentSum=0
    for j in range(len(accounts[i])):
        currentSum+=accounts[i][j]
        if max<currentSum:
            max = sum(accounts[i])
    return max
```
3. 내 풀이
```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        strin = []
        for i in range(1, n+1):
            if i%3 == 0 and i%5 == 0:
                strin.append("FizzBuzz")
            elif i%5 == 0:
                strin.append("Buzz")
            elif i%3 == 0:
                strin.append("Fizz")
            else:
                strin.append(str(i))
        return strin
```
- 다른 방법
```python
class Solution:
    def fizzBuzz(self, n: int) -> List[str]:
        Answer = []
        for i in range(n):
            if (i+1) % 3 == 0 and (i+1) % 5 == 0:
                Answer.append('FizzBuzz')
            elif (i+1) % 3 == 0:
                Answer.append('Fizz')
            elif (i+1) % 5 == 0:
                Answer.append('Buzz')
            else:
                Answer.append(str(i+1))
        return Answer
```
4.  내 풀이 틀림
```python
class Solution:
    def numberOfSteps(self, num: int) -> int:
        count = 0
        for i  in range(num):
            if num % 2 == 0:
                return num / 2
            elif num % 2 != 0:
                return num -1
            
```
- 맞는 풀이
```python
class Solution:
    def numberOfSteps(self, num: int) -> int:
        CurrentNum = num
        nCount = 0
        while CurrentNum != 0:
            if CurrentNum % 2 == 0:
                CurrentNum /= 2
            else:
                CurrentNum -= 1
            nCount += 1
        return nCount
```

5. leet code 383
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        if ransomNote in magazine:
            return True
        elif ransomNote != magazine:
            return False

```

- 정답 풀이
```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        ransomNoteList = list(ransomNote)
        magazineList = list(magazine)
        Answer = True
        for char in ransomNoteList:
            if char not in magazineList: #글자가 없으면
                Answer = False
                break
            else: #글자가 있으면
                CharIdx = magazineList.index(char)
                magazineList.pop(CharIdx)
                #magazineList.pop(magazineList.index(char)) # 위 두줄을 한줄로 가능
        return Answer
```