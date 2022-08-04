# 오늘 배운 내용 작성
## leetcode 771
- list도 가능하나 수가 많으면 시간 오래걸려 아래 방식 추천 이건 n제곱
```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        jewelslist = list(jewels)
        stoneslist = list(stones)
        count = 0
        for stone in stoneslist:
            if stone in jewelslist:
                count +=1
        return count
```

- 딕셔너리 활용한 n개 문제, 해쉬테이블임
- 해쉬테이블 = 딕셔너리라고 보면될 듯

```python
class Solution:
    def numJewelsInStones(self, jewels: str, stones: str) -> int:
        jewelsList = list(jewels)
        stonesList = list(stones)
        Answer = 0
        Counts = collections.Counter(stonesList)
        for key, value in Counts.items():
            if key in jewelsList:
                Answer += value
        return Answer
```

## 1295
- 어디가 틀린거지..

```python
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        num = [str(integer) for integer in nums]
        nums = ''.join(num)
        nums = int(nums)
        if nums > 0 :
            digits = int(math.log10(nums))+1
        elif nums == 0 :
            digits = 1
        elif nums < 0 :
            digits = int(math.log10(-nums))+2
        return digits
```
- 정답 리스트 컴프리핸션 쓰면 간단하게 해결 가능

```python
class Solution:
    def findNumbers(self, nums: List[int]) -> int:
        Res = [len(str(num)) for num in nums]
        Answer = 0
        for n in Res:
            if n%2 == 0:
                Answer += 1
        return Answer
```

## 2094
```python
class Solution:
    def findEvenNumbers(self, digits: List[int]) -> List[int]:
        ans = random.randint(digits)
        print(ans)
```
- 난 못품.. 정답
```python
# 첫번째로 올 수 있는 경우의 수: 0 뺴고 전부다...
# 두번째는 모두가 올 수 있음..
# 세번째: 짝수만 올 수 있음..
# 위 조건을 만족하는 3가지 index (First, Second, Third)를 for loop를 돌면서
# 같은 숫자를 동시에 쓰는지에 대한 if 조건만 주시면
# 모든 숫자를 만들어 낼 수 있다!
# 그리고 정렬하면 정답

class Solution:
    def findEvenNumbers(self, digits: List[int]) -> List[int]:
        First = [i for i, digit in enumerate(digits) if digit != 0]
        Second = list(range(0, len(digits)))
        Last = [i for i, digit in enumerate(digits) if digit %2 == 0]
        Answer = set()
        for i in First:
            for j in Second:
                for k in Last:
                    if i != j and i != k and j != k:
                        Answer.add(digits[i]*100 + digits[j]*10 + digits[k])
        Answer = list(Answer)
        Answer.sort()
        return Answer
```

## 66
- 내 풀이
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        digi = str(digits)
        digi[-1] + 1
        digit = [int() for i in digi]
        digits[-1]+1
        print(digits)
```
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        digits[-1] = digits[-1]+1
        print(digits)
```
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        digits[-1] = digits[-1]+1
        if len(digits) == 1:
            digits.append(1)
            if digits[-1] == 10:
                digits[-2]+1
        return digits
        print(digits)
```
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        digits[-1] = digits[-1]+1
        if len(digits) == 1:
            digits.append(1)
            if digits[-1]+1 == 10:
                digits.insert(0,1)
        return digits
        print(digits)
            
```
- 정답
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        res = int(''.join([str(di) for di in digits]))
        res += 1
        return [int(idx) for idx in list(str(res))]
```
- 편법 풀이
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        Index = len(digits)-1
        while Index >= 0:
            digits[Index] += 1
            if digits[Index] != 10:
                return digits
            else:
                digits[Index] = 0
            Index -= 1
        if digits[0] == 0:
            digits.insert(0, 1)
        return digits
```
```python
class Solution:
    def plusOne(self, digits: List[int]) -> List[int]:
        Index = len(digits) - 1
        while Index >= 0:
            digits[Index] += 1
            # 자릿수가 바뀌지 않았을 경우
            if digits[Index] < 10:
                break
            # 여기로 왔다는 말은 Index가 가리키고 있는 게 10이라는 뜻
            digits[Index] = 0
            Index -= 1
            if Index == -1:
                digits.insert(0, 1)
            # 자릿수가 바뀐 경우
        return digits
```
## 1512
풀이

```python

```

- 정답
```python
class Solution:
    def numIdenticalPairs(self, nums: List[int]) -> int:
        # 모든 digit에 대한 count를 구한다.
        Counts = collections.Counter(nums)
        # count가 2개 이상인 경우에 대해서 nC2 (pair의 수)를 Answer에 더한다
        Answer = 0
        for key, value in Counts.items():
            if value > 1:
                Answer += value * (value-1) / 2 # nC2
        return int(Answer)
```