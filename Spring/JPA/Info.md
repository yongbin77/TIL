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

