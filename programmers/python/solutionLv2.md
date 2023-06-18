# Lv2


## 올바른 괄호

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/12909
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(s):
    answer = []
    for i in s:
        if i =="(":
            answer.append(i)
        else:
            if(len(answer)<1):
                return False
            answer.pop()
    if len(answer)>0:
        return False
    return True
```
</details>
