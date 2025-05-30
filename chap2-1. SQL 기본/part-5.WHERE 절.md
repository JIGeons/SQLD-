## PART 5. WHERE 절

### ✅ 연산자 종류

🔹 **비교 연산자** ( =, >, ≥, <, ≤ )

- 비교 대상 데이터 타입에 따라 자동으로 형 변환되는 경우도 있음.

🔹 **부정 비교 연산자**

- ‘NOT 컬럼명 비교연산자’와 동일하다.
- 부등호 ( ≠, ^=, <> ISO 표준 )

🔹 **SQL 연산자 입력값을 비교하는 논리값 출력**

- BETWEEN A AND B: A와 B 사잇값
- IN(리스트): 리스트 내의 값
- LIKE ‘문자열’ : 문자열의 형태와 일치하는 값 (와일드카드를 사용)
- IS NULL : 어떤 상황에서도 NULL은 등호로 판단 불가
- NOT BETWEEN A AND B, NOT IN (리스트), IS NOT NULL

🔹 **논리 연산자** : AND, OR, NOT

🔹 **우선순위**: 부정 연산자 > 비교 연산자 > 논리 연산자

[ ‘()’(괄호) ] → [ NOT ] → [ 비교 연산자 및 SQL 연산자 ] → [ AND ] → [ OR ]

🔹 문자열 비교방법

- CHAR vs CHAR :
    - 첫 서로 다른 문자열 값으로 비교한다. (뒤 순서가 더 큰 값)
    - 길이가 다를 때 공백을 추가하여 길이를 맞춘다. (공백 수만 다르면 같은 값이다.)
- CHAR vs VARCHAR :
    - 첫 서로 다른 문자열 값으로 비교한다.
    - 길이가 다르면 길이가 긴 값이 크다고 판단한다.
    - VARCHAR의 공백도 문자로 판단한다.
    - TRIM 함수로 VARCHAR의 공백을 제거하고 판단할 수 있다.
- CHAR vs 상수 :
    - 상수를 변수 타입으로 바꿔 비교한다.

### ✅ 부분 범위 처리

- ROWNUM(Oracle) :
    - SQL 처리 결과 집합의 각 행에 임시로 부여되는 번호이다.
    - 조건절 내에서 행의 개수를 제한하는 목적으로 사용한다.
- TOP (SQL Server)
    - 출력 행의 수 제한 함수.
    - `TOP(N)`로 N개의 행을 출력하고, 개수 대신 비율로도 제한이 가능하다.
    - ORDER BY절이 없으면 ROWNUM과 TOP의 기능이 같다.

    ```sql
    WHERE ROWNUM = 1;
    SELECT TOP(1) PLAYER_NAME FROM PLAYER;
    ```