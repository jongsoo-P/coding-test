# Lv0

## 특이한 정렬

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120880
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(numlist, n):
    answer = sorted(numlist, key = lambda x: (abs(x-n),-x))
    return answer
```
</details>


## 다항식 더하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120863
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(polynomial):
    polyList = polynomial.split(" + ")
    xList = list(map(lambda x:int(x[:-1]) if x[:-1]!="" else 1,filter(lambda x:x[-1]=="x",polyList)))
    numList = list(filter(lambda x:x[-1]!="x",polyList))

    numSum = str(sum(map(lambda x:int(x),numList)))
    if len(xList) == 0:
        return numSum
    xNum = str(sum(xList) if sum(xList)>1 else '')
    if len(numList)!=0:
        return xNum+"x"+ " + " + numSum
    else:
        return xNum+"x"
```
</details>


## OX퀴즈

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120907
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def check(quiz):
    ans = 0
    quizList = quiz.split(" ")
    if quizList[1] == "+":
        return "O" if int(quizList[0])+int(quizList[2]) == int(quizList[4]) else "X"
    else:
        return "O" if int(quizList[0])-int(quizList[2]) == int(quizList[4]) else "X"


def solution(quiz):
    answer = list(map(check,quiz))
    return answer
```
</details>


## 중복된 숫자 개수

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120583
-   JavaScript
-   Python3

<details>
<summary>접기/펼치기</summary>

-   JavaScript
```javascript
function solution(array, n) {
    var answer = array.filter(x=> x==n).length;
    return answer;
}
```

-   Python3
```py
def solution(array, n):
    answer = array.count(n)
    return answer
```
</details>


## 문자열 밀기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120921
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
from collections import deque

def solution(A, B):
    A = deque(A)
    loopLen = len(A)
    loopCnt = 0
    while loopCnt < loopLen:
        if B == "".join(A):
            return loopCnt
        A.rotate(1)
        loopCnt += 1
    return -1
```
</details>


## 겹치는 선분의 길이

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120876
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(lines):
    totalLine = [0 for i in range(0,201)]
    for lineLen in lines:
        i = lineLen[0]
        while i <lineLen[1]:
            if totalLine[i+100] == 0:
                totalLine[i+100] = 1
            else:
                totalLine[i+100] = 2
            i += 1
    return len(list(filter(lambda x:True if x==2 else False,totalLine)))
```
</details>


## 연속된 수의 합

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120923
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
import math
def solution(num, total):
    answer = []
    half = num/2
    if num%2 == 0:
        answer = [i for i in range(int(math.floor(total/num)-half+1),int(math.ceil(total/num)+half))]
    else:
        answer = [i for i in range(math.floor(total/num)-math.floor(half),math.ceil(total/num)+math.floor(half)+1)]
    return answer
```
</details>


## 양꼬치

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120830
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(n, k):
    answer = n*12000+(k-int(n/10))*2000
    return answer
```
</details>


## 다음에 올 숫자

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120924
-   Python3

<details>
<summary>접기/펼치기</summary>

```py
def solution(common):
    answer = int(common[len(common)-1]*(common[1]/common[0])) if sum(common[0:3])/3 != common[1] else common[len(common)-1]+(common[1]-common[0])
    return answer
```
</details>
