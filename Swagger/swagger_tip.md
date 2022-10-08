
## Tip

컨트롤러에 각 메소드 마다 메소드 위에 어노테이션으로
```java
@ApiOperation(value = "전체 회원 보기", notes = "전체 회원을 조회한다.")
```

@ApiOperation 을 붙여주면


![image](https://user-images.githubusercontent.com/99226598/194254209-198d8eed-d19d-4582-8f29-5af554a5c5bb.png)

이런식으로 스웨거에 제목과 설명이 생긴다! 

value = 제목 , notes = 내용 

즉, Controller의 진입메소드에 붙여주면된다! 
