HTTP 요청에는 '메소드'라는 개념이 있습니다. 앞 투썸플레이스에서는 리소스를 그저 달라고(GET) 요청했지만, 사용자 관리 API에서는 사용자를 추가해달라고 (CREATE)하거나, 지워달라고 (DELETE)요청할 수 도 있습니다. 마치 CRUD행동과 비슷합니다. CRUD는 각각의 행동과 일치하는 HTTP 메소드의종류가 존재합니다. HTTP메소드는 리소스를 이용해 하려는 행동에 맞게 적절하게 사용해야합니다.

## 브라우저 작동원리 (눈에 보이지 않는 공간)

URL과 URI 브라우저 주소창에 입력한 URL은 '서버가 제공되는 환경에 존재하는 파일의 위치'를 나타냅니다. 사용자는 슬래시(/)를 이용해 서버의 폴더에 진입하거나 파일을 요청할 수 있습니다.
- URL: 웹페이지,이미지, 동영상등의 파일이 위치한 정보 URL의 구성요소는 Scheme,hosts,url-path등으로 구성되어 있습니다 . 가장먼저 작성하는 Scheme는 통신방식 (프로토콜)을 결정합니다. 일반적인 웹페이지는 http(s)를 사용합니다 hosts는 웹서버의 이름,도메인,IP를 사용해 주소를 나타냅니다. URI-Path는 웹서버에서 지정한 루트 디렉토리부터 웹이미지,동영상 등이 위치한 파일명과 경로를 나타냅니다.

- URI는 이 3개를 포함한것과 더불어 query, Bookmark를 추가적으로 포합합니다.(query란 웹서버에 보내는 추가적인 질문)

> IP 특정 PC의 주소를 IP라 합니다. 인터넷에서 사용되는 주소체계는 네덩이의 숫자로 구분됩니다. 이러한 IP체계를 IPV4라 합니다,사용되는 컴퓨터가 많아져 IPV6까지 발전되었습니다.

- localhost : 현재 사용중인 로컬pc 지칭 ex) 255.255.255.255 로컬 네트워크랑 접속한 모든장치와 소통하는 주소입니다.

- port: 예시를 통해 설명하겠습니다. 우리가 회사 서버에 접속한다고 할떄 ,그 서버는 웹서버 말고도 mysql, Dns, ssh등의 서비스를 제공합니다 ip/port번호를 입력하면 서버가 제공하는 서비스에 맞는 서비스를 찾아갑니다. 255,255,255.255+ port 80 (웹서비스 안내)
