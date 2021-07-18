### [HTTP 프로토콜](https://youtu.be/TwsQX1AnWJU?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- **Hyper Text Transfer Protocol**

#### 웹을 만드는 기술들

- **HTML, Javascript, CSS 등의 파일**을 **서버로부터 받아오는 프로토콜**
- HTTPS -> 보안이 추가되었습니다.
- **ASP/ASP.NET**, **JSP**, **PHP** -> **서버 쪽**에서 활용하는 것들
- DB

#### HTTP 프로토콜의 특징

- www에서 쓰이는 핵심 프로토콜
- 문서의 전송을 위해 쓰이며, 오늘날 거의 모든 웹 application에서 사용되고 있습니다.
- 음성, 화상 등 여러 종류의 데이터를 MIME로 정의하여 전송 가능
  - MIME: Multipurpose Internet Mail Extensions
    - 전자우편의 데이터 형식을 정의한 표준 포맷
    - 여러 **멀티미디어 데이터**들의 바이너리 데이터를 **ASCII 코드로 변환하는 방법**과 미디어 종류를 **MIME 타입 목록으로 정의**하였습니다.
- Request / Response 동작에 기반하여 서비스 제공
- HTTP 1.0의 특징
  - **단순함**
  - **네트워크 부하가 심합**니다. (매번 3Way Handshake...)
- HTTP 1.1 
  - 처음에 3Way Handshake를 진행합니다.
  - 이후에 **모든 요청 응답을 처리**하고 **연결을 종료**합니다.
  - 1.0을 개선했습니다.

### [HTTP 요청 프로토콜](https://youtu.be/rxaBwwI_JnI?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- HTTP Method 설명 중 **GET, POST**만 사용해야 한다고 하지만 개발자 입장에서 **RESTful API** 개발시 **PUT, DELETE도** 사용하는게 원칙임
- 요청 프로토콜 구조
  - 아래 그림과 같이 생겼습니다.
    <img src="imgs/11_http_request.png" style="zoom:50%;" />
  - Request Line 구조
    <img src="imgs/11_request_line.png" style="zoom:50%;" />
  - **GET, POST, PUT, DELETE** 중요 (HTTP 메소드)
- GET과 POST 방식의 차이
  - GET은 **url**에 -> **중요한 정보가 아닌**경우
  - POST는 **body**에 -> 중요한 정보의 경우 (**body**에 데이터를 추가하기 때문에 **다른 사람이 볼 수 없**다.)

### [URL, URI란?](https://youtu.be/2ikhZ_fNP5Y?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- **URI**: 인터넷 상에서 **특정 자원(파일)**을 나타내는 **유일한 주소**
  - `scheme://host[:port][/path][?query]`
    - `scheme`: 7계층 프로토콜을 작성한다고 생각하면 됩니다.
    - `host[:port]`: ip 주소와 port 번호를 직접쓰기 보다는 **도메인 주소**를 작성합니다.
      - 특히 port 번호는 웹 브라우저가 알아서 처리 해줍니다. (80 혹은 443)
    - `/path`: 파일 경로

### [HTTP 응답 프로토콜](https://youtu.be/kuucNF4Zvbs?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- 아래 사진은 http 응답 프로토콜의 구조입니다.
  ![](imgs/11_http_response.png)

- 아래 사진은 **Status Line**의 구조입니다.
  ![](imgs/11_response_status_line.png)

- 상태 코드

  | 상태 코드 종류 |설명|
  | :------------: | :------------: |
  | 100 ~ 199 |단순한 정보|
  | 200 ~ 299 |Client의 요청이 **성공**|
  | 300 ~ 399 |Client의 요청이 수행되지 않아 다른 URL로 재지정|
  | 400 ~ 499 |Client의 요청이 불완전하여 다른 정보가 필요 (**Client의 잘못**), 403->forbidden, 404->not found|
  | 500 ~ 599 |Server의 오류를 만나거나 Client의 요청 수행 불가 (**Server의 잘못**), 500->internal server error, 503->service unavailable(최대 session 수를 초과했을 때)|


### [HTTP 헤더 포맷](https://youtu.be/mQTGmxendk8?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- 일반적인 정보를 담고 있는 **일반 헤더**

  |   헤더 종류    |설명|
  | :------------: | :------------: |
  | Content-Length |**메시지 바디 길이**를 나타낼 때 쓰인다.|
  | Content-Type |메시지 바디에 들어있는 **컨텐츠 종류** (Ex: HTML 문서는 **text/html**)|

- 클라이언트 정보를 담고 있는 **요청 헤더**

  | 헤더 종류 |설명|
  | :-------: | :-------: |
  | Cookie    |서버로부터 받은 쿠키를 다시 서버에게 보내주는 역할을 한다.|
  | Host |요청된 URL에 나타난 호스트명을 상세하게 표시 (HTTP 1.1은 필수)|
  | User-Agent |Client Program에 대한 식별 가능 정보를 제공|

- 서버 정보를 담고 있는 응답 헤더

  | 헤더 종류 | 설명 |
  | :-------: | :-------: |
  | Server |사용하고 있는 웹서버의 소프트웨어에 대한 정보를 포함|
  | Set-Cookie |쿠키를 생성하고 브라우저에 보낼 때 사용, 해당 쿠키 값을 브라우저가 서버에게 다시 보낼 때 사용|


### [HTTP 프로토콜 분석 실습](https://youtu.be/dhMrKTwNI8U?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- Burf Suite: 브라우저 혹은 서버가 보내는 **요청 및 응답을 잠시 캡처**하고 **확인 또는 수정 후 원래의 목적지로 해당 데이터를 보냅**니다.

