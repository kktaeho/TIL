# 오늘 배운 내용 작성
## 509 피보나치 requr
```python
- requr 안쓰고
class Solution:
    def fib(self, n: int) -> int:

        if n < 2 :
            return n
        else:    
            return self.fib(n-1) + self.fib(n-2)
- requr 트라이


```