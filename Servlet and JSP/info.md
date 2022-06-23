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
 # 서블릿의 규칙
 
1. HttpServlet을 상속받아야 한다.  public class yb extends HttpServlet (고정)
2. 서블릿에서는 service메소드가 항상 고정 (고정)
``` java
public void Service(HttpServletRequest request , HttpServletResponse response throws IoException)
```

- 서블릿과 Controller 를 비교해보면 굉장히 유사합니다. 하지만 Controller가 여러가지면에서 더욱 발전되어있습니다. 
- 예를 들자면 Controller는 상속을 받지 않고 ,매개변수가 고정되어있지 않아 필요한것만 사용하면 됩니다.
 
 서블릿의 과정 
 ![캡처 2](https://user-images.githubusercontent.com/99226598/175276151-1824801f-02c7-4253-8696-abdf96b632c5.PNG)

# 유효범위(Scope)와 속성(attribute)



