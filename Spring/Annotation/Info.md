# Spring Annotation의 종류와 기능
```java
- @RestController : Spring MVC에서 특정 클래스에 추가하면 해당 클래스가 REST API의 리소스를 처리하기 위한 API의 Endpoint로 동작함을 알림 (스프링빈으로 등록됨)
- @RequestMapping : 클라이언트 요청과 요청을 처리하는 핸들러메서드를 매핑해주는 역할, RequestMapping을 Controller클래스에 추가하며 클래스 전체에 사용하는 공통 URL설정 
- @PostMapping : 클라이언트 요청데이터를 서버에 생성할떄 사용하는 애너테이션, 
(GetMapping , PatchMapping..등) 클라이언트에서 요청 전송시, HTTP Method 타입을 동일하게 맞춰야 함 

```
