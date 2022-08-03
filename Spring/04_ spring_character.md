### 스프링 아키텍쳐에 관한 부가적인 내용들 

> spring mvc는 요청사항을 처리하기 위해 만들어진것 

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

@ResponseEntitiy: HTTP Entity의 확장클래스로서 HTTPStatus 상태코드를 추가한 전체 Http응답으로 표현
- controller or RestController클래스 붙은것의 요청처리 응답으로 구성하는데 사용된다.


Controller 클래스에 자주사용되는 애너테이션에 관한 나의 궁금증과 답변 

@Restcontroller - Rest api를 처리하기 위한 api엔드포인트로 동작 (class 위 상단에 붙어짐)

1. question : RestController와 Controller의 차이점은 무엇일까 ?
- anwer : HTTP Responsebody가 생성되는 방식과 사용목적이 다르다 . controller는 주로 view를 반환하기 위해 사용,
Restcontroller는 data를 반환하기 위해 주로 사용된다 -> Responsebody를 활용 ( json으로 자동 convert해준다.)
즉 Restcontroller : Controller + Responsebody.


2. question : 클라이언트 요청을 받는 RequestParam과 Pathvariable의 차이점이 뭐지?
- anwer : Requestparam은 쿼리파라미터 "?"를 기준으로 key와 value값(요청값)을 받기위해서 사용되는 것,
- pathvariable은 예를 들자면 @Getmapping({"member-id"}) 아이디를 찾는 요청 값 같은 사람마다 다른 아이디를 동적인 요청으로 받아들일떄 사용 
- {"  "} 어떤것을 넣느냐에 따라 동적인 값으로 바뀌어 메서드 수행

이 두가지의 애너테이션을 활용해 메서드 만드는 방법 
```java
1. RequestParam
public String car(@RequsetParam("carname") String carname){ ...}

2. pathvariable 
@Getmapping({"member-id"})
public String findmember(@Pathvariable("member-id")String memberid) {...}
//Getmapping에 있는 동적인 값과 Pathvariable의 값은 같아야한다 그래야 에러가 안남  
// 뒤에있는 String에 요청값들을 담는다.
```



