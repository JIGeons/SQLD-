## PART 7. 집계 함수(Aggregate Function, GROUP BY, HAVING 절)

: 여러 행들의 그룹이 모여서 그룹당 단 하나의 결과를 돌려주는 함수이다. </br>
GROUP BY절이 없으면 그룹핑 대상이 존재하지 않아 에러 발생한다. </br>
WHERE 절에 사용이 불가능하다. 공집합에서도 연산을 수행한다.

- ALL, DISTINCT : 전체 출력, 중복 제외 출력

- SUM, AVG, MAX, MIN, VARIAN(분산), STDDEV(표준 편차)
  : NULL 제외하고 연산 ( ↔ 숫자 연산은 NULL 출력 )

  - COUNT : 행 수 출력
  - COUNT(*) : NULL 포함
  - COUNT(표현식) : NULL 제외

### ✅ GROUP BY, HAVING 절의 특징

1. GROUP BY 절을 통해 소그룹별 기준을 정한 후, SELECT 절에 집계 함수를 사용한다.
2. 집게 함수의 통계 정보는 NULL 값을 가진 행을 제외하고 수행한다.
3. GROUP BY 절에서는 ALIAS를 사용 불가하다.
4. 집계 함수는 WHERE 절에 올 수 없다.
5. HAVING 절에는 집계 함수를 이용하여 조건을 표시한다.
   (↔ WHERE 절은 SELECT 절에 조건을 걸기 때문에 제외된 데이터가 GROUP BY 대상이 아니다.)
6. HAVING 절은 일반적으로 GROUP BY 절 뒤에 위치한다.