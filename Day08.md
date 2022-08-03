# 오늘 배운 내용 작성
## leetcode 125
- 내코드
```python
- 1차 시도
from collections import deque
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = "Ameria, Down"
        a = sorted(s)
        b = deque(s)
        c = deque(s)
        for i in range(len(a)):
            if b.pop()==c.popleft():
                return Ture
            else:
                return False
        print(a)
- 2차 시도
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = "".join(filter(str.isalnum, s))
        s = s.lower()
        a = list(s)
        b = list(s[::-1])
        if a == b :
            return True
        else :
            return False

```
- 답안
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        # Step 1.
        # s가 들어 오는데, s에 포함된 모든 글자만 남긴다.
        # (띄어쓰기, 콤마, 쿼트 등등.. 글자 빼고 모두 삭제)
        # Google: How to delete non-character string in python
        s = ''.join(filter(str.isalnum, s))
        print(s)
        # Step 2.
        # 모든 문자를 소문자 (혹은 대문자) 로 바꾼다.
        # Google: How to change char capital to lower in python
        s = s.lower()
        print(s)
        # Step 3.
        # 문자열을 뒤집어서 새로운 변수를 만든다.
        # How to reverse string in python
        s_reverse = s[::-1]
        return s == s_reverse # 얘가 무슨 기능하길래 얘 없으면 안되지?
        # Step 3-2 / 다른 방법 (while, two-pointer를 활용한 방법)
        i, j = 0, len(s)-1
        Answer = True
        while i < j:
            if s[i] == s[j]:
                i += 1
                j -= 1
            else:
                Answer = False
               
        return Answer
```

2. 344

- 내 풀이
```python
class Solution:
    def firstPalindrome(self, words: List[str]) -> str:
        ans = ""
        pa_li = [word for word in words if word == word[::-1]]
        if len(pa_li) !=0:
            ans = pa_li[0]
        return ans
```
- 정답
```python
class Solution:
    def checkPalindrome(self, s: str) -> bool:
        s = ''.join(filter(str.isalnum, s))
        s = s.lower()
        s_reverse = s[::-1]
        return s == s_reverse
    def firstPalindrome(self, words: List[str]) -> str:
        for s in words:
            if self.checkPalindrome(s):
                return s
        return ""
```

## 344
- 정답
```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        i, j = 0, len(s)-1
        while i<j:
            s[i], s[j] = s[j], s[i]
            i+=1
            j-=1
        return s
        
```
## 819
- 내풀이
```python
class Solution:
    def mostCommonWord(self, paragraph: str, banned: List[str]) -> str:
        para_fil = ''.join(filter(str.isalnum, paragraph))
        para = para_fil.split(" ")
        count = 0
        if para == para[]:
            count+=1
        return count
```
- 정답
```python

```

## 2021
- 내풀이 중간에 막힘
```python
class Solution:
    def twoOutOfThree(self, nums1: List[int], nums2: List[int], nums3: List[int]) -> List[int]:
        result = []
        for i in zip(nums1, nums2, nums3):
            if i not in result:
                result.append(i)
                if i>reuslt.append(i).coxunt(2):
                    print(result)
```
```python
class Solution:
    def twoOutOfThree(self, nums1: List[int], nums2: List[int], nums3: List[int]) -> List[int]:
        nums1 = list(dict.fromkeys(nums1))
        nums2 = list(dict.fromkeys(nums2))
        nums3 = list(dict.fromkeys(nums3))
        nums = [nums1+nums2+nums3]
        ans = 0
        cnums = count(nums)
        if cnums >= 2:
            ans.append()
        print(nums1)
```
- 정답
```python
class Solution:
    def twoOutOfThree(self, nums1: List[int], nums2: List[int], nums3: List[int]) -> List[int]:
        # Step1: num1, num2, num3에서 중복을 제거한다.
        # python list delete duplicate
        # Step2: num1+num2+num3 를 합쳐서 하나의 list로 만든다.
        # python concatenate lists to one list
        # Step3: 하나의 list가 된 데이터에서 count를 하여,
        # Step4: 2개 이상인 숫자들만 list 형태로 return 한다.
        AllList = list(set(nums1)) + list(set(nums2)) + list(set(nums3)) # step 1 ~ 2
        Counts = collections.Counter(AllList) # step 3
        Answer = []
        for key, value in Counts.items(): # step4
            if value >= 2:
                Answer.append(key)
        return Answer 
```
