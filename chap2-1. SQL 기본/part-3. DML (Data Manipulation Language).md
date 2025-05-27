## PART 3. DML (Data Manipulation Language, 데이터 조작어)

### ✅ INSERT: 데이터 입력

```sql
// 단일 행 데이터 입력
INSERT INTO 테이블명 (칼럼명...) VALUES (필드값...);
// Oracle - 여러 행 데이터 입력
INSERT ALL
INTO 테이블명 (컬럼명...) VALUES (필드값...)
INTO 테이블명 (컬럼명...) VALUES (필드값...)
// SQL Server - 여러 행 데이터 입력
INSERT INTO 테이블명 (컬럼명...)
VALUES
	(필드값...),
	(필드값...);
```

### ✅ UPDATE: 데이터 수정

```sql
UPDATE 테이블명 
SET 컬럼명 = 필드값, ...
[WHERE 조건];
```

### ✅ DELETE: 데이터 삭제

```sql
DELETE FROM 테이블명 [WHERE 조건절];
```

- DELETE로 데이터를 삭제해도 테이블 용량은 초기화되지 않는다.
  (↔ TRUNCATE로 삭제하면 초기화된다.)
- ↔ DROP은 객체 삭제 명령어이다.
- 조건절이 없는 경우 테이블의 모든 행을 삭제한다.

### ✅ SELECT

**🔹 컬럼별 데이터 선택**

```sql
SELECT 컬럼명 FROM 테이블명;
```

🔹 **데이터 중복 없이 선택**

```sql
SELECT DISTINCT 컬럼명 FROM 테이블명;
```

🔹 **전체 컬럼의 데이터 선택**

```sql
SELECT * FROM 테이블명;
```

✔️ **엘리어스(Alias)**

- SELECT 컬럼명 AS “별명” : 출력되는 컬럼명 설정
- FROM 테이블명 별명 : 쿼리 내에서 사용할 테이블명 설정, 컬럼명이 중복될 경우 SELECT 절에서 엘리어스는 필수이다.

**🔹 와일드카드**

: SQL에서 주로 `LIKE` 연산자와 함께 사용되며, 두 가지 주요 와일드카드가 있다.

1. 퍼센트 기호 (`%`)
    - 의미: 0개 이상의 모든 문자(문자열)를 나타낸다.
    - 사용 예시:
        - `‘김%’`: ‘김’으로 시작하는 모든 문자열 (예: 김철수, 김영희, 김치)
        - `‘%스%’`: ‘스’를 포함하는 모든 문자열 (예: 버스, 키보드, 스프링)
        - `‘%동’`: ‘동’으로 끝나는 모든 문자열 (예: 홍길동, 서초동)
2. 언더스코어 (`_`)
    - 의미: 정확히 하나의 문자를 나타낸다. (빈칸 포함)
    - 사용 예시:
        - `‘김_수’`: ‘김’으로 시작하고 ‘수’로 끝나는 세 글자 문자열 (예: 김지수, 김민수, 김은수)
        - `‘A__C’`: ‘A’로 시작하고 ‘C’로 끝나는 네 글자 문자열 (예: ABCD, A12C)

```sql
// 사원 테이블에서 이름이 김씨인 데이터 전부 검색
SELECT *
FROM employees
WHERE name LIKE '김%';
```

🔹 **합성 연산자**

1. **문자열 연결(Concatenation) 연산자**

   : 두 개 이상의 문자열(컬럼 값, 리터럴 등)을 하나로 **합치는(연결하는)** 연산자를 의미한다.
   이는 SQL의 `SELECT` 문 등에서 결과를 조합할 때 매우 자주 사용된다.

   **Oracle에서 문자열 연결 연산자 :** </br>
   Oracle에서는 `||` (두 개의 수직 막대)를 문자열 연결 연산자로 사용한다.

    ```sql
    // first_name 컬럼의 값, 공백 리터럴, last_name 컬럼의 값을 합성하여 
    // full_name이라는 하나의 컬럼으로 보여준다.
    SELECT first_name || ' ' || last_name AS full_name
    FROM employees;
    ```

   **SQL Server에서 문자열 연결 연산자 :** </br>
   SQL Server에서는 `+` (덧셈 기호)를 문자열 연결 연산자로 사용한다. 또는 `CONCAT` 함수를 사용할 수도 있다.

    ```sql
    SELECT first_name + ' ' + last_name AS full_name
    FROM employees;
    // 또는
    SELECT CONCAT(first_name, ' ', last_name) AS full_name
    FROM employees;
    ```

2. **복합 할당 연산자**

   : SQL 자체보다는 데이터베이스 시스템의 절차적 확장 언어 </br> 
     (예: Oracle의 PL/SQL, SQL Server의 T-SQL)에서 변수의 값을 변경할 때 사용된다. 산술 연산자와 할당 연산자를 결합한 형태이다.

   **예시 (Oracle PL/SQL) :**

    ```sql
    DECLARE
        v_salary NUMBER := 50000;
    BEGIN
        v_salary := v_salary + 1000; -- 일반적인 할당
        DBMS_OUTPUT.PUT_LINE('After direct add: ' || v_salary); -- 51000
    
        v_salary += 500; -- PL/SQL 11gR2부터 지원 (복합 할당)
        DBMS_OUTPUT.PUT_LINE('After compound add: ' || v_salary); -- 51500
    
        v_salary *= 1.1; -- 복합 할당
        DBMS_OUTPUT.PUT_LINE('After compound multiply: ' || v_salary); -- 56650
    END;
    ```

   Oracle PL/SQL 에서는 `$op=` 형태로 `+=`, `-=`. `*=` 등을 지원한다.

   **예시 (SQL Server T-SQL) :**

    ```sql
    DECLARE @salary DECIMAL(10, 2);
    SET @salary = 50000;
    
    SET @salary = @salary + 1000; -- 일반적인 할당
    PRINT 'After direct add: ' + CAST(@salary AS VARCHAR(20)); -- 51000.00
    
    SET @salary += 500; -- 복합 할당
    PRINT 'After compound add: ' + CAST(@salary AS VARCHAR(20)); -- 51500.00
    
    SET @salary *= 1.1; -- 복합 할당
    PRINT 'After compound multiply: ' + CAST(@salary AS VARCHAR(20)); -- 56650.00
    ```

   SQL Server T-SQL 에서도 `+=`, `-=`, `*=` 등의 복합 할당 연산자가 사용된다.


**🔹 DUAL**

: Oracle 데이터베이스에만 존재하는 특수한 더미(dummy) 테이블.
연산 수행을 위해 사용된다.

- **단일 컬럼, 단일 행** : `DUAL` 테이블은 `DUMMY`라는 이름의 `VARCHAR2(1)` 타입 컬럼과 ‘X’라는 값을 가진 단 하나의 행만을 가진다.
- **SYS 소유** : `DUAL` 테이블은 `SYS` 사용자가 소유하지만, 모든 데이터베이스 사용자가 접근할 수 있도록 권한이 부여되어 있다.
- **목적** : SQL 구문상 `FROM` 절이 필수적인 Oracle에서, 특정 데이터를 조회할 필요 없이 함수나 상수, 표현식의 결과만 얻고 싶을 때 임시로 사용되는 플레이스홀더(placeholder) 역할을 한다.