# Lv0

## 특이한 정렬

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120880
-   python

```py
def solution(numlist, n):
    answer = sorted(numlist, key = lambda x: (abs(x-n),-x))
    return answer
```

## 다항식 더하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/120863
-   python

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
