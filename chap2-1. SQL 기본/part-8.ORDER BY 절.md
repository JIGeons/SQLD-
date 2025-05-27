## PART 8. ORDER BY 절

### ✅ ORDER BY

: 특정 컬럼을 기준으로 정렬, 기본 정렬 기준은 오름차순

🔹 **ORDER BY 특징**

1. SQL 문장으로 조회된 데이터들을 다양한 목적에 맞게 특정한 컬럼을 기준으로 정렬하여 출력하는데 사용한다.
2. ORDER BY 절에 컬럼명 대신 ALIAS 명이나 컬럼 순서를 나타내는 정수도 사용 가능하다.
3. DEFAULT 값으로 오름차순(ASC)이 적용되며 DESC 옵션을 통해 내림차순으로 정렬이 가능하다.
4. SQL 문장의 제일 마지막에 위치한다.
5. SELECT 절에서 정의하지 않은 컬럼도 사용이 가능하다.
6. GROUP BY 절이 있으면 GROUP BY 대상이 아니다.

→ Oracle에서는 NULL을 가장 가장 큰 값으로 취급하며, </br>
SQL Server에서는 NULL을 가장 작은 값으로 취급한다.

### ✅ SELECT문 실행 순서

: 테이블에서 출력 대상이 아닌 것은 제거하고 그룹핑해서 그룹핑된 값이 조건에 맞는 데이터를 계산 및 출력하고 정렬한다.

    FROM → WHERE → GROUP BY → HAVING → SELECT → ORDER BY