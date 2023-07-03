# Lv2


## 조건에 부합하는 중고거래 상태 조회하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/164672
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT BOARD_ID, WRITER_ID, TITLE, PRICE,
CASE WHEN STATUS = 'SALE' THEN '판매중'
WHEN STATUS = 'RESERVED' THEN '예약중'
WHEN STATUS = 'DONE' THEN '거래완료'
END AS STATUS
FROM USED_GOODS_BOARD
WHERE CREATED_DATE >= '2022-10-05' AND CREATED_DATE <'2022-10-06'
ORDER BY BOARD_ID DESC;
```
</details>


## 루시와 엘라 찾기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/59046
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    ANIMAL_ID,
    NAME,
    SEX_UPON_INTAKE
FROM ANIMAL_INS
WHERE NAME IN ('Lucy', 'Ella', 'Pickle', 'Rogan', 'Sabrina', 'Mitty')
ORDER BY ANIMAL_ID;
```
</details>


## 이름에 el이 들어가는 동물 찾기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/59047
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
   ANIMAL_ID,
   NAME
FROM ANIMAL_INS
WHERE ANIMAL_TYPE = 'Dog'
    and lower(NAME) like '%el%'
ORDER BY NAME;
```
</details>


## 중성화 여부 파악하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/59409
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    ANIMAL_ID
    , NAME
    , CASE WHEN SEX_UPON_INTAKE like 'Intact%' then 'X'
    ELSE 'O' END AS '중성화'
FROM ANIMAL_INS
ORDER BY ANIMAL_ID;
```
</details>


## DATETIME에서 DATE로 형 변환

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/59414
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    ANIMAL_ID,
    NAME,
    DATE_FORMAT(DATETIME, '%Y-%m-%d') AS '날짜'
FROM ANIMAL_INS
ORDER BY ANIMAL_ID;
```
</details>


## 가격이 제일 비싼 식품의 정보 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131115
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT 
*
FROM FOOD_PRODUCT
ORDER BY PRICE DESC
LIMIT 1;
```
</details>


## 3월에 태어난 여성 회원 목록 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131120
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    MEMBER_ID,
    MEMBER_NAME,
    GENDER,
    DATE_FORMAT(DATE_OF_BIRTH,'%Y-%m-%d') AS DATE_OF_BIRTH
FROM MEMBER_PROFILE
WHERE DATE_FORMAT(DATE_OF_BIRTH,'%m') = '03'
    AND GENDER = 'W'
    AND TLNO IS NOT NULL
ORDER BY MEMBER_ID;
```
</details>


## 카테고리 별 상품 개수 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131120
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    LEFT(PRODUCT_CODE,2) AS CATEGORY,
    COUNT(PRODUCT_ID) AS PRODUCTS
FROM PRODUCT
GROUP BY (LEFT(PRODUCT_CODE,2))
ORDER BY CATEGORY;
```
</details>
