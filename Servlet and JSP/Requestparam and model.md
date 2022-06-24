# Requestparam이란?

- 요청의 파라미터를 연결한 매개변수를 붙이는 애너테이션 (URL에 입력)

```java 
public String main Requestparam(name = "year",required = true String year) 와

public String main (@Requestparam String year)

http: localhost/yb/requestParam3? year  
year에 대응 값을 넣어줘야합니다, year안쓰면 400번대 에러발생합니다. why? 클라이언트가 요청값을 주지 않았기 떄문입니다. 

이럴떄는, @Requestparam(required=false) int year) { 
필수 입력이 아닐떄 기본값을 주어야 에러가 발생하지 않습니다. defaultvalue "값"으로 넣기 
}
필수입력일떄는 예외처리 , 필수입력이 아닐떄 default 값 넣기

```

# modelAttribute

- 적용대상을 model의 속성으로 자동추가해주는 애너테이션

@modelAttribute mydate date   이렇게 진행되면 key : mydate , value : date 가 저장되어집니다
![KakaoTalk_20220624_230537513](https://user-images.githubusercontent.com/99226598/175552461-5d680d21-bb97-4050-900b-6dd59b25489a.jpg)
![KakaoTalk_20220624_230537513_01](https://user-images.githubusercontent.com/99226598/175552466-0afd1626-4f4d-49cc-b099-ef718e604f07.jpg)
