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


## 가격대 별 상품 개수 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131530
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    TRUNCATE(PRICE,-4) AS PRICE_GROUP,
    count(PRODUCT_ID) AS PRODUCTS
FROM PRODUCT
GROUP BY TRUNCATE(PRICE,-4)
ORDER BY PRICE_GROUP;
```
</details>


## 상품 별 오프라인 매출 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131533
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    PRODUCT_CODE,
    SUM(SALES_AMOUNT)*PRICE AS SALES
FROM PRODUCT P
    INNER JOIN OFFLINE_SALE OS ON P.PRODUCT_ID = OS.PRODUCT_ID
GROUP BY PRODUCT_CODE
ORDER BY SALES DESC, PRODUCT_CODE;
```
</details>


## 재구매가 일어난 상품과 회원 리스트 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/131536
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    USER_ID,
    PRODUCT_ID
FROM ONLINE_SALE
GROUP BY USER_ID, PRODUCT_ID
HAVING COUNT(ONLINE_SALE_ID) > 1
ORDER BY USER_ID, PRODUCT_ID DESC;
```
</details>
 

## 진료과별 총 예약 횟수 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/132202
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    MCDP_CD AS '진료과코드',
    COUNT(APNT_NO) AS '5월예약건수'
FROM APPOINTMENT
WHERE DATE_FORMAT(APNT_YMD,'%Y%m') = '202205'
GROUP BY MCDP_CD
ORDER BY COUNT(APNT_NO), MCDP_CD;
```
</details>


## 성분으로 구분한 아이스크림 총 주문량

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/133026
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    INGREDIENT_TYPE,
    SUM(TOTAL_ORDER) AS TOTAL_ORDER
FROM FIRST_HALF FH
LEFT JOIN ICECREAM_INFO II ON FH.FLAVOR = II.FLAVOR
GROUP BY INGREDIENT_TYPE
ORDER BY TOTAL_ORDER;
```
</details>


## 조건에 맞는 도서와 저자 리스트 출력하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/144854
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    B.BOOK_ID,
    A.AUTHOR_NAME,
    DATE_FORMAT(B.PUBLISHED_DATE,'%Y-%m-%d') AS PUBLISHED_DATE
FROM BOOK B
LEFT JOIN AUTHOR A ON B.AUTHOR_ID = A.AUTHOR_ID
WHERE B.CATEGORY = '경제'
ORDER BY PUBLISHED_DATE;
```
</details>


## 자동차 종류 별 특정 옵션이 포함된 자동차 수 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/151137
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    CAR_TYPE,
    COUNT(CAR_ID) AS CARS
FROM CAR_RENTAL_COMPANY_CAR
WHERE OPTIONS LIKE '%통풍시트%'
    OR OPTIONS LIKE '%열선시트%'
    OR OPTIONS LIKE '%가죽시트%'
GROUP BY CAR_TYPE
ORDER BY CAR_TYPE;
```
</details>


## 자동차 평균 대여 기간 구하기

-   링크 : https://school.programmers.co.kr/learn/courses/30/lessons/157342
-   MySQL

<details>
<summary>접기/펼치기</summary>

```sql
SELECT
    CAR_ID,
    ROUND(AVG((TIMESTAMPDIFF(DAY, START_DATE, END_DATE)+1)),1) AS AVERAGE_DURATION
FROM CAR_RENTAL_COMPANY_RENTAL_HISTORY
GROUP BY CAR_ID
HAVING AVERAGE_DURATION >= 7
ORDER BY AVERAGE_DURATION DESC, CAR_ID DESC;
```
</details>
