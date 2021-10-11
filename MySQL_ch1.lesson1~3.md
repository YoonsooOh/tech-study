# Ch0. 관계형 데이터베이스란?
- mySQL: RDBMS(Relational Database Management System)
- 데이터베이스: 한 곳에 저장된 정보들을 원하는 어떤 곳에서든 사용할 수 있는 것, 특정 소프트웨어나 프로그램에 종속되지 않고 독립된 정보의 집합, 저장소
---
# Ch1-Lesson1. SELECT 전반 기능 
- WHERE: 조건을 나타냄
- mySQL의 구문은 줄바꿈, 대소문자 상관없이 표현 가능 e.g) SELECT, FROM, WHERE 등
- ORDER BY: 정렬 순서 (기본은 오름차순)
  - 기준을 두 가지로 정할 수 있음
- LIMIT: 원하는 갯수만 가져오기
  - LIMIT 10, 10; (페이징에 사용됨, 첫 10은 앞의 10개를 건너뛴다는 의미) 
- AS: 원하는 column명으로 가져오기

## 정리
1. 테이블의 모든 내용 보기
```
SELECT * FROM Customers;
```
2. 원하는 column(열)만 골라서 보기
```
SELECT CustomerName, ContactName, Country
FROM Customers;
```
2-1. 테이블의 컬럼이 아닌 값도 선택할 수 있음
```
SELECT
  CustomerName, 1, 'Hello', NULL
FROM Customers;
```
3. 원하는 조건의 row(행)만 걸러서 보기
```
SELECT * FROM OrderDetails 
WHERE Quantity < 5;
```
4. 원하는 순서로 데이터 가져오기
```
SELECT * FROM OrderDetails
ORDER BY ProductID ASC, Quantity DESC;
```
5. 원하는 만큼만 데이터 가져오기
- LIMIT {가져올 갯수} 또는 LIMIT {건너뛸 갯수}, {가져올 갯수}
```
SELECT * FROM Customers
LIMIT 30, 10;
```
6. 원하는 별명(alias)으로 데이터 가져오기
```
SELECT
  CustomerId AS '아이디',
  CustomerName AS '고객명',
  Address AS '주소'
FROM Customers;
```
> 참고 [URL](https://www.yalco.kr/@sql/1-1/)

---
# Ch1-Lesson2. 각종 연산자들
1) 문자열에 사칙연산을 가하면 0으로 인식
- 결과값: 3
```
SELECT 'ABC' + 3;
```
- 결과값: 7
```
SELECT '1' + '002' * 3; //숫자로 구성된 문자열은 숫자로 자동인식
```
2) TRUE는 1, FALSE는 0으로 저장
3) !=, <> 양쪽 값이 다름을 의미
4) 기본 사칙연산자는 대소문자 구분을 하지 않음
5) like 연산자
  - IN (...)	괄호 안의 값들 가운데 있음
  - NOT IN (...)	괄호 안의 값들 가운데 없음
  - LIKE '... % ...'	0~N개 문자를 가진 패턴
  - LIKE '... _ ...'	_ 갯수만큼의 문자를 가진 패턴
---
  # Ch1-Lesson3. 숫자와 문자열을 다루는 함수들
1) 그룹 함수(집계 함수)
  - MAX	가장 큰 값
  - MIN	가장 작은 값
  - COUNT	갯수 (NULL값 제외)
  - SUM	총합
  - AVG	평균 값
2) CONCAT: 괄호 안의 내용 이어붙여서 string을 만듦
  - CONCAT_WS: 맨앞에 있는 것을 나머지 것들 사이사이에 넣어서 하나의 string을 만듦
```
SELECT CONCAT('HELLO', ' ', 'THIS IS', 2021)
//결과값: HELLO THIS IS 2021
//숫자도 문자로 변환
```
3) 
 - SUBSTR, SUBSTRING	주어진 값에 따라 문자열 자름
 - LEFT	왼쪽부터 N글자
 - RIGHT 오른쪽부터 N글자
```
SELECT SUBSTR('ABCDEFG', 3)
//결과값: CDEFG(앞에서부터 3번째)
SELECT SUBSTR('ABCDEFG', 3, 2)
//결과값: CD (앞에서부터 3번째부터 2개)
SELECT SUBSTR('ABCDEFG', -4)
//결과값: DEFG(뒤에서부터 4번째)
SELECT SUBSTR('ABCDEFG', -4, 2)
//결과값: DE(뒤부터 4번째 2개)
```
4) 
 - LENGTH	문자열의 바이트 길이
 - CHAR_LENGTH, CHARACTER_LEGNTH	문자열의 문자 길이
>mySQL에서 글자수를 셀 때, **보통 CHARACTER_LEGNTH를 사용**
5) 
- TRIM	양쪽 공백 제거
- LTRIM	왼쪽 공백 제거
- RTRIM	오른쪽 공백 제거
6) 
- LPAD(S, N, P)	S가 N글자가 될 때까지 P를 이어붙임
- RPAD(S, N, P)	S가 N글자가 될 때까지 P를 이어붙임
```
SELECT
  LPAD('ABC', 5, '-'),
  RPAD('ABC', 5, '-');
 //결과값: --ABC / ABC--
```
7) REPLACE(S, A, B)	S중 A를 B로 변경
```
SELECT
  REPLACE('맥도날드에서 맥도날드 햄버거를 먹었다.', '맥도날드', '버거킹');
  //결과값: 버거킹에서 버거킹 햄버거를 먹었다.
```
8) 
```
SELECT
   INSTR('ABCDE', 'ABC'),
   //결과값: 1
   INSTR('ABCDE', 'BCDE'),
   //결과값: 2
   INSTR('ABCDE', 'F');
   //결과값: 0
```
9) CAST(A, T)	A를 T 자료형으로 변환
