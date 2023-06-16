# Lv1


## 같은 숫자는 싫어

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/12906
-   Python3

```py
def solution(arr):
    answer = [arr[0]] + [arr[i] for i in range(1,len(arr)) if arr[i-1]!=arr[i]]
    return answer
```

## 키패드 누르기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/67256
-   Python3

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

## 체육복

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/42862
-   Python3

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

## 내적

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/70128
-   Python3

```py
def solution(a, b):
    answer = sum([i*j for i, j in zip(a,b)])
    return answer
```

## 삼총사

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131705
-   Python3

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

## 추억점수

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/176963
-   Python3

```py
def solution(name, yearning, photo):
    point = {name[i]:yearning[i] for i in range(len(name))}
    answer = [sum([point[j] for j in i if j in point]) for i in photo]
    return answer
```

## 바탕화면 정리

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/161990
-   Python3

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

## 신고 결과 받기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/92334
-   Python3

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

## 대충 만든 자판

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/160586
-   Python3

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
