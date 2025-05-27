## PART 9. 조인 (JOIN)

: 두 개 이상의 테이블을 연결 또는 결합하여 데이터를 출력하는 것. </br>
일반적으로 행들은 PK나 FK 값의 연관에 의해 JOIN이 성립된다. </br>
어떤 경우에는 PK, FK 관계가 없어도 논리적인 값들의 연관만으로 JOIN이 성립가능하다.

  → 5가지 테이블을 JOIN 하기 위해서는 최소 4번의 JOIN과정이 필요하다. (N-1)

🔹 **등가 조인(EQUI JOIN)**

: 2개의 테이블 간에 컬럼 값들이 서로 정확하게 일치하는 경우에 사용한다. </br>
대부분 PK, FK의 관계를 기반으로 한다.

```sql
// SELECT 대상 컬럼이 두 테이블 모두에 있는 경우 앨리어스를 지정해야 한다. (양쪽 앨리어스 모두 무관)
SELECT e.name, e.salary, d.department_name, d.location
FROM employees e
JOIN departments d ON e.department_id = d.department_id;
```

🔹 **비등가 조인(NON EQUI JOIN)**

: 두 개의 테이블 간에 컬럼 값들이 서로 정확하게 일치하지 않는 경우에 사용한다. </br>
‘=’ 연산자가 아닌 BETWEEN, >, ≤ 등 연산자를 사용한다.

```sql
SELECT e.name, e.salary, sg.grade_level
FROM employees e
JOIN salary_grades sg ON e.salary BETWEEN sg.min_salary AND sg.max_salary;
```

🔹 **NATURAL JOIN**
: WHERE 절에서 JOIN 조건 추가 불가 </br>
SELECT EMP, DEPT 처럼 OWNER명 사용 불가

🔹 **CROSS JOIN**

: WHERE 절에서 JOIN 조건 추가 가능