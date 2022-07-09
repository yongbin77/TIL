# JPA(JAVA Persistence API)란?
데이터 저장 , 조회 작업은 JPA를 거쳐 JPA구현체인 Hiberate ORM을 통해서 이루어집니다. Hiberat ORM은 JDBC API를 이용해 데이터베이스에 접근합니다.

Persistence를 해석하면 영속성 지속성입니다. 영속성이란 단어가 쉽게 사용되는 단어가 아니니 지속성이라는 단어로 기억하면 조금더 와닿을겁니다.

## JPA의 P인 지속성이 오래지속하는것은 과연 무엇일까요 ?
- ORM은 객체와 데이터베이스 Table의 매핑을 통해 '엔티티클래스 객체만 포함된 정보'를 테이블에 저장하는 기술입니다.
- JPA에서는 테이블과 매핑하는 '엔티티객체정보' 를 '지속성(영속성) 콘테스트'라는 곳에 보관해 애플리케이션 내 '오래 지속'되도록 합니다.
- 엔티티 클래스를 지속성 Context에 저장하면 지속성클래스내부의 1차캐시에 엔티티가 저장이 됩니다.

![117632455-1cc98600-b1b8-11eb-9db0-a6c460ea47dd](https://user-images.githubusercontent.com/99226598/177574593-78bc28f5-a4e8-4d6c-ba12-b0bd8bf2e5fd.png)

특정 클래스에 @Configuration 애너테이션을 추가하면 Spring에서 Bean검색대상인 Configuration클래스로 간주해서, Bean애너테이션이 추가된 메서드를 검색 후 해당메서드에서
리턴하는 객체를 Spring Bean으로 추가합니다.
실행문쪽 CommndLineRunner는 스프링에서 제공하는 객체서비스입니다.


영속성(지속성) 컨테스트에 엔티티 저장 < JPA에서 사용하기 위한 Entity클래스 설정 변경> 
```java
@Getter 
@Setter
@Entity
@NoArg~ 를 붙여 엔티티클래스의 기본 구조를 완성합니다.

// @ Entity, @ Id 애너테이션을 붙이면 JPA에서 해당클래스를 엔티티클래스로 인식하니 꼭 같이 붙여야합니다 ( 1 + 1)으로 생각 
@Generated Value : 식별자를 생성해줍니다, 쉽게 말하자면 식별자에 해당하는 멤버 변수에 @Generated Value를 추가하면 데이터베이스 테이블에서 기본기가 되는 식별자를  
                    자동으로 생성해줍니다.
                    ```

- JPA영속성 콘테스트는 Entity Manager에 의해 관리되는데 EntityManager 클래스의 객체는 Entity ManagerFactory 객체를 Spring으로부터 DI받을 수 있습니다.
```java
this.em = emFactory.createEntityManager(); // 엔티티매니저 팩토리의 매서드를 사용해 엔티티 Manager클래스의 객체를 얻을 수 있습니다.
EntityManager 객체를 통해 JPA API메서드를 사용가능케 합니다.
```
persist(XXXX) 메서드를 호출하면 영속성콘테스트 Member객체를 저장합니다. > 1차캐시에 멤버저장 
XXXX객체는 쓰기지연 SQL저장소에 Insert쿼리형태로 등록됩니다.
find를 통해 영속성 컨텍스트에 멤버가 잘 저장되어있는지 확인할 수 있습니다( 첫번쨰 값: 조회할 엔티티타입, 두번쨰 값: 식별자값(엔티티) )
- tip : em.persist(XXXX)를 호출할 경우, 영속성 컨텍스트에 xxxx 객체가 저장되지만 실제 테이블에 정보를 저장하지는 않습니다, 또한 실제 log에 insert쿼리에도 X

## 영속성 컨텍스트와 테이블에 엔티티 저장

만약에 회원정보 (Member)정보를 실제 테이블에 저장한다고 가정해보겠습니다.

- 실제 테이블에 member정보 저장 = Member객체를 영속성컨텍스트 뿐만아니라 데이터베이스 Table에 저장

EntitiyManager를 통해서 Transaction 객체를 얻어야 합니다 . JPA에서는 이 Transaction 객체를 기준으로 테이블에 저장합니다
(this.tx = em.getTransaction();  -> transaction 객체 얻어서 담궈둔곳 : tx

그후 , JpA에서는 Transaction을 시작하기 위해서는 tx.begin() 메서드를 먼저 호출해야합니다.
Member객체를 영속성 컨텍스트에 저장
tx.commit() 을 호출하는 시점에 영속성컨텍스트에 저장되어 있는 member객체를 데이터베이스 table에 저장합니다.

코드를 실행하면


