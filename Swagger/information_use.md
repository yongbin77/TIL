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

### 해결방법 
application.properties 혹은 application.yml 파일에 가서 아래와 같은 소스코드를 추가한다

#### properties 일 경우
spring.mvc.pathmatch.matching-strategy=ant_path_matcher


#### yml 일 경우
mvc:
    pathmatch:
      matching-strategy: ant_path_matcher
      
      
2. Swagger 세팅
![Swagger 세팅](https://user-images.githubusercontent.com/99226598/194250279-94b44f8a-367d-4e97-89b0-a40290c932a9.png)

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.ApiInfo;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;

@Configuration
public class SwaggerConfig {

    // http://localhost:8080/swagger-ui/index.html
    @Bean
    public Docket api() {
        return new Docket(DocumentationType.OAS_30)
                .useDefaultResponseMessages(false)
                .select()
                .apis(RequestHandlerSelectors.basePackage("self.study.controller"))
                .paths(PathSelectors.any())
                .build()
                .apiInfo(apiInfo());
    }

    private ApiInfo apiInfo() {
        return new ApiInfoBuilder()
                .title("Swagger Test")
                .description("SwaggerConfig")
                .version("3.0")
                .build();
    }

}
```
   
   저기 위에서

apis 부분에서 'self.study.controller' 부분을

적용하고자 하는 api가 작성된 자신의 컨트롤러 패키지를 지정해주면 됩니다. 이렇게 설정을 하고나서, 서버를 키신 후에
http://localhost:8080/swagger-ui/index.html


여기로 들어가면
![swagger](https://user-images.githubusercontent.com/99226598/194252094-46d76ae1-edd6-40da-95f4-01cf07e69bf2.png)


이렇게 화면이 뜬다! 

      
      
