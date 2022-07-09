# Spring Annotation의 종류와 기능
```java
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

```
