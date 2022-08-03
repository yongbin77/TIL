### 스프링 아키텍쳐에 관한 내용들 

> spring mvc는 요청사항을 처리하기 위해 만듦 

처리한 작업의 결과를 view로 표현하는 것 외에도 데이터로만 전송하는 방법도 존재 
처리한 작업의 결과 = 데이터 = Model 
- model data를 특정 프로토콜 형태로 변환해서 클라이언트에 전송
- 이 방식은 특정형식의 데이터만 전송하고 프런트엔드에서 이 데이터를 기반으로 HTML을 만듦
- 형식은 바로 json형식이 가장 널리 사용된다 -> 기본포맷 = { "속성" : "값" }
- json형식은 속성과 값을 같이 전송한다. 

> java의 객체를 Json 포맷으로 변환이 가능하다 


-------------
고객의 요청(리소스)을 받아들일 controller클래스가 필요한데 그 controller클래스안에는 이렇게 구성될 수 있다.
리소스: 정보

### 핸들러 메서드 
> controller클래스안에 구현된 '요청처리메서드' 

@Restcontroller - Rest api를 처리하기 위한 api엔드포인트로 동작 (class 위 상단에 붙어짐)

1. question : RestController와 Controller의 차이점은 무엇일까 ?
- anwer : HTTP Responsebody가 생성되는 방식과 사용목적이 다르다 . controller는 주로 view를 반환하기 위해 사용,
Restcontroller는 data를 반환하기 위해 주로 사용된다 -> Responsebody를 활용 ( json으로 자동 convert해준다.)
즉 Restcontroller : Controller + Responsebody.


2. question : 
