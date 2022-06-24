# Requestparam이란?

- 요청의 파라미터를 연결한 매개변수를 붙이는 애너테이션 (URL에 입력)

```java 
public String main Requestparam(name = "year",required = true String year) 와

public String main (@Requestparam String year)

http: localhost/yb/requestParam3? year  
year에 대응 값을 넣어줘야합니다, year안쓰면 400번대 에러발생합니다.
