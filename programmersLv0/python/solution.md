# Lv0

## 특이한 정렬

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120880
-   Python3

```py
def solution(numlist, n):
    answer = sorted(numlist, key = lambda x: (abs(x-n),-x))
    return answer
```

## 다항식 더하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120863
-   Python3

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

## OX퀴즈

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120907
-   Python3

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

## 중복된 숫자 개수

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120583
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

## 문자열 밀기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120921
-   Python3

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
