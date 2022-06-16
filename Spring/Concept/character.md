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
