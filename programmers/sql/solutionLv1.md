# Lv1


## 평균 일일 대여 요금 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/151136
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    round(avg(DAILY_FEE),0) as AVERAGE_FEE FROM
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


## 가장 비싼 상품 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131697
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT MAX(PRICE) AS MAX_PRICE FROM PRODUCT;
```
</details>


## 조건에 맞는 회원수 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131535
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT COUNT(USER_ID) AS USERS FROM USER_INFO WHERE DATE_FORMAT(JOINED,'%Y') = 2021 AND AGE BETWEEN 20 and 29;
```
</details>


## 나이 정보가 없는 회원 수 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131528
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT COUNT(USER_ID) AS USERS FROM USER_INFO WHERE AGE IS NULL;
```
</details>


## 경기도에 위치한 식품창고 목록 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131114
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    WAREHOUSE_ID,
    WAREHOUSE_NAME,
    ADDRESS,
    COALESCE(FREEZER_YN,'N') AS FREEZER_YN
FROM FOOD_WAREHOUSE
WHERE SUBSTRING(ADDRESS,1,3) = '경기도';
```
</details>


## 경기도에 위치한 식품창고 목록 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131112
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    FACTORY_ID,
    FACTORY_NAME,
    ADDRESS
FROM FOOD_FACTORY
WHERE SUBSTRING(ADDRESS,1,3) = '강원도'
ORDER BY FACTORY_ID;
```
</details>


## 12세 이하인 여자 환자 목록 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/132201
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    PT_NAME,
    PT_NO,
    GEND_CD,
    AGE,
    COALESCE(TLNO,'NONE') AS TLNO
FROM PATIENT
WHERE GEND_CD = 'W'
    AND AGE < 13
ORDER BY AGE DESC, PT_NAME;
```
</details>


## 흉부외과 또는 일반외과 의사 목록 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/132203
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    DR_NAME,
    DR_ID,
    MCDP_CD,
    DATE_FORMAT(HIRE_YMD,'%Y-%m-%d') AS DATE_FORMAT
FROM DOCTOR
WHERE MCDP_CD IN ('CS','GS')
ORDER BY HIRE_YMD DESC, DR_NAME;
```
</details>


## 인기있는 아이스크림

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/133024
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT FLAVOR FROM FIRST_HALF ORDER BY TOTAL_ORDER DESC,SHIPMENT_ID;
```
</details>


## 과일로 만든 아이스크림 고르기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/133025
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    FH.FLAVOR
FROM FIRST_HALF FH
    JOIN ICECREAM_INFO I ON FH.FLAVOR = I.FLAVOR
WHERE FH.TOTAL_ORDER > 3000 AND I.INGREDIENT_TYPE = 'fruit_based'
ORDER BY FH.TOTAL_ORDER DESC;
```
</details>


## 조건에 맞는 도서 리스트 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/144853
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    BOOK_ID,
    DATE_FORMAT(PUBLISHED_DATE,'%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK
WHERE DATE_FORMAT(PUBLISHED_DATE,'%Y') = 2021
    AND CATEGORY = '인문'
ORDER BY PUBLISHED_DATE;
```
</details>
