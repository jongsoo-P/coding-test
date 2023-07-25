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


## 덧칠하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/161989
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(n, m, section):
    answer = 0
    nextPaint = 0
    for i in section:
        if i < nextPaint:
            continue
        answer += 1
        nextPaint = i + m
    return answer
```
</details>


## 성격 유형 검사하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/118666
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(survey, choices):
    points = {"R": 0, "T": 0, "C": 0, "F": 0, "J": 0, "M": 0, "A": 0, "N": 0}
    for idx,surv in enumerate(survey):
        point= choices[idx] - 4
        if point < 0:
            points[surv[0]] += abs(point)
        else:
            points[surv[1]] += point
    answer = ''
    answer += "T" if points["R"] < points["T"] else "R"
    answer += "F" if points["C"] < points["F"] else "C"
    answer += "M" if points["J"] < points["M"] else "J"
    answer += "N" if points["A"] < points["N"] else "A"
    return answer
```
</details>


## 카드 뭉치

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/159994
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(cards1, cards2, goal):
    i1=0
    i2=0
    for word in goal:
        if i1 < len(cards1) and word == cards1[i1]:
            i1 += 1
        elif i2 < len(cards2) and word == cards2[i2]:
            i2 += 1
        else:
            return "No"
    return "Yes"
```
</details>


## 크기가 작은 부분문자열

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/147355
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(t, p):
    answer = 0
    lenP = len(p)
    lenT = len(t)
    intP = int(''.join(p))
    answer = [i for i in range(0,lenT-lenP+1)
            if int(''.join(t[i:i+lenP])) <= intP]
    return len(answer)
```
</details>


## 가장 가까운 같은 글자

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/142086
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(s):
    answer = []
    dictChar = {}
    for idx, i in enumerate(s):
        if i not in dictChar:
            answer.append(-1)
        else:
            answer.append(idx - dictChar[i])
        dictChar[i] = idx
    return answer
```
</details>


## 문자열 나누기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/140108
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(s):
    answer = 0
    lenS = len(s)
    idx = 0
    while idx < lenS:
        tempIdx = idx
        char = s[idx]
        count = 0
        for i in s[idx:]:
            if i == char:
                count += 1
            else:
                count -= 1
            tempIdx += 1
            if count == 0:
                break
        idx = tempIdx
        answer += 1
    return answer
```
</details>


## 명예의 전당 (1)

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/138477
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(k, score):
    scores = []
    answer = []
    for idx,s in enumerate(score):
        scores.append(s)
        scores.sort(reverse=True)
        if idx < k:
            answer.append(scores[idx])
        else:
            answer.append(scores[k-1])
            scores = scores[:k]
    return answer
```
</details>


## 과일 장수

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/135808
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(k, m, score):
    answer = 0
    score.sort(reverse=True)
    for i in range(1,len(score)//m+1):
        answer += score[i*m-1]*m
    return answer
```
</details>


## 푸드 파이트 대회

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/134240
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(food):
    answer = '0'
    for i in range(len(food)-1,0,-1):
        temp = ''.join(map(str,[i for j in range(food[i]//2)]))
        answer = temp + answer + temp
    return answer
```
</details>


## 햄버거 만들기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/133502
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(ingredient):
    if len(ingredient) < 4:
        return 0
    stackList = [ingredient[i] for i in range(3)]
    answer = 0
    for i in ingredient[3:]:
        stackList.append(i)
        stackSize = len(stackList)-1
        if stackSize < 3:
            continue
        if (stackList[stackSize] == 1 and
            stackList[stackSize-1] == 3 and
            stackList[stackSize-2] == 2 and
            stackList[stackSize-3] == 1):
            answer += 1
            stackList.pop()
            stackList.pop()
            stackList.pop()
            stackList.pop()
    return answer
```
</details>


## 옹알이 (2)

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/133499
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
import re
def solution(babbling):
    answer = 0
    for babble in babbling:
        if re.match("^(aya|ye|woo|ma)*$",babble) and re.match(".*(ayaaya|yeye|woowoo|mama).*",babble) == None:
            answer += 1
    return answer
```
</details>


## 콜라 문제

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/132267
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(a, b, n):
    answer = 0
    while n >= a:
        newN = (n // a) * b
        n = newN + n % a
        answer += newN
    return answer
```
</details>


## 숫자 짝꿍

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131128
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(X, Y):
    answer = []
    for i in range(9,-1,-1):
        countX = X.count(str(i))
        countY = Y.count(str(i))
        countI = countX if countX < countY else countY
        answer = answer + [str(i) for j in range(countI)]
    if len(answer) == 0:
        return "-1"
    result = ''.join(answer)
    if re.match(r"^0*$",result) != None:
        return "0"
    return result
```
</details>


## 나머지가 1이 되는 수 찾기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/87389
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(n):
    answer = n - 1
    for i in range(2,int(answer**(1/2))+1):
        if answer % i == 0:
            return i
    return answer
```
</details>


## 최소직사각형

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/86491
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(sizes):
    width = []
    height = []
    for i in sizes:
        if i[0] > i[1]:
            width.append(i[0])
            height.append(i[1])
        else:
            width.append(i[1])
            height.append(i[0])
    maxWidth = max(width)
    maxHeight = max(height)
    answer = maxHeight * maxWidth
    return answer
```
</details>


## 달리기 경주

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/178871
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(players, callings):
    rankingNumber = {}
    rankingName = {}
    for idx,name in enumerate(players):
        rankingNumber[idx+1]=name
        rankingName[name]=idx + 1
    tempName = ""
    for name in callings:
        changeRanking = rankingName[name] - 1
        changeName = rankingNumber[changeRanking]
        rankingName[name] = changeRanking 
        rankingName[changeName] = changeRanking + 1

        rankingNumber[changeRanking] = name
        rankingNumber[changeRanking+1] = changeName
    answer = [rankingNumber[i] for i in range(1, len(players)+1)]
    return answer
```
</details>


## 없는 숫자 더하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/86051
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(numbers):
    answer = 45 - sum(numbers)
    return answer
```
</details>


## 부족한 금액 계산하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/82612
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(price, money, count):
    answer = count * (2*price +(count-1)*price)/2
    return answer - money if answer > money else 0
```
</details>


## 숫자 문자열과 영단어

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/81301
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(s):
    text = {
        0:'zero',
        1:'one',
        2:'two',
        3:'three',
        4:'four',
        5:'five',
        6:'six',
        7:'seven',
        8:'eight',
        9:'nine'
    }
    for i in text:
        s = s.replace(text[i],str(i))
    answer = int(s)
    return answer

print(solution("2three45sixseven"))
```
</details>


## 로또의 최고 순위와 최저 순위

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/77484
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(lottos, win_nums):
    answer = []
    zero = 0
    win_num = 0
    for i in lottos:
        if i==0:
            zero += 1
        elif i in win_nums:
            win_num += 1
    max_win = zero + win_num
    rank = [6,6,5,4,3,2,1]
    answer.append(rank[max_win])
    answer.append(rank[win_num])
    return answer
```
</details>
