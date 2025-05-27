## PART 4. TCL (Transaction Control Language, 트랜잭션 제어어)

### ✅ 트랜잭션이란?

: DB의 논리적 연산 단위, 하나 이상의 SQL 문을 포함한다. </br> 
밀접히 관련되어 분리될 수 없는 1개 이상의 DB 조작을 하나의 트랜잭션으로 본다.

🔹 **트랜잭션의 특성 ACID**

- 원자성(Atomicity): 전부 실행되거나 전혀 실행되지 않는다.(All or Nothing)
- 일관성(Consistency): 트랜잭션으로 인한 DB 상태의 모순이 없다.
- 고립성(Isolation):
    - 부분적인 실행 결과에 다른 트랜잭션이 접근할 수 없다.
    - LOCKING으로 고립성을 보장한다.
- 영속성(Durability): 트랜잭션의 결과는 영구적으로 저장된다.

🔹 **TCL**

: 데이터 무결성 보장을 목적으로 한다. </br>
영구 변경 전 확인과, 연관 작업을 동시에 처리가 가능하다.

- Oracle은 SQL 문장을 실행하면 트랜잭션이 시작되고 TCL을 실행하면 트랜잭션이 종료된다.
- DDL을 실행하면 자동 커밋 (DML 이후 커밋 없이 DDL을 실행해도 자동 커밋)
- DB를 정상적으로 종료하면 자동 커밋, 애플리케이션 등의 이상으로 DB 접속이 단절되면 자동 롤백

🔹 **COMMIT**

: 데이터를 DB에 영구적으로 반영하는 명령어, 커밋 시 트랜잭션이 완료되어 LOCKING이 해제된다. SQL Server은 기본적으로 자동 커밋한다.

- **COMMIT 전**
    - 데이터 변경이 메모리 버퍼에만 영향을 받았기 때문에 복구가 가능하다. </br>
      (NOLOGGING 옵션 사용 시 버퍼 캐시의 기록을 생략하여 입력 성능이 향상된다.)
    - 사용자는 SELECT절로 결과를 확인할 수 있으나 다른 사용자는 현재 결과를 볼 수 없다.
    - 변경된 행에 LOCKING이 설정되어 다른 사용자가 변경할 수 없다. </br>
      (LOCKING이 안 걸린 상태일 때 여러 사용자가 데이터를 변경하면 상관이 없다.)
- **COMMIT 후**
    - 변경 사항이 DB에 반영되고 이전 데이터는 복구가 불가능하다.
    - 모든 사용자가 결과를 볼 수 있다.
    - LOCKING이 해제되어 다른 사용자가 행을 조작할 수 있다.

🔹 ROLLBACK

- 트랜잭션 시작 이전의 상태로 되돌리는 명령어이다.
- COMMIT 이전 상태로 돌려준다.
- ROLLBACK 시 LOCKING이 해제된다.
- SQL Server에서는 ‘BEGIN TRAN’으로 명시해야 가능하다.

🔹 SAVEPOINT

- 트랜잭션 일부만 롤백 할 수 있도록 중간상태를 저장하는 명령어이다.
- ‘ROLLBACK TO 저장점명’ 시 해당 저장점 상태로 돌려준다.
- 동일한 저장점명이 있으면 나중 저장점이 유효하다.
```sql
// Oracle
SAVEPOINT SVPT1;
ROLLBACK TO SVPT1;
// SQL Server
SAVE TRANSACTION SVPT1;
ROLLBACK TRANSACTION SVPT1;
// 공통
COMMIT;
```