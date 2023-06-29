# Lv1


## 평균 일일 대여 요금 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/151136
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT round(avg(DAILY_FEE),0) as AVERAGE_FEE FROM
CAR_RENTAL_COMPANY_CAR
where CAR_TYPE = "SUV"
group by CAR_TYPE;
```
</details>


## 조건에 부합하는 중고거래 댓글 조회하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/164673
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
ugb.TITLE, ugb.BOARD_ID, ugr.REPLY_ID, ugr.WRITER_ID, ugr.CONTENTS,
DATE_FORMAT(ugr.CREATED_DATE, "%Y-%m-%d") as CREATED_DATE
from USED_GOODS_BOARD as ugb
inner join USED_GOODS_REPLY as ugr
on ugb.BOARD_ID = ugr.BOARD_ID
where ugb.CREATED_DATE >= "2022-10-01" and ugb.CREATED_DATE < "2022-11-01"
order by ugr.CREATED_DATE, ugb.TITLE;
```
</details>


## 최댓값 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/59415
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT max(datetime) from ANIMAL_INS;
```
</details>


## 특정 옵션이 포함된 자동차 리스트 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/157343
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
CAR_ID,
CAR_TYPE,
DAILY_FEE,
OPTIONS
from CAR_RENTAL_COMPANY_CAR
WHERE OPTIONS like '%네비게이션%'
ORDER BY CAR_ID DESC;
```
</details>


## 자동차 대여 기록에서 장기/단기 대여 구분하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/151138
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT 
HISTORY_ID,
CAR_ID,
DATE_FORMAT(START_DATE,'%Y-%m-%d') AS START_DATE,
DATE_FORMAT(END_DATE,'%Y-%m-%d') AS END_DATE,
CASE
    WHEN TIMESTAMPDIFF(DAY,START_DATE,END_DATE)<29 THEN '단기 대여' 
    ELSE '장기 대여'
END AS RENT_TYPE
FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
WHERE DATE_FORMAT(START_DATE,"%Y%m") = 202209
ORDER BY HISTORY_ID DESC;
```
</details>