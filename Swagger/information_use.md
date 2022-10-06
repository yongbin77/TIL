## Swagger 란?

간단히 말해서 스웨거는 

> 우리가 만든 REST API 서비스를 설계, 빌드, 문서화, 소비하는 일들을 도와주는 대형 도구 생태계의
지원을 받는 오픈 소스 소프트웨어 프레임워크이다

이런 말은 너무 어려우니깐, 쉽게 말하자면, 스웨거는 보통 협업할 때 사용되며 프론트엔드에게 API를 쉽게 설명하기 위해 이용된다.

> 즉 내가 어떤 API를 만들었는지 문서화 시켜서 프론트나, 다른 백엔드 개발자들과의 협업을 조금 더 효율적이고 편하게 만들어준다.

## Gradle 환경에서 Swagger 사용법

1. build.gradle 에서 아래와 같은 dependencies 를 추가
```java
// Swagger 
implementation 'io.springfox:springfox-boot-starter:3.0.0'
```

디펜던시 추가 후에 코끼리를 눌러서 디펜던시 적용을 시켜주고, 프로젝트 실행

> 만약에 프로젝트가 실행되지 않고, Swagger NullPointerException 오류가 뜬다면

#### 해결방법 
application.properties 혹은 application.yml 파일에 가서 아래와 같은 소스코드를 추가한다

# properties 일 경우
spring.mvc.pathmatch.matching-strategy=ant_path_matcher


# yml 일 경우
mvc:
    pathmatch:
      matching-strategy: ant_path_matcher
      
      
      
