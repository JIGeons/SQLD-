## PART 2. DDL (Data Definition Language, 데이터 정의어)

### ✅ 데이터 타입 (Oracle / SQL Server)

🔹 **CHAR(s) :**
- 고정 길이 문자열
- 할당된 변수 값의 길이가 s 이하일 때 차이는 공백으로 채워진다.

🔹 **VARCHAR2(s), VARCHAR(s)**
- 가변 길이 문자열
- 할당되는 변수 값의 길이의 최대값이 s이다.
- 문자열은 가능한 최대 길이로 설정

**🔹 NUMBER(s,d)**
- 정수, 실수 등 숫자 정보
- s는 전체 자리 수, d는 소수점 자리 수

→ SQL Server은 NUMBERIC / DECIMAL / FLOAT / REAL 등

**🔹 DATE / DATETIME**

- 날짜형, 데이터 크기 지정이 필요하지 않다.

### ✅ CREATE TABLE

```sql
CREATE TABLE 테이블명 (컬럼명, 데이터타입, 제약조건, ...);
```

🔹 **테이블 및 컬럼 명명 규칙**

- 알파벳 → 숫자→ ‘_’ (언더바) → ‘$’ (달러) → ‘#’(샵) 사용
- 대소문자를 구분하지 않는다.
- 테이블명은 다른 테이블의 이름과 중복되면 안된다.
- 테이블명은 단수형을 권고한다.
- 테이블 내의 컬럼명은 중복될 수 없다.
- 각 컬럼들은 , 로 구분되고 ; 로 끝난다.
- 컬럼 뒤에 데이터 유형은 꼭 지정되어야 한다.
- DATETIME 데이터 유형에는 별도로 크기를 지정할 수 없다.

🔹 **제약조건**

: 데이터 무결성 유지가 목적, 복제 테이블에는 기존 테이블 제약조건 중 NOT NULL만 적용

- **PRIMARY KEY :**
    - 테이블 당 하나의 기본키만 정의 가능하다.
    - 기본키 생성 시 DBMS가 자동으로 인덱스를 생성한다.
    - NULL 값이 불가능 하다.
- **FOREIGN KEY :**
    - 다른 테이블의 기본키를 외래키로 지정한다. 참조 무결성 제약조건

        ```sql
        ALTER TABLE 테이블명 ADD CONSTRAINT 컬럼명 FOREIGN KEY (컬럼명) REFERENCES 테이블명(컬럼명);
        ```

- **UNIQUE KEY :**
    - 행 데이터를 식별하기 위해 생성한다.
    - NULL 값을 허용한다.
- **DEFAULT :**
    - ‘DEFAULT 값’으로 기본값을 설정한다.
- **NOT NULL :**
    - NULL - 아직 정의되지 않은 값 또는 현재 데이터를 입력하지 못하는 값이다.
    - NULL과의 1) 수치연산은 NULL, 2) 비교연산은 FALSE 출력
- **CHECK :**
    - 입력값의 종류 및 범위를 제한한다.

✔️ DESCRIBE 테이블명; → 테이블 구조 확인 (Oracle) sp_help ‘dbo.테이블명’ → (SQL Server)

### ✅ 테이블 구조 변경(ALTER TABLE: 컬럼 추가, 삭제 등) DDL

**🔹 컬럼 추가**

```sql
ALTER TABLE 테이블명 ADD (컬럼명 데이터타입);
```

- 마지막 컬럼으로 추가됨 (컬럼 위치 지정 불가)
- SQL Server - 여러개 테이블 동시수정 불가

**🔹 컬럼 삭제**

```sql
ALTER TABLE 테이블명 DROP COLUMN 컬럼명;
```

- 삭제 후 복구 불가

**🔹 컬럼 설정 변경**

```sql
// Oracle
ALTER TABLE 테이블명 
MODIFY (
    컬럼명1 데이터타입1(크기) [DEFAULT 값] [NULL | NOT NULL],
    컬럼명2 데이터타입2(크기) [DEFAULT 값] [NULL | NOT NULL],
    ...
);
// SQL Server
ALTER TABLE 테이블명 
ALTER COLUMN 컬럼명 데이터타입(크기) [NULL | NOT NULL] [DEFAULT (값)];
```
- NULL만 있거나 행이 없는 경우에만 컬럼의 크기를 축소할 수 있다.
- NULL만 있을 때는 데이터 유형도 변경 가능하다.
- NULL이 없으면 NOT NULL 제약조건 추가 가능하다.
- 기본값 변경 작업 이후 발생하는 데이터에 대해서만 기본값이 변경된다.

**🔹 컬럼명 변경**

```sql
// Oracle
ALTER TABLE 테이블명 RENAME COLUMN 기존컬럼명 TO 새컬럼명;
// SQL Server
EXEC sp_rename '테이블명.기존컬럼명', '새컬럼명', 'COLUMN';
```

- ANSI/ISO 표준에 명시된 기능은 아니다.

**🔹 제약조건 추가**

```sql
ALTER TABLE 테이블명 ADD CONSTRAINT 제약조건;
```

**🔹 제약조건 제거**

```sql
ALTER TABLE 테이블명 DROP CONSTRAINT 제약조건;
```

**🔹 테이블명 변경**

```sql
// Oracle
ALTER TABLE 기존테이블명 RENAME TO 새테이블명
// SQL Server
EXEC sp_rename '기존테이블명', '새테이블명';
```

🔹 **테이블 삭제**

```sql
DROP TABLE 테이블명 [CASCADE CONSTRAINTS] [PURGE];
```

- 테이블의 데이터와 구조 삭제, 복구 불가
- CASCADE CONTRAINTS 옵션으로 관련 테이블의 참조 제약조건도 삭제하여 참조 무결성을 준수할 수 있다. </br>
  (CREATE TABLE에서 ON DELETE CASCADE 옵션으로도 동일 기능을 실현할 수 있다.)

**🔹 테이블 전체 데이터 제거**

```sql
TRUNCATE TABLE 테이블명;
```

- 테이블의 전체 데이터를 삭제 (↔ DROP TABLE은 테이블 자체를 제거한다.)
- 로그를 기록하지 않기 때문에 ROLLBACK 불가하다.
- 저장공간을 재사용한다.

✔️ **Dependent**
: 관계형 데이터베이스에서 Child Table의 FK 데이터 생성시 Parent Table에 PK가 없는 경우,
Child Table 데이터 입력을 허용하지 않는 참조 동작