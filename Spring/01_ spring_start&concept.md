# Spring의 시작과 발전

Spring은 2000년대 초 웹,어플리케이션의 수요가 폭팔적으로 증가함에따라 기존 개발도구들이 사용하기에 복잡하고 수요를 감당하지 못하게 되어 Spring을 출시하였습니다.
그렇게 Spring프레임워크의 또 다른 장점은, 기존의 웹어플리케이션 개발자가 이직 및 퇴사하여도 정해진 구조안에 Spring 사용이 정해져있기에 다른 개발자가와도 유지보수가 쉬웠습니다.
그러던 중 2014년 Spring이 무겁다는 단점을 보완하기 위해 Spring Boot를 출시하였습니다.

> 그렇다면 최근에는 Spring boot를 사용하는데 왜 오래된 Spring을 배워야하나요의 질문이 생길 수 있습니다. 
> 그 이유는 서블릿 > JSP > Spring > Spring boot  이렇게 발전되는 순서중 서블릿과 jSP 그리고 스프링까지 배운다면 원리에 대해 완벽하게 파악할 수 있고 Spring과 Springboot의 사용법은 같다! 



### Framework과 Library의 차이?



애플리케이션의 구현을 위해 필요한 여러가지 기능들을 제공한다라는 의미에서 Framework과 Library는 유사하다고 볼 수 있지만 Framework과 Library에는 결정적인 차이점이 존재하는데 그것은 바로 애플리케이션에 대한 제어권입니다.

 애플리케이션 코드는 애플리케이션을 개발하는 사람 즉, 개발자가 작성을 할 것입니다. 이렇게 개발자가 짜 놓은 코드내에서 필요한 기능이 있으면 해당 라이브러리를 호출해서 사용하는 것이 바로 Library입니다. 즉, 애플리케이션 흐름의 주도권이 개발자에게 있는 것입니다.

즉, 애너테이션이나 main() 메서드 내의 메서드들의 애플리케이션 흐름에 주도권이 개발자가 아닌 Framework에 있는것은 framework입니다. 
짧은 내용이긴하지만Framework Library의 차이점을 학습하면서 Spring Framework의 핵심 개념인 IoC(Inversion Of Control, 제어의 역전)라는 중요한 개념을 알게된 것입니다.


## Spring의전개


Spring Framework이 도입되기 전에는 JSP나 Servlet 기술을 사용한 Model1, Model2 아키텍쳐를 기반으로 한 Java 웹 애플리케이션을 제작하였습니다.
Spring MVC 방식이 도입됨으로써 Java 웹 애플리케이션의 제작 방식이 획기적으로 변하게 되었습니다.
Spring MVC 설정의 복잡함과 어려움을 극복하기 위해 Spring Boot이 탄생하게 되었습니다.


## Spring의 구조


![스프링 구조](https://user-images.githubusercontent.com/99226598/181009374-1e800c52-19e6-4726-b309-0038fb500a13.png)

Core: 제어 역전(IoC)과 의존성 주입(DI) 기능을 제공합니다. 제어 역전은 전체적인 프로세스의 흐름이 개발자가 아니라 프레임워크(여기서는 Spring)에 의해 결정된다는 뜻입니다. 개발자는 프레임워크가 정한 틀에 따라 적절한 코드를 작성해 넣으면 됩니다.  
DAO: JDBC 추상 계층을 제공하고 JDBC는 자바의 데이터베이스 커넥터이고 데이터가 담겨있는 VO(Value Object) 클래스를 이용해 사용합니다.
ORM: JPA, Hibernate와 같은 ORM이나 MyBatis 같은 데이터베이스 API 등과 통합할 수 있는 기능을 제공합니다.
AOP: 스프링 프레임워크에서 제공하는 AOP 패키지를 제공합니다. 
Web: Spring Web MVC, Struts, WebWork 등 웹 어플리케이션 구현에 도움되는 기능을 제공합니다.
JEE: EJB, JMX 등의 엔터프라이즈 J2EE 스펙에 관한 기능을 제공합니다.
