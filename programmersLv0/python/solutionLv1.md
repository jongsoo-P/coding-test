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
