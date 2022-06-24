# 쿠키란?
- 이름과 값의 싸응로 구성된 작은 정보
- ex. id (name) = asdf (value) 로 구성되어있습니다.\

쿠키의 특징
- 서버에서 생성 후 전송 > 브라우저(클라이언트)에서 저장
- 유효기간 이후 자동삭제
- 서버에 요청시 domain,path가 일치하는 경우 자동 전송
- 요청체제에 쿠키가 자동으로 따라가서 서버가 판별
- 클라이언트를 구별하기 위한 기술

# 쿠기 관련 다양한 메소드명	설명
getCookies()	HTTP 요청 메시지의 헤더에 포함된 쿠키를 javax.servlet.http.Cookie 배열(Cookie[])로 리턴.
getServerName()	서버의 도메인명을 문자열로 리턴한다.
getReqeustIRL()	요청 URL을 StringBuffer로 리턴한다.
getName()	쿠키의 이름을 가져온다. (String으로 리턴)
getPath() 	쿠키의 유효한 디렉토리 정보를 가져온다. (String으로 리턴)
getValue() 	쿠키에 설정된 값을 가져온다. (String으로 리턴)
setMaxAge(int)	쿠키의 유효한 기간을 설정한다. 
setValue(String value)	쿠키 값을 설정한다.
getMaxAge()	쿠키 만료 기간을 얻어온다.

```java
Cookie cookie = new Cookie("id","asdf")  // 쿠키생성
Cookie.setMaxAge(60*60*30) // 유효 기간 설정
response.addCookie;  //응답에 쿠키 추가
```

# 세션이란

웹 사이트의 여러 페이지에 걸쳐 사용되는 사용자 정보를 저장하는 방법을 의미합니다. 
사용자가 브라우저를 닫아 서버와의 연결을 끝내는 시점까지를 세션이라고 합니다. 앞서 살펴본 쿠키는 클라이언트 측의 컴퓨터에 모든 데이터를 저장합니다.
하지만 세션은 서비스가 돌아가는 서버 측에 데이터를 저장하고, 세션의 키값만을 클라이언트 측에 남겨둡니다.
브라우저는 필요할 때마다 이 키값을 이용하여 서버에 저장된 데이터를 사용하게 됩니다.
이러한 세션은 보안에 취약한 쿠키를 보완해주는 역할을 하고 있습니다.
