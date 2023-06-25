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


## 방문 길이

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/49994
-   Python3
-   비고 : 2023.06.24 이후 set을 이용하여 다시 풀어볼 것.

<details>
<summary>접기/펼치기</summary>

```py
def solution(dirs):
    answer = 0
    location = [0,0]
    xRoad = [[0 for j in range(11)] for i in range(11)]
    yRoad = [[0 for j in range(11)] for i in range(11)]
    for i in dirs:
        if i == "U":
            y = location[1] - 1
            if y < -5:
                continue
            y = y + 5
            if yRoad[location[0]][y] == 0:
                answer += 1
                yRoad[location[0]][y] = 1
            location[1] = y - 5
        elif i == "D":
            y = location[1]
            if y + 1 > 5:
                continue
            y = y + 5
            if yRoad[location[0]][y] == 0:
                answer += 1
                yRoad[location[0]][y] = 1
            location[1] = y - 4
        elif i == "L":
            x = location[0] - 1
            if x < -5:
                continue
            x = x + 5
            if xRoad[x][location[1]] == 0:
                answer += 1
                xRoad[x][location[1]] = 1
            location[0] = x - 5
        else:
            x = location[0]
            if x + 1 > 5:
                continue
            x = x + 5
            if xRoad[x][location[1]] == 0:
                answer += 1
                xRoad[x][location[1]] = 1
            location[0] = x - 4
    return answer
```
</details>


## 영어 끝말잇기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/12981
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(n, words):
    answer = [0,0]
    wordCheck = [words[0]]
    for i in range(1,len(words)):
        if words[i][0] != words[i-1][-1] or words[i] in wordCheck:
            answer[0] = i%n + 1
            answer[1] = i//n +1
            break
        wordCheck.append(words[i])
    return answer
```
</details>
