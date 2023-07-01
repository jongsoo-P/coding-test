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
