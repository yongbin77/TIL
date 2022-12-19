

> root계정은 MySQL 관리자 계정으로 실제 작업이나 test는 별도의 계정을 만들어 필요한 권한을 부여해주고 사용하는것이 바람직

MYSQL Workbench에서 나오는 Schema의 의미 

Schema의 의미를 알기전 'metadate'를 알아야 한다.

metadata는 data about data , 즉 데이터 속에 데이터(data about data)다 
예를 들자면 핸드폰 사진첩 내부의 사진들 중 개별 사진마다 이 사진의 픽셀,용량,찍힌 날짜 등 해당 사진을 설명하는 다양한 세부적인 요소들이 존재
이 세부적인 요소를 데이터 속 데이터라는 '메타데이터'라 부름

데이터베이스  query의 의미
데이터베이스 사용 중 쿼리를 날린다라는 용어를 많이 사용하는데 여기서 쿼리는 데이터베이스를 생성,수정,삭제 등 요청해 데이터베이스를 생성 및 변경을 만들어주는 요청이라 생각하면됨

>Schema : 데이터베이스의 구조를 기술
>스키마는 데이터베이스를 설계할 때 정해지며 한번 정해지면 자주 바뀌지 않는다.
속성(attribute ) 등 다양한 내용이 기술 

----


### Mysql 인텔리제이 사용

#### bulid.gradle에 설정

```java
runtimeOnly 'mysql:mysql-connector-java'
// runtimeOnly : 컴파일할떄 mysql사용 하는것이 아닌 실행시점에 사용한다는 뜻
```

#### application.yml
```java
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:(MySQL의 포트번호)/(DB이름)?serverTimezone=Asia/Seoul
    username: (user명)
    password: (password)
    
    ()에 알맞는 값을 대입할떄, () 제거해야함
```

## 중요!  Mysql 계정 및 권한 설정 , connection에 따른 스키마 설정  
https://mystyle1057.tistory.com/entry/MySQL-Workbench-%EC%82%AC%EC%9A%A9%EC%9E%90-%EA%B3%84%EC%A0%95-%EC%83%9D%EC%84%B1%EA%B6%8C%ED%95%9C-%EB%B6%80%EC%97%AC-%EB%B0%A9%EB%B2%95
