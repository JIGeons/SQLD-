## PART 6. 함수

### ✅ 단일 행 함수

- SELECT 절, WHERE 절, ORDER BY 절에 사용 가능하다.
- 각 행에 개별적으로 작용하고, 여러 인자를 입력해도 단 하나의 결과만 출력한다.

🔹 **문자열 함수**: 문자열 입력 시 문자열이나 숫자를 변환한다.

- LOWER, UPPER, LENGTH
- CONCAT : 문자열 결합
- SUBSTR/SUBSTRING : 문자열 부분 추출
- LTRIM, RTRIM, TRIM : 왼쪽 공백 제거, 오른쪽 공백 제거, 양쪽 공백 제거
- ASCII : 아스키 코드값 출력

🔹 **숫자형 함수**

- ABS, SIGN : 절대값, 부호 (1, 0, -1 중 출력)
- MOD : 나머지, 연산자 ‘%’로 대체 가능하다.
- ROUND : 반올림, 올림, 버림 (’함수(E, N)’으로 소수점 이후 N번째 자리까지 출력)
- CEIL/CEILING(n) : 크거나 같은 최소 정수 반환
- FLOOR(n) : 작거나 같은 최대 정수 리턴
- TRUNC : 숫자형 부분 추출

🔹 **날짜형 함수**

- SYSDATE/GETDATE : 현재 날짜와 시각 출력 (년, 월, 일, 시, 분, 초)
- EXTRACT/DATEPART : 날짜에서 데이터 출력
- +- 숫자, +- 숫자 / 24 : 일자 연산, 시간 연산
- NEXT_DAY : 지정된 요일 첫 날짜 출력

🔹 **변환형 함수**: 데이터 타입 변환, 명시적 형 변환 방식

- TO_NUMBER, TO_CHAR, TO_DATE (Oracle): 문자열을 숫자로, 숫자나 날짜를 문자열로, 문자열을 날짜로
- CAST, CONVERT (SQL Server)

🔹 **CASE**

- SIMPLE_CASE_EXPRESSION : CASE 다음에 바로 조건에 사용되는 칼럼이나 표현식을 표시
- SEARCHED_CASE_EXPRESSION : WHEN절에서 EQUI 조건을 포함한 여러 조건을 사용 가능

```sql
SEARCHED_CASE_EXPRESSION
CASE WHEN LOC = 'a' THEN 'b'
SIMPLE_CASE_EXPRESSION
CASE LOC WHEN 'a' THEN 'b'
// 이 두 문장은 같은 의미이다.
```

🔹 **NULL 관련 함수**

- NVL(컬럼, 값): NULL 값 변환
- NVL2(컬럼, 값, 값): NULL이면 앞의 값 아니면 뒤의 값 출력
- NULLIF(값, 값): 같으면 NULL 다른면 첫 값 출력
- COALESCE(값, 값, …): NULL이 아닌 첫 값 출력
- ISNULL(컬럼, 값): NULL이면 값으로 대치 아니면 컬럼 값 출력

### ✅ 데이터 변환

🔹 **명시적 변환**

: 변환형 함수를 이용하여 데이터 타입을 변환한다.

🔹 **암시적 변환**

: DBMS가 자동으로 데이터 타입을 변환한다.

### ✅ 조건문: IF-THEN-ELSE 형태

🔹 **CASE WHEN 조건절1 THEN 출력값 1… ELSE 기본값 END**

: ELSE 생략 시 NULL 출력

- ‘CASE WHEN NULL THEN 출력값 ELSE 기본값’은 조건이 없으므로 모든 행에서 기본값 출력 </br>
  (일반적으로 ‘WHEN 컬럼 IS NULL’로 수정 필요)

🔹 **DECODE (컬럼, 기준값1, 출력값1, …, 기본값)**

: Oracle 함수, 기준값 n이면 출력값 n 출력