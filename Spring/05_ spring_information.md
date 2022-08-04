### Dto 변환

Dto가 필요한 이유 
> 요청이 많아지면 -> controller에 요청데이터가 계속 쌓임 -> RequestParam의 개수 증가 -> 비용증가

요청데이터를 하나의 객체(바구니)에 담으면 RequestParam이 쌓이지 않고 한번에 데이터를 넘길 수 있기에 DTO가 생기게 되었다.

>  Dto클래스가 이 '요청데이터'를 하나의 객체로 전달받음 

```java
//회원등록 메서드로 예시 
@Postmapping
public ResponseEntity postMember(MemberPostDto memberpostdto) {
  return new ResponseEntity<>(memberpostdto)
```

### 요청데이터 유효성 검사 
> 서버쪽에서 유효한 데이터를 전달 받기위해 유효성 검증을 실시한다 (validation)

요청데이터들이 모이는 Dto클래스에서 유효성검증 로직을 실행하는것이 가장 효율적
@Email, @NotBlank(message="빈공간이 있으면안됩니다)  ,등 필드위에 적용시켜 유효성검증을 시작한다

> Controller클래스의 핸들러메서드 각각 마다 @valid를 추가시켜 요청데이터를 검증한다는것을 알려야함

```java
//이거 추가해줘야 유효성검증 사용가능 
dependencies {
	implementation 'org.springframework.boot:spring-boot-starter-validation'
	...
	...
}

```
### 요청데이터가 Json형식으로 올 경우 

요청데이터 중 body에 해당하는것을 RequestBody라 한다

> Json형식일 경우 핸들러메서드 각각에 @Requestbody를 붙인다 ( post,put,patch 형식일 경우, 이 http메세지들은 바디에 내용이 있기떄문)

@RequestBody: Json형식의 Requestbody(요청데이터)가 Dto클래스의 객체로 변환시켜준다!!!


여기서 질문! Responsebody는 왜 추가 안하나?

anwer: dto클래스를 다시 Json으로 바꿔주는것 ResponseEntity가 대신 수행해줌


