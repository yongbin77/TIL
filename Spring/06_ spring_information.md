### 비즈니스 계층 : 비즈니스 로직을 수행하는 즉, 클라이언트의 요청을 처리하는 메서드들을 구현

> Entity class : 1) 비즈니스 로직을 처리하기 위해 필요한 데이터를 전달받고  2) 로직 처리후 결과값을 API계층의 Dto로 전달하는 클래스

![KakaoTalk_20220803_225357195](https://user-images.githubusercontent.com/99226598/182625757-d349d27a-4d58-4302-8e41-b13225aa3adf.jpg)


#### Entity클래스는 DTO클래스에서 요청받는 값 (필드)를 전부 기입하여 생성

### DI 사용

> DI를 사용해 컨트롤러 클래스에서 서비스 클래스에 구현된 메서드들을 사용하게 해준다 .
- DI 사용으로 느슨한 결합을 만들어줌 
- DI를 통해 주입받기 위해서는 스프링 BEAN으로 등록되어 있어야 한다.(ex, 서비스 클래스에 @Service 애너테이션 기입)


### Mapper 

> 매퍼클래스는 API계층의 Dto(요청데이터의 집) -> service계층에서 사용하기 위한 Entity클래스에 보내주는 역할을 함 

#### MapStruct 인터페이스를 사용하여 매퍼클래스를 구현하여 정확도와 편의성을 높이자! 

MapStruct 인터페이스 사용하기 위한 과정

```java 
1. mapstruct 의존라이브러리 추가
dependencies {
	...
	...
	implementation 'org.mapstruct:mapstruct:1.4.2.Final'
	annotationProcessor 'org.mapstruct:mapstruct-processor:1.4.2.Final'
}

2. 해당매퍼 인터페이스 만들기

// @mapper선언하고 componentmodel = "spring" 선언해줘야 스프링빈으로 등록되어 mapstruct사용가능  

@Mapper(componentModel = "spring")
public interface MemberMapper {
    //1. 최종위치   2. 매퍼 이름    3.시작위치
    Member memberPostDtoToMember(MemberPostDto memberPostDto);
    Member memberPatchDtoToMember(MemberPatchDto memberPatchDto);
    MemberResponseDto memberToMemberResponseDto(Member member);
    
    // 1: dto -> entitiy 가는구조 
       2: entity -> dto 가는 구조 

```

3. MemberMapperImpl 클래스 생성한다 
IntelliJ IDE의 오른쪽 상단의 [Gradle] 탭을 클릭한 후, 
[프로젝트 명 > Tasks 디렉토리 > build 디렉토리 > build task]를 더블 클릭하면 MapStruct로 정의된 인터페이스의 구현 클래스가 생성

MemberMapperImpl 클래스는 어디에 생성되는것인가
IntelliJ IDE의 좌측에서 [Project 탭 > 프로젝트명 > build] 디렉토리내의 MemberMapper 인터페이스가 위치한 패키지 안에 생성.

4. 해당 controller클래스에 import 해준다 import ybproject.member.mapstruct.mapper.MemberMapper;


