##  PART 2. 엔터티
: 업무에서 관리해야 하는 데이터의 집합, 명사형, 인스턴스의 집합

**🔹 엔터티의 특징**
1. 반드시 해당 업무에서 필요하고 관리하고자 함
2. 유일한 식별자에 의해 식별 가능
3. 두 개 이상의 인스턴스의 집합
4. 업무 프로세스에 의해 이용되어야 함
5. 반드시 속성이 있어야 함
   (예외적으로 관계엔터티의 경우는 주식별자 속성만 가지고 있어도 엔터티로 인정)
6. 다른 엔터티와 최소 1개 이상의 관계가 있어야 함.
   (관계를 생략하여 표현해야하는 경우는 통계성 엔터티, 코드성 엔터티, 시스템 처리시
   내부 필요에 의한 엔터티 도출과 같은 경우)

### ✅ 엔터티의 분류

**🔹 유무형에 따른 분류:** 유형, 개념, 사건 엔터티
- 유형 엔터티: 물리적 형태가 있고, 안정적이고 지속적으로 활용되는 엔터티
  ex) 사원, 물품, 강사 등
- 개념 엔터티: 물리적 형태가 없고, 개념적인 정보를 담고 있는 엔터티
  ex) 조직, 보험 상품 등
- 사건 엔터티: 업무 수행시 발생하는 엔터티. 주로 특정 행위의 발생을 기록한다.
  ex) 주문, 청구, 미납 등

**🔹 발생 시점에 따른 분류**: 기본/키, 중심, 행위 엔터티
- 기본 엔터티(Key Entity): 원래 존재하는 정보, 타엔터티의 부모 역할, 자신의 고유한 주식별자를 가진다.
  ex) 사원, 부서 등
- 중심 엔터티(Main Entity): 기본 엔터티로부터 발생한다. 다른 엔터티와의 관계로 많은 행위 엔터티를 생성한다.
  ex) 계약, 사고, 주문 등
- 행위 엔터티(Active Entity): 2개 이상의 부모 엔터티로부터 발생하며, 내용이 자주 바뀌거나 양이 증가한다.
  ex) 주문 목록, 사원 변경 이력 등

### ✅ 엔터티의 명명규칙
1. 현업 업무에서 사용하는 용어를 사용한다.
2. 약어 사용을 지양한다.
3. 단수 명사를 사용한다.
4. 고유한 이름 사용한다. (유일성 보장)
5. 생성 의미대로 부여한다. (명확성)