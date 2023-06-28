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
