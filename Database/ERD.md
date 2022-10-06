Entity Relationship Diagram
개체-관계 모델. 테이블간의 관계를 설명해주는 다이어그램이라고 볼 수 있으며, 이를 통해 프로젝트에서 사용되는 DB의 구조를 한눈에 파악할 수 있다.
즉, API를 효율적으로 뽑아내기 위한 모델 구조도라고 생각하면 된다.

직사각형, 다이아몬드, 타원형 및 연결선과 같은 정의된 기호 집합을 사용하여 Entity, Relationships 및 해당 속성의 상호 연결성을 나타낸다.
개체를 명사로, 관계를 동사로 사용하여 문법 구조를 반영한다.



Entity 란?
테이블을 구성하는 객체 구성성분
ex) 항해99라는 Data에 크루원과 매니저의 Entity가 있다고 가정해보자
크루원(Entity)는 이름, 나이, 생일 등의 속성(attributes) 값으로 구성된 Entity 이다.
구성관계
ERD > Entity > Entity attribute
이 Entity 들의 논리적인 관계를 시각적으로 잘 알아보기위해 기호를 사용하여 표기한다.
ERD 사용법
데이터 베이스 모델링
관계형 DB에서 주로 널리 사용된다.
엔티티와 속성들을 테이블과 컬럼들로 변환할 수 있다.
테이블과 관계들을 시각화 할 수 있기 때문에 설계 문제점을 파악할 수 있다.
소프트웨어 엔지니어링
소프트웨어 기획 단계에서 사용된다.
서로 다른 시스템 요소와 서로 간의 관계를 식별하는데 도움된다.
ERD Notation


기본 요소는 Entity, Attribute, Relationship 등이 있다.
확장하여 Weak Entity, Multivalued Attribute, Weak Relationship 이 있다.

Entity
어떤 시스템인지에 따라 Entity는 사람, 장소, 사건(이벤트), 오브젝트가 될 수도 있다.
Weak Entity
존재하는 다른 Entity에 의존적인 Entity를 Weak Entity라고 한다.
그 자식의 속성들에 의해 식별할 수 없는 Entity이다.

Attribute
Attribute 는 특성, Entity의 성격, 관계, 또 다른 속성이다.

Multivalued Attribute
한 값 이상의 값을 가진 Attribute

Derived Attribute
다른 속성에 기초한 속성
ERD 에서는 보기 드물다

Relationship
Relationship은 Entity간의 상호작용을 표현함

Cadinality and Ordinality
Entity들 간의 관계에 대한 추가 정보
One to many, many to many 관계를 나타낼 수 있음

여러 기호들로 관계를 표현할 수 있으나, 기호들만 숙지하여도 충분히 표현이 가능하다.



One
일대일 혹은 일대다 관계이다. 주로 하나의 외래키가 걸린 관계라도 보면 된다.
Many
다대다 관계이다. 중계 테이블을 통하여 여러개의 데이터를 바라보고 있을 때 사용한다.
One (and only one)
위의 조건과 동일하게 일대일 관계이나, 하나의 row 끼리만 연결된 데이터이다.
Zero or one
일대일 혹은 일대다 관계를 가지고 있으나, 필수 조건이 아님을 의미한다.
One or many
일대일 혹은 다대다 관계를 가지고 있음을 의미한다.
관계를 가지고 있으나, 참조되는 row 값들이 불명확함을 의미한다.
Zero or many
참조하는 테이블과의 관계가 불명확한 경우이다.
장바구니처럼 row 생성값이 없을수도, 하나일수도, 여러개일 수도 있는 경우이다.
