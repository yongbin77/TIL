
## API 문서화

>API 문서화란 클라이언트가 REST API 백엔드 애플리케이션에 요청을 전송하기 위해서 알아야 되는 요청 정보(요청 URL(또는 URI), request body, query parameter 등)를 문서로 잘 정리하는 것을 의미


### Spring Rest Doc 장점

>Spring Rest Docs를 사용한 API 문서화의 대표적인 장점은 테스트 케이스에서 전송하는 API 문서 정보와 Controller에서 구현한 Request Body, Response Body, Query Parmeter 등의 정보가 하나라도 일치하지 않으면 테스트 케이스의 실행 결과가 “failed” 되면서 API 문서가 정상적으로 생성이 되지 않는다.
>즉, 테스트 케이스의 실행 결과를 “passed”로 만들지 않으면 API 문서 생성이 완료되지 않는다.
>테스트 케이스의 실행 결과가 “passed”이면 Controller에 정의되어 있는 Request Body나 Response Body 등의 API 스펙 정보와 일치하는 API 문서가 만들어진다.
