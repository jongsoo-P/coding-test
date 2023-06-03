# Lv1

## 같은 숫자는 싫어

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/12906
-   Python3

```py
def solution(arr):
    answer = [arr[0]] + [arr[i] for i in range(1,len(arr)) if arr[i-1]!=arr[i]]
    return answer
```
