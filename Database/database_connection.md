## database와 인텔리제이 연동

```java

spring: #띄어쓰기 없음
 datasource: #띄어쓰기 2칸
   url: jdbc:h2:tcp://localhost/~/kybdatabase #4칸     // 이곳에 기존에 내가 만들어놓은 database와 연동한다. 
   username: sa 
   password:
   driver-class-name: org.h2.Driver
 
 jpa: #띄어쓰기 2칸
   hibernate: #띄어쓰기 4칸
     ddl-auto: create #띄어쓰기 6칸
   properties: #띄어쓰기 4칸
     hibernate: #띄어쓰기 6칸
# show_sql: true #띄어쓰기 8칸 
       format_sql: true #띄어쓰기 8칸
logging.level: #띄어쓰기 없음
 org.hibernate.SQL: debug #띄어쓰기 2칸
# org.hibernate.type: trace #띄어쓰기 2칸


```
