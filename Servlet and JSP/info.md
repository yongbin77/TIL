# JSP와 서블릿은 무엇일까 ?

## Servlet
- Servlet이란 웹 기반의 요청에 대한 동적인 처리가 가능한 Server Side에서 돌아가는 Java Program
- Java 코드 안에 HTML 코드 (하나의 클래스)
- 웹 개발을 위해 만든 표준
 
## JSP

- Java 언어를 기반으로 하는 Server Side 스크립트 언어
- HTML 코드 안에 Java 코드
- Servlet를 보완하고 기술을 확장한 스크립트 방식 표준


이 둘은, 기능의 차이는 없고 역할의 차이만 존재합니다.
서블릿을 발전시킨게 Spring 입니다. 그래서 Spring에서는 서블릿의 일부분을 사용합니다

``` java 
서블릿에서 @ WebServlet = @ Controller + @ RequestMapping 과 같습니다.
 // WebServlet은 서블릿의 맵핑 URL주소이다 . 
 ```
 
 
 

