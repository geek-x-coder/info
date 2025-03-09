# Oracle/Tibero Flashback feature

데이터베이스를 이용하다보면 실수로 데이터를 삭제하거나, 잘못 업데이트를 하는 경우가 있습니다.
commit을 하기 전이라면 상관이 없습니다.
하지만 commit을 한 이후에 문제를 파악하여 데이터를 복구해야 하는 경우가 생깁니다.
이럴 때 ORACLE의 `TIMESTAMP`를 이용하면 데이터를 복구 할 수 있습니다.
> DB의 설정에 따라서 시간이 오래 지난 데이터는 TIMESTAMP로 복구가 불가능합니다.

#### Oracle/Tibero Flashback Query를 이용한 복구
- AS OF TIMESTAMP 절을 이용하여 삭제된 데이터를 특정 시점의 상태로 복구 할 수 있습니다.

> `Oracle Flashback Technology` is a group of features in Oracle Database that allows you to view past states of database objects or return them to a previous state without using point-in-time media recovery. Here's what you can do with flashback features:
>  1. Flashback Query (AS OF) : Perform queries that return past data using the `AS OF` clause.

단위는 SECOND, MINUTE, HOUR, DAY로 지정해서 사용할 수 있습니다.
SYSTIMESTAMP에서 설정한 시간을 입력하여 데이터를 보여줍니다.

```sql
-- 10초 전 데이터 조회
select * from 테이블 as of timestamp(systimestamp - interval '10' second)
where 컬럼 = 'A'; -- 필요에 따라서 조건문

-- 10분 전 데이터 조회
select * from 테이블 as of timestamp(systimestamp - interval '10' minute)

-- 3시간 전 데이터 조회
select * from 테이블 as of timestamp(systimestamp - interval '3' hour)

-- 1일 전 데이터 조회
select * from 테이블 as of timestamp(systimestamp - interval '1' day)

-- 특정 시간 기준으로 데이터 조회
select * from 테이블 as of timestamp(TO_DATE('20200605000000', 'YYYYMMDDHH24MISS'))
```

> TIMESTAMP 데이터 기준으로 복구, 수정 방법 (예시입니다.)

```sql
-- SELECT INSERT 
INSERT INTO TEMP_TABLE
SELECT * FROM TEMP_TABLE AS OF TIMESTAMP(SYSTIMESTAMP - INTERVAL '10' MINUTE)
WHERE COLUMN_A = 'found';

-- SELECT UPDATE
UPDATE TEMP_TABLE A
SET A.COLUMN_A = (SELECT B.COLUMN_A FROM TEMP_TABLE B AS OF TIMESTAMP(SYSTIMESTAMP - INTERVAL '10' MINUTE WHERE A.COLUMN_B = B.COLUMN_B AND B.COLUMN_B ='found')
WHERE A.COLUMN_B = 'found'
```
