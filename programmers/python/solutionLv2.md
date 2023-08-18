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


## 점프와 순간 이동

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/12980
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(n):
    ans = 0
    while n > 0:
        ans += n % 2
        n = n // 2
    return ans
```
</details>


# 뒤에 있는 큰 수 찾기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/154539
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(numbers):
    answer = [-1 for i in range(len(numbers))]
    stackArr = []
    pass
    for idx, i in enumerate(numbers):
        while stackArr and numbers[stackArr[-1]] < i:
            answer[stackArr.pop()] = i
        stackArr.append(idx)
    return answer
```
</details>


# 오픈채팅방

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/42888
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
nickname = {}
messageLog = []
def recordLog(record):
    recordStrArr = record.split(" ")
    if recordStrArr[0] == "Enter":
        nickname[recordStrArr[1]] = recordStrArr[2]
        messageLog.append([1,recordStrArr[1]])
    elif recordStrArr[0] == "Leave":
        messageLog.append([2,recordStrArr[1]])
    else:
        nickname[recordStrArr[1]] = recordStrArr[2]
def printLog(log):
    result = f'{nickname[log[1]]}님이 {"들어왔습니다" if log[0]==1 else "나갔습니다"}.'
    return result
def solution(record):
    answer = []
    for i in record:
        recordLog(i)
    for i in messageLog:
        answer.append(printLog(i))
    return answer
```
</details>


# 스킬트리

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/49993
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
import re
def solution(skill, skill_trees):
    answer = 0
    for tree in skill_trees:
        tree = re.sub(f'[^{skill}]','',tree)
        if skill.find(tree) == 0:
            answer += 1
    return answer
```
</details>


# 전화번호 목록

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/42577
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(phone_book):
    numberDict = dict.fromkeys(phone_book, 1)
    for number in numberDict:
        tempNum = ""
        for num in list(number):
            tempNum += num
            if tempNum in numberDict and tempNum != number:
                return False
    return True
```
</details>


# 이진 변환 반복하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/70129
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(s):
    countZero = 0
    count = 0
    while s != "1":
        countZero += s.count("0")
        count += 1
        s = bin(len(s.replace("0","")))[2:]
    answer = [count,countZero]
    return answer
```
</details>


# 기능 개발

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/42586
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
import math
def solution(progresses, speeds):
    answer = []
    minDay = math.ceil((100-progresses[0])/speeds[0])
    countProgress = 1
    for idx, i in enumerate(progresses[1:]):
        day = math.ceil((100-i)/speeds[idx+1])
        if minDay >= day:
            countProgress += 1
        else:
            minDay = day
            answer.append(countProgress)
            countProgress = 1
    day = math.ceil((100-progresses[-1])/speeds[-1])
    answer.append(countProgress if minDay >= day else 1)
    return answer
```
</details>

