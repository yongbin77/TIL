 JAVA인터프리터가 메인메소드를 호출하는 과정을 한번 다시 기억해보겠습니다.
 
 java인터프리터가 메인메소드를 우선 호출하게 되고 main() 메서드부터 실행하게 됩니다~
 static이 있으면 객체를 생성할 필요 없기에 객체생성과정을 거치지 않고 메인메서드를 부를 수 있습니다.
 
 ## 원격 프로그램 실행을 위한 과정은 위의 상황과 동일합니다.
 
 
![123123123](https://user-images.githubusercontent.com/99226598/174137660-5c1ac0a8-8f02-42fe-a24d-42947df5446f.png)

쉽게 표현하자면, 원격프로그램을 실행하기 위해서는 필요한것이 있는데 바로 '브라우저'입니다.
클라이언트는 URL을 (Https:111.222.333.444.8080)입력하고 엔터를 누르면 was의 Tomcat이 8080포트를 실행하고 main메서드를 실행시켜 클라이언트에게 화면을 보여줍니다.

그렇다면 외부에서 호출할 수 있도록 프로그래밍 하는 방법은 무엇일까요
1. 프로그램 등록 
2. URL과 프로그램 연결

- 프로그램을 실행 하려면 어떤 URL을 등록해야하는지, 이 작업이 선행되야 원격 프로그래밍 가능 

```java

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;

// 1. 원격 호출가능한 프로그램으로 등록 
@Controller
public class Hello {
	//2. URL과 메서드를 연결, 브라우저에 hello라고 주소창에 치면 main메서드가 호출되서
    //Hello가 찍힘
	@RequestMapping("/hello")
	public void main() { //인스턴스 메서드(static없는것) 왜 인스턴스 메서드로 하냐면 
		//static 메서드로 할시 static 변수만 호출가능한대 인스턴스 메서드로 하게되면 
		//인스턴스 변수,스태틱 변수 등 둘다 부를 수 있으므로 인스턴스 메서드로 호출하는게 편함
		System.out.println("Hello"); 
	}
}
```

// @ Controller 는 프로그램을 등록 <클래스 앞에 쓴다>
// @ requestMapping ("/  ")  URL과 MAIN()함수를 연결 즉 https:111.222.333.444.8080/hello를 누르면 호출 Hello 메소드 실행 



# HTTP 요청과 응답
http://111.222.333.444.8080/ch2/requestinfo 가 있습니다.
여기서 클라이언트가 URL을 입력하여 요청을하면 서버의 톰캣이 HTTP Servelet request 객체를 만들어 담습니다.


![9985D2485C52B72E2F](https://user-images.githubusercontent.com/99226598/174153932-a4a0ed08-7c66-45ea-97f3-a5475732f39c.png)

```java

@Controller 
public class ReuqustInfo{
@requestMapping("/requestinfo")

public void main(HTTPServeletRequest request){
//여기서 request 에 톰캣이 담았던 정보들을 넘겨준다.
System.out.println(request.parameter("year");
System.out.println(request.parameter("month");
	}
}

//이렇게 진행 시 URL에  http://111.222.333.444.8080/ch2/requestinfo/year=2022&month=10 으로 바뀌어 보여짐


BUT...!!!

이렇게 콘솔에만 출력시 정작 서버창(브라우저 출력창)에는 보이지 않습니다. 
이러한 문제를 해결하기 위해, response를 이용합니다. 
main{HTTPServeletrequest request, HttpServeletresponse response) {
response.setContenttype("text/html") // 브라우저는 내가 보내는 내용이 text인지 무엇인지 모르기에 text와 HTML을 보낸다는 것을 알려줍니다.
response.setcharaterencoding("utf-8") //한글깨지는 것 방지
prinwriter out = response.getwriter //response 객체에서 출력스트림을 얻는다.
out.println("~~~) 
}
```
# HttpServlet
- HTTP 프로토콜을 사용하는 웹 브라우저에서 서블릿 기능을 수행합니다.
- 따라서 개발자는 HttpServlet을 상속받아 많은 기능을 사용할 수 있습니다.
- WAS가 웹브라우저로부터 Servlet 요청을 받으면
요청 받을 때 전달 받은 정보를 HttpServletRequest 객체를 생성해서 저장합니다.
웹브라우저에 응답을 반환할 HttpServletResponse 객체를 생성합니다. (응답을 담기 전 빈 객체)
생성된 HttpServletRequest, HttpServletResponse 객체를 Servlet에 전달합니다.
# Servlet
- WAS에서 동적 웹페이지 구현을 할 수 있도록 도와주는 자바 클래스의 일종 (프로그래밍 기술)
- 서블릿 관련 추상 메서드를 제공하는 인터페이스
- Servlet 덕분에 개발자는 의미있는 비즈니스 로직에 집중할 수 있습니다.
  EX. init(), service() 등
# HttpServletRequest
- HTTP 요청 정보(클라이언트 요청, 쿠키, 세션 등)를 제공하는 인터페이스 HTTP 프로토콜의 request 정보를 서블릿에게 전달하기 위한 목적으로 사용합니다.
- Message Body의 Stream을 읽어들이는 메서드를 가지고 있다.
메서드 예시
getParameterNames() : 현재 요청에 포함된 매개변수 이름을 열거 형태로 넘겨준다.
getParameter(name) : 문자열 name과 같은 이름의 매개변수를 가져온다.
# HttpServletResponse
- HTTP 응답 정보(요청 처리 결과)를 제공하는 인터페이스
- Servlet은 HttpServletResponse객체에 content-type, 응답 코드, 응답 메세지 등을 담아서 전송한다.
Servlet으로 들어온 요청은 텍스트(HTML)로 응답을 보내기 때문에 출력 스트림을 받기 위해 주로 response로부터 writer 객체를 얻어서 내보낸다.
PrintWriter w = response.getWriter();
메서드 예시
setContentType() : 요청에 대해 클라이언트에게 돌려줄 content-type 결정
setCharacterEncoding()
