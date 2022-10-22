# Spring Annotation의 종류와 기능
```java
- @SpringBootApplication: 스프링 부트는 기본적으로 이 어노테이션 기준으로 동작하도록 되어 있다. 스프링에서 필수적인 초기화를 담당하는 @EnableAutoConfiguration, @ComponentScan,     @Configuration 어노테이션이 함축, 이 클래스를 기준으로 빈 스캔을 하게 되며, 여기다가도 @Bean 어노테이션을 이용한 빈 정의도 가능
- @EnableAutoConfiguration: 스프링 부트의 핵심 어노테이션으로, 여태까지 Spring boot 없이 XML이던 자바던 필수적으로 annotation-driven 이나 annotation-config 등... 
  필수적으로 스프링에 세팅하는 왠만한 것들을 자동 설정하여 일단 돌아가게 하도록 도와주는 어노테이션
- @RestController : Spring MVC에서 특정 클래스에 추가하면 해당 클래스가 REST API의 리소스를 처리하기 위한 API의 Endpoint로 동작함을 알림 (스프링빈으로 등록됨)
- @RequestMapping : 클라이언트 요청과 요청을 처리하는 핸들러메서드를 매핑해주는 역할, RequestMapping을 Controller클래스에 추가하며 클래스 전체에 사용하는 공통 URL설정 
- @PostMapping : 클라이언트 요청데이터를 서버에 생성할떄 사용하는 애너테이션, 
(GetMapping , PatchMapping..등) 클라이언트에서 요청 전송시, HTTP Method 타입을 동일하게 맞춰야 함 
- @Configuration : Spring Bean 검색대상인 Configuration 클래스로 간주, Bean 애너테이션 (@Bean)추가된 매서드 검색 후 해당메서드에서 리턴하는 객체를 Bean으로추가 
- @RequestParam : 클라이언트에서 전송하는 요청데이터를 x.www.form.ur ~ 형식으로 전소앟면 서버쪽에서 전달받을떄 사용하는 애너테이션 
                  URL뒤에 붙는 파라메터 값을 가져올떄 사용
- @Getmapping : 클라이언트가 서버에 리소스 조회할떄 사용하는 애너테이션
- @Requestbody : JSON형식의 RequestBody를 객체로 변환시켜주는 것 (클라이언트에서 전송하는 요청데이터가 JSON형식이어야한다)
- @ResponseEntitiy : JSON으로 응답해줄떄 사용 ( ResponseEntity객체가 존재하기에 @Responsebody 애너태이션을 따로 설정해줄 필요는 없다)
- @Getter,Setter : lombok라이브러리에서 제공하는 애너테이션, 각 멤버변수에 해당하는 getter/setter 메서드 일일이 작성하는 수고를 덜어줌
  (getter : 요청값 받아오기 , setter : 값을 설정하기 ) 라고 생각하면 쉬움 
- @AllArgsConstructor : 클래스에 추가된 모든멤버 변수를 파라미터로 갖는 생성자를 자동으로 생성해줌
- @NoArgsConstructor : 파라미터 없는 기본생성자 자동으로 생성
- @ service : 서비스계층 및 클래스에 애너테이션 추가시 Spring Bean으로 등록 (@Restcontroller와 동일) 
- @ Requiredargs : 생성자를 자동으로 만들어 의존관계를 자동으로 설정해줌
- @ResponseEntity : 주로 @Controller, @RestController가 붙은 Controller클래스의 핸들러메서드에서 요청처리의 응답을 구성하는데 사용된다
new ResponseEntity로 객체생성하는게 일반적인 방법
return ResponseEntity<>(~,HttpStatus.~) 으로 사용됨
응답 데이터를 래핑함으로써 조금 더 세련된 방식으로 응답 데이터를 생성
- @RequestBody : HTTP요청데이터를 Body로 받을떄 사용하는 애너테이션 (DTO클래스 옆에 사용)
DTO클래스 앞에 붙은 @RequestBody애너테이션은 JSON형식의 Requestbody를 DTO클래스의 객체로 변환
즉, 클라이언트쪽에서 전해주는 RequestBody가 JSON형식이어야함
Responsebody는 사용하지 않는데 그 이유는 ResponseEntity가 Responsebody를 포함하고 있기떄문
- @Email : 클라이언트 요청데이터에 이메일주소 포함여부 검증하는 유효성 검증 애너테이션
- @valid : Dto클래스 옆에 붙어 memberDTO객체에 유효성 검증적용하는 애너티에션
- @notBlank : 정보가 비어있지 않는지 검사하는 애너테이션, @notBlank(message="비어있으면안됩니다")로 사용가능
- @pattern : 정규표현식에 매치되는것인지 확인
  @patter(regexp = " " , message=" " )
  - @BeforeEach : 테스트 케이스 실행전 전처리 과정을 해주는 애너테이션, 테스트 메서드 실행 전 테스트메서드 숫자만큼 초기화를 하며 먼저 수행됨 
 - @Lob은 Large Object의 약자로 이미지, 동영상, 대용량 데이터등을 의미한다. (ex CLOB = Char Lob)
```
