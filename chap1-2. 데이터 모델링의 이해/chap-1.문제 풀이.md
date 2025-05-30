### SQL 자격 검정 실전 문제 답

| 번호 | 정답      | 번호 | 정답      | 번호 | 정답  | 번호 | 정답      | 번호 | 정답     |
|----|---------|----|---------|----|-----|----|---------|----|--------|
| 1  | 2 ✅     | 2  | 1 ❌ → ③ | 3  | 3 ✅ | 4  | 3 ❌ → ② | 5  | 1 ✅    |
| 6  | 2 ✅     | 7  | 4 ✅     | 8  | 4 ✅ | 9  | 2 ✅     | 10 | 3 ✅    |
| 11 | 1 ✅     | 12 | 1 ✅     | 13 | 1 ✅ | 14 | 속성 ✅    | 15 | 3 ✅    |
| 16 | 1 ❌ → ③ | 17 | 1 ✅     | 18 | 4 ✅ | 19 | 3 ✅     | 20 | 3, 4 ✅ |
| 21 | 2 ✅     | 22 | 2 ✅     | 23 | 3 ✅ | 24 | 4 ✅     | 25 | 4 ✅    |
| 26 | 3 ❌ → ④ | 27 | 2 ✅     | 28 | 2 ✅ | 29 | 4 ✅     | 30 | 2 ✅    |

## 오답노트
2. **다음 설명 중 데이터 모델링이 필요한 주요 이유로 가장 부적절한 것은?** </br>
   ① 업무정보를 구성하는 기초가 되는 정보들에 대해 일정한 표기법에 의해 표현한다. ✅ </br>
   ② 분석된 모델을 가지고 데이터베이스를 생성하여 개발 및 데이터관리에 사용하기 위한 것이다. ✅ </br>
   ③ 데이터베이스를 구축하기 위한 용도를 위해 데이터모델링을 수행하고 ~~업무에 대한 설명은 별도의 표기법~~을 이용한다. ❌ </br>
   ④ 데이터모델링 자체로서 업무의 흐름을 설명하고 분석하는 부분에 의미를 가지고 있다. ✅ </br>


👉🏻 데이터 모델링을 하는 주요한 이유는 업무정보를 구성하는 기초가 되는 정보들에 대해 일정한 표기법에 의해 표현함으로써 정보시스템 구축의 대상이 되는 업무 내용을 정확하게 분석하는 것이 첫 번째 목적이다. </br>
두 번째는 분석된 모델을 가지고 실제 데이터베이스를 생성하여 개발 및 데이터관리에 사용하기 위한 것이 두 번째 목적이다. </br>
다시 말하면, 데이터모델링이라는 것은 단지 데이터베이스만을 구축하기 위한 용도로 쓰이는 것이 아니라 데이터모델링 자체로서 업무를 설명하고 분석하는 부분에서도 매우 중요한 의미를 가지고 있다고 할 수 있다.

---

4. **다음 중 아래 설명이 의미하는 데이터모델링의 유의점에 해당하는 특성은 무엇인가?**

   > 데이터 모델을 어떻게 설계했느냐에 따라 사소한 업무변화에도 데이터 모델이 수시로 변경됨으로써 유지보수의 어려움을 가중시킬 수 있다. 데이터의 정의를 데이터의 사용 프로세스와 분리함으로써 데이터모델링은 데이터 혹은 프로세스의 작은 변화가 애플리케이션과 데이터베이스에 중대한 변화를 일으킬 수 있는 작은 가능성을 줄인다.
   
   ① 중복 ❌ </br>
   ② 비유연성 ✅ </br>
   ③ 비일관성 ❌ </br>
   ④ 일관성 ❌ </br>


👉🏻 데이터 모델링 시의 유의점에 대한 사항 중 비유연성(Inflexibility)에 대한 설명이다. </br>
**중복**: 데이터 모델 내에서 동일한 정보가 두 개 이상의 다른 위치(엔터티, 속성)에 저장되거나 표현되는 상태를 말한다. 이는 불필요한 데이터 저장 공간을 차지하고, 데이터 업데이트 시 비일관성을 유발할 수 있는 잠재적 위험 요인이 된다. </br>
**비일관성:** 데이터 모델 내에서 동일한 정보가 서로 다르게 정의되거나 표현되거나, 혹은 논리적으로 모순되는 관계나 제약 조건이 설정되는 상태를 말한다. 이는 엔터티, 속성, 관계, 식별자 등 데이터 모델의 모든 구성 요소에서 발생할 수 있다.

---

16. **다음 중 아래와 같은 사례에서 속성에 대한 설명으로 가장 부적절한 것은?**

    > 우리은행은 예금분류(일반예금, 특별예금 등)의 원금, 예치기간, 이자율을 관리할 필요가 있다. 또한 원금에 대한 이자율을 적용하여 계산된 이자에 대해서도 속성으로 관리하고자 한다. 예를 들어 원금이 1000원이고 예치기간이 5개월이며 이자율이 5.0%라는 속성을 관리하고 계산된 이자도 관리한다. 일반예금이나 특별예금 등에 대해서는 코드를 부여(예. 01-일반예금, 02-특별예금 등)하여 관리한다.

   ① 일반예금은 코드 엔터티를 별도로 구분하고 값에는 코드값만 포함한다. ✅ </br>
   ② 원금, 예치기간은 기본(BASIC)속성이다. ✅ </br>
   ③ 이자와 이자율은 파생(DERIVED)속성이다. ❌ </br>
   ④ 예금분류는 설계(DESIGNED)속성이다. ✅ </br>


👉🏻 이자는 계산된 값으로 파생속성이 맞지만, 이자율은 원래 가지고 있어야 하는 속성이므로 기본속성에 해당한다.  </br>
속성을 특성에 따른 분류할 시 기본속성, 파생속성, 설계속성으로 분류가 된다. </br>
**기본속성**: 업무로부터 직접 분석하거나 수집되는 속성이다. 엔터티의 본질적인 특징을 표현한다.  </br>
**파생속성**: 다른 속성들의 값으로부터 계산되거나 유추되어 얻어지는 속성이다. 데이터베이스에 직접 저장되지 않는 것이 원칙이며, 필요할 때마다 원본 속성을 이용하여 실시간으로 계산하여 사용한다. </br>
**설계속성**: 데이터 모델링 과정에서 특정 목적을 위해 인위적으로 추가하거나 재조정하는 속성이다. 업무 규칙이나 데이터의 특성상 명확히 기본 속성이나 파생 속성으로 분류하기 어렵거나, 효율적인 데이터 관리를 위해 모델러가 전략적으로 도입하는 속성이다.
---

26. **다음 중 사원엔터티에서 식별자의 특성에 해당하지 않는 것은 무엇인가?**

    ```mermaid
    erDiagram
        DEPT {
            int    dept_id    PK
            string dept_name
            string location
        }
        EMP {
            int    emp_id        PK
            int    dept_id    FK
            string ssn
        }
    
        DEPT ||--o{ EMP : "부서번호"
    ```
   ① 주식별자 ✅ </br>
   ② 단일식별자 ✅ </br>
   ③ 내부식별자 ✅ </br>
   ④ 인조식별자 ❌ </br>

👉🏻 사번은 업무적으로 의미 있는 식별자로 시스템적으로 부여된 인조식별자가 아니라 일반적으로 사원 인스턴스의 탄생과 함께 업무적으로 부여되는 사원 인스턴스의 본질적인 속성에 해당한다 할 수 있기 때문에 본질식별자로 볼 수 있다. </br>
**주식별자**: 대표성을 만족하는 식별자, 타 엔터티와 참조 관계를 연결할 수 있다. → dept_id </br>
**단일식별자**: 각 엔터티의 주식별자를 구성하는 속성이 하나인 경우 → dept_id, emp_id </br>
**내부식별자**: 자연스럽게 존재(스스로 생성되는)하는 식별자 (~ 본질 식별자) → dept_id, emp_id </br>
**인조식별자**: 인위적으로 만들어지는 대체 가능한 식별자 (순서번호)를 사용하여 생성된 식별자. </br>