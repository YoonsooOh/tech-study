# Ch1-Lesson 4. 시간/날짜 관련 및 기타 함수들
1) **DATE_FORMAT	시간/날짜를 지정한 형식으로 반환**
- 형식	설명
  - %Y	년도 4자리
  - %y	년도 2자리
  - %M	월 영문 
  - %m	월 숫자 
  - %D	일 영문(1st, 2nd, 3rd...)
  - %d, %e	일 숫자 (01 ~ 31)
  - %T	hh:mm:ss 
  - %r	hh:mm:ss AM/PM 
  - %H, %k	시 (~23)
  - %h, %l	시 (~12)
  - %i	분 
  - %S, %s	초 
  - %p	AM/PM
  
```
SELECT REPLACE(
  REPLACE(
    DATE_FORMAT(NOW(), '%Y년 %m월 %d일 %p %h시 %i분 %초'),
    'AM', '오전'
  ),
  'PM', '오후'
)
//결과값이 AM이면 오전을, PM이면 오후를 출력
```

2) 기타 함수들
- IF(조건, T, F)	조건이 참이라면 T, 거짓이면 F 반환
- 보두 복잡한 조건은 CASE문 사용
- e.g 1)
```
SELECT
CASE
  WHEN -1 > 0 THEN '-1은 양수다.'
  WHEN -1 = 0 THEN '-1은 0이다.'
  ELSE '-1은 음수다.'
END;
```
- e.g 2)
```
SELECT
  Price,
  IF (Price > 30, 'Expensive', 'Cheap'),
  CASE
    WHEN Price < 20 THEN '저가'
    WHEN Price BETWEEN 20 AND 30 THEN '일반'
    ELSE '고가'
  END
FROM Products;
```

- IFNULL(A, B)	A가 NULL일 시 B 출력
  ```
  SELECT
  IFNULL('A', 'B'),
  IFNULL(NULL, 'B'); //B는 백업과 같은 것으로 볼 수 있음
  //어떤 column을 선택했는데, 그 column의 값이 없을 때 대신에 B를 넣어줌
  ```
---
# Ch1-Lesson 5. 조건에 따라 그룹으로 묶기
1. GROUP BY - 조건에 따라 집계된 값을 가져옴
```
SELECT Country FROM Customers
GROUP BY Country;
//어떤 테이블의 특정 행을 그 안에 겹치지 않는 모든 값을 골라서 뽑아낼 수 있음
//결과값: Austria, Belgium, ...등
```
1-2. 여러 컬럼을 기준으로 그룹화할 수 있음
```
SELECT 
  Country, City,
  CONCAT_WS(', ', City, Country)
FROM Customers
GROUP BY Country, City;
```

WHERE는 그룹하기 전 데이터, HAVING은 그룹 후 집계에 사용됨
```
WHERE
GROUP BY 
HAVING
```

2. DISTINCT - 중복된 값을 제거

- 기본적으로는 정렬되지 않음
- GROUP BY와 달리 집계함수가 사용되지 않음 
  - ORDER BY를 붙여서 수동으로 정렬할 수 있음