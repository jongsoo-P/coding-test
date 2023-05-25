# Lv0

## 특이한 정렬

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120880
-   python

```py
def solution(numlist, n):
    answer = sorted(numlist, key = lambda x: (abs(x-n),-x))
    return answer
```
