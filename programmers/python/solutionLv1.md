# Lv1


## 같은 숫자는 싫어

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/12906
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(arr):
    answer = [arr[0]] + [arr[i] for i in range(1,len(arr)) if arr[i-1]!=arr[i]]
    return answer
```
</details>


## 키패드 누르기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/67256
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(numbers,hand):
    answer = ''
    leftHand = 11
    rightHand = 12
    leftRange = [1,4,7,11]
    rightRange = [3,6,9,12]
    anyRange = [2,5,8,0]
    for i in range(len(numbers)):
        if(numbers[i] in leftRange):
            leftHand = numbers[i]
            answer += "L"
        elif(numbers[i] in rightRange):
            rightHand = numbers[i]
            answer +="R"
        else:
            leftAbs = abs((anyRange.index(leftHand) if leftHand in anyRange else leftRange.index(leftHand)) - anyRange.index(numbers[i])) \
                + (1 if leftHand in leftRange else 0)
            rightAbs = abs((anyRange.index(rightHand) if rightHand in anyRange else rightRange.index(rightHand)) - anyRange.index(numbers[i])) \
                + (1 if rightHand in rightRange else 0)
            if leftAbs > rightAbs:
                rightHand = numbers[i]
                answer +="R"
            elif leftAbs < rightAbs:
                leftHand = numbers[i]
                answer += "L"
            else:
                if hand == "right":
                    rightHand = numbers[i]
                    answer += "R"
                else:
                    leftHand = numbers[i]
                    answer += "L"
    return answer
```
</details>


## 체육복

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/42862
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(n, lost, reserve):
    intersection = list(set(reserve) & set(lost))
    lost = list(set(lost)-set(intersection))
    reserve = list(set(reserve)-set(intersection))
    tempLost = [i for i in lost]
    for i in tempLost:
        if i-1 in reserve:
            lost.remove(i)
            reserve.remove(i-1)
        elif i+1 in reserve:
            lost.remove(i)
            reserve.remove(i+1)
    answer = n-len(lost)
    return answer
```
</details>


## 내적

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/70128
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(a, b):
    answer = sum([i*j for i, j in zip(a,b)])
    return answer
```
</details>


## 삼총사

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131705
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(number):
    answer = 0
    for idx1,i in enumerate(number):
        for idx2,j in enumerate(number[idx+1:]):
            for k in number[idx1+idx2+2:]:
                if i+j+k ==0:
                    answer += 1
    return answer
```
</details>


## 추억점수

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/176963
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(name, yearning, photo):
    point = {name[i]:yearning[i] for i in range(len(name))}
    answer = [sum([point[j] for j in i if j in point]) for i in photo]
    return answer
```
</details>


## 바탕화면 정리

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/161990
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(wallpaper):
    xAxis = []
    yAxis = []
    for yIdx,i in enumerate(wallpaper):
        for xIdx,j in enumerate(i):
            if j == "#":
                yAxis.append(yIdx)
                xAxis.append(xIdx)
    answer = [min(yAxis),min(xAxis),max(yAxis)+1,max(xAxis)+1]
    return answer
```
</details>


## 신고 결과 받기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/92334
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(id_list, report, k):
    countDict = {i:0 for i in id_list}
    reportDict = {i:[] for i in id_list}
    for i in report:
        ids = i.split(" ")
        if ids[0] not in reportDict[ids[1]]:
            reportDict[ids[1]].append(ids[0])
    for key,val in reportDict.items():
        if len(val) >= k:
            for id in val:
                countDict[id] += 1
    answer = [countDict[i] for i in countDict]
    return answer
```
</details>


## 대충 만든 자판

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/160586
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(keymap, targets):
    answer = []
    alphabets = {chr(i):200 for i in range(65,91)}
    for key in keymap:
        for idx,alphabet in enumerate(key):
            alphabets[alphabet] = (idx+1) if alphabets[alphabet] > idx+1 else alphabets[alphabet]
    for target in targets:
        sumKey = []
        for key in target:
            if alphabets[key] == 200:
                sumKey.clear()
                sumKey.append(-1)
                break
            else:
                sumKey.append(alphabets[key])
        answer.append(sum(sumKey))
    return answer
```
</details>


## 기사단원의 무기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/136798
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def measure(num):
    answer = set()
    for i in range(1,int(num**(1/2)+1)):
        if num % i == 0:
            answer.add(i)
            answer.add(num//i)
    return len(answer)

def solution(number, limit, power):
    answer = []
    for i in range(1,number+1):
        num = measure(i)
        if num <= limit:
            answer.append(num)
        else:
            answer.append(power)
    return sum(answer)
```
</details>


## 공원 산책

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/172928
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(park, routes):
    maxX = len(park[0])
    maxY = len(park)
    partY = [[] for i in range(len(park[0]))]
    startPoint = [-1,-1]

    for y,yText in enumerate(park):
        for x,xText in enumerate(list(yText)):
            if xText == "S":
                startPoint[0] = y
                startPoint[1] = x
            partY[x].append(xText)

    for routeText in routes:
        route = routeText.split(" ")
        if route[0] == "E":
            endPoint = startPoint[1] + int(route[1])
            startPoint[1] = endPoint if ((endPoint < maxX) and 
                ("X" not in park[startPoint[0]][startPoint[1]:endPoint+1])) else startPoint[1]
        elif route[0] == "W":
            endPoint = startPoint[1] - int(route[1])
            startPoint[1] = endPoint if ((endPoint > -1) and 
                ("X" not in park[startPoint[0]][(endPoint if endPoint > -1 else 0):startPoint[1]+1])) else startPoint[1]
        elif route[0] == "S":
            endPoint = startPoint[0] + int(route[1])
            startPoint[0] = endPoint if ((endPoint < maxY) and 
                ("X" not in partY[startPoint[1]][startPoint[0]:endPoint+1])) else startPoint[0]
        else:
            endPoint = startPoint[0] - int(route[1])
            startPoint[0] = endPoint if ((endPoint > -1) and 
                ("X" not in partY[startPoint[1]][(endPoint if endPoint > -1 else 0):startPoint[0]+1])) else startPoint[0]
            
    return startPoint
```
</details>  


## 개인정보 수집 유효기간

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/150370
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(today, terms, privacies):
    answer = []
    months = {i.split(" ")[0]: int(i.split(" ")[1]) * 28 for i in terms}
    todayArr = today.split(".")
    todayDays = int(todayArr[0]) * 12 * 28 + int(todayArr[1]) * 28 + int(todayArr[2])
    for idx, i in enumerate(privacies):
        iArr = i.split(" ")
        destructionArr = iArr[0].split(".")
        destruction = int(destructionArr[0]) * 12 * 28 + int(destructionArr[1]) * 28 + int(destructionArr[2])
        if destruction + months[iArr[1]] <= todayDays:
            answer.append(idx+1)
    return answer
```
</details>


## 신규 아이디 추천

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/72410
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
import re

def solution(new_id):
    answer = re.sub('\\.\\.+','.',''.join(re.findall('[a-z0-9\\.\\-\\_]',new_id.lower())))
    answer = re.sub('\\.$','',re.sub('^\\.','',answer))
    answer = 'a' if len(answer) == 0 else answer
    answer = re.sub('\\.$','',answer[:15])
    while len(answer) < 3:
        answer += answer[-1]
    return answer
```
</details>


## 둘만의 암호

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/155652
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(s, skip, index):
    skips = [ord(i) for i in skip]
    asciis = [i for i in range(97,123) if i not in skips]
    answer = ''.join([chr(asciis[(asciis.index(ord(i))+index)%len(asciis)]) for i in s])
    return answer
```
</details>
