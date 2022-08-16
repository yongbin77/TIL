
## API 문서화

>API 문서화란 클라이언트가 REST API 백엔드 애플리케이션에 요청을 전송하기 위해서 알아야 되는 요청 정보(요청 URL(또는 URI), request body, query parameter 등)를 문서로 잘 정리하는 것을 의미


### Spring Rest Doc 장점

>Spring Rest Docs를 사용한 API 문서화의 대표적인 장점은 테스트 케이스에서 전송하는 API 문서 정보와 Controller에서 구현한 Request Body, Response Body, Query Parmeter 등의 정보가 하나라도 일치하지 않으면 테스트 케이스의 실행 결과가 “failed” 되면서 API 문서가 정상적으로 생성이 되지 않는다.
>즉, 테스트 케이스의 실행 결과를 “passed”로 만들지 않으면 API 문서 생성이 완료되지 않는다.
>테스트 케이스의 실행 결과가 “passed”이면 Controller에 정의되어 있는 Request Body나 Response Body 등의 API 스펙 정보와 일치하는 API 문서가 만들어진다.


### Rest Doc 진행 단계

테스트 코드 작성

1. 슬라이스 테스트 코드 작성
- Spring Rest Docs는 Controller의 슬라이스 테스트와 밀접한 관련이 있다, Controller에 대한 슬라이스 테스트 코드를 먼저 작성

2. API 스펙 정보 코드 작성
- 슬라이스 테스트 코드 다음에 Controller에 정의 되어 있는 API 스펙 정보(Request Body, Response Body, Query Parameter 등)를 코드로 작성

3. test 태스크(task) 실행

- 작성된 슬라이스 테스트 코드를 실행
- 하나의 테스트 클래스를 실행시켜도 되지만 일반적으로 Gradle의 빌드 태스크(task)중 하나인 test task를 실행 시켜서 API 문서 스니핏(snippet)을 일괄 생성
- 테스트 실행 결과가 “passed”이면 다음 작업을 진행하고, “failed”이면 문제를 해결하기 위해 테스트 케이스를 수정한 후, 다시 테스트를 진행

4. API 문서 스니핏(.adoc 파일) 생성

- 테스트 케이스의 테스트 실행 결과가 “passed”이면 테스트 코드에 포함된 API 스펙 정보 코드를 기반으로 API 문서 스니핏이 .adoc 확장자를 가진 파일로 생성됨

> 스니핏(snippet)은 일반적으로 코드의 일부 조각을 의미하는 경우가 많은데 여기서는 문서의 일부 조각을 의미
스니핏은 테스트 케이스 하나 당 하나의 스니핏이 생성되며, 여러개의 스니핏을 모아서 하나의 API 문서를 생성할 수 있다!

5. API 문서 생성

- 생성된 API 문서 스니핏을 모아서 하나의 API 문서로 생성.

6. API 문서를 HTML로 변환

- 생성된 API 문서를 HTML 파일로 변환
- HTML로 변환된 API 문서는 HTML 파일 자체를 공유할 수도 있고, URL을 통해 해당 HTML에 접속해서 확인
