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

url 패턴
@WebServle("/ name~") 하나말고 여러개가 등록가능합니다. ("/hello*") 누르면 맵핑에 따라 헬로우 뒤에 붙은 어떤단어 붙여도 url 화면 출력
url 패턴이랑 여러개가 등록가능하며 url.pattern으로 연결되는 상황을 말합니다. 

# 유효범위(Scope)와 속성(attribute)

서블릿 JSP의 유효범위와 속성을 알기 전 HTTP의 특징을 우선 알아두어야합니다.
가장 중요한 특징은 HTTP는 상태정보를 저장하지 않는다는것입니다. (stateless) 
![HTTP로는 불가능](https://user-images.githubusercontent.com/99226598/175280120-2f5e4309-f9e2-45d6-8060-aff941b25cae.jpg)
그러므로 필요한게 상태저장소 이고 4개의 상태저장소가 존재합니다 .
map형식으로 저장 (key , value) 
저장소에 값을 읽고 쓰기 위한 메서드 용어 
- SetAttribute() : 쓰기(저장)
- GetAttribute() : 읽기  
### pageContext 저장소
- 읽기 쓰기가 가능하지만 다른 page에는 접근하지 못합니다.

### application 저장소
- 전체에서 접근 가능한 저장소입니다. 그러므로 보안에 취약합니다.

###  session 저장소
- 그래서 개별저장소인 session이 만들어졌습니다. 클라이언트 마다 하나의 개별저장소가 생긴것입니다. 
- 클라이언트 마다 갖고 있는 저장소로 logout하면 개별저장소는 제거 됩니다
- 만약 100만명의 회원이라면 100만개의 session이 존재하므로 서버에 부담이 큰 부작용이 존재합니다.

### request 저장소
- 객체 자체로 저장하는 request 저장소 
- 요청이 처리되는 동안에만 존재하고 만약 다른 jsp로 넘기고 싶다면 forward를 통해 다른 page에 데이터를 명령합니다 .
- 

# filter

서블릿이 3개의 클래스를 가동한다 할때 1.전처리 2.처리 3.후처리 이 묶음 3개가 있다면 1번과 3번은 중복이 됩니다.
이 상황에서 공통적인 요청인 전처리와 응답후 처리를 각 클래스마다 3번이 아닌 한번씩만 가동하여 '중복을 제거'합니다

요청 > 전처리 > 서블릿 호출 > 3개 묶음 처리 > 후처리 > 응답 
이렇게 하는것을 filter라 하며 코드의 분리 , 중복을 제거하는 이점을 갖고있습니다.
