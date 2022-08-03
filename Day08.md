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
        return s == s_reverse
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