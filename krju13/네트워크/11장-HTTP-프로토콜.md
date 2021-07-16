## [HTTP 프로토콜](https://youtu.be/TwsQX1AnWJU?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)  

### 웹을 만드는 기술들
- http(https -> ssl/tls) 
- html 웹페이지를 채울 내용
- javascript 웹 페이지에 들어갈 기능
- css 웹 페이지를 예브게 꾸밀 디자인  
- asp/asp.net
- jsp
- php 이거 세개는 서버에서 동작하는 것, 웹 서버 페이지를 만드는 기술
- db     
- python
- spring
- Jquery
- Ajax

### HTTP 프로토콜의 특징
- HyperText Transfer Protocol(하이퍼 텍스트 전송 프로토콜)  
- www에서 쓰이는 핵심 프로토콜로 문서의 전송을 위해 쓰이며, 오늘날 거의 모든 웹 애플리케이션에서 사용되고 있다.   
    -> 음성, 화상 등 여러 종류의 데이터를 MIME로 정의하여 전송 가능
  
- HTTP 특징  
    Request/ Response(요청/ 응답) 동작에 기반하여 서비스 제공
  
HTTP 1.0의 특징
- "연결 수립, 동작, 연결 해제"의 단순함이 특징 -> 하나의 URL은 하나의 TCP연결
    HTML 문서를 전송 받은 뒤 연결을 끊고 다시 연결하여 데이터를 전송한다.
  
- HTTP 1.0의 문제점   
    단순 동작(연결 수립, 동작, 연결 해제)이 반복되어 통신 부하 문제 발생
    매번 TCP 3way handshake 를 하고 또 HTTP 요청에 대한 응답을 받으면 연결을 끊어서 다시 처음부터 반복해야했다.
  
 HTTP/1.1  
한번연결 하면 받을 꺼 다 받고 연결을 종료하라는 의미  





## [HTTP 요청 프로토콜](https://youtu.be/rxaBwwI_JnI?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)
### 요청 프로토콜의 구조
![11HTTP구조](./img/11HTTP구조.png)
- HTTP Method 설명 중 GET, POST만 사용해야 한다고  
  하지만 개발자 입장에서  
  RESTful API 개발시 PUT, DELETE도 사용하는게 원칙임
  
리퀘스트 라인 : 요청타입 공백 URI 공백 HTTP버전

### 요청타입
- GET 문서를 읽어오려 할 때 사용
- POST 클라이언트가 데이터를 원할 때 
- PUT 특정자원 업로드할 때 
- Delete 제거할 때 


## [URL, URI란?](https://youtu.be/2ikhZ_fNP5Y?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)
URI(Uniform Resource Identifier)  
- 인터넷 상에서 특정 자원을 나타내는 유일한 주소  
scheme://host[:post][/path][?query]  
  ex) ftp://IP주소:포트/파일이름  
  ex) http://IP주소:포트/폴더이름/파일이름  


## [HTTP 요청 프로토콜 작성 실습](https://youtu.be/XbGJYsxed2w?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

...


## [URI 이해를 위한 실습](https://youtu.be/HBojczyd1Ac?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- 

## [HTTP 응답 프로토콜](https://youtu.be/kuucNF4Zvbs?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- 

## [HTTP 헤더 포맷](https://youtu.be/mQTGmxendk8?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- 

## [HTTP 프로토콜 분석 실습](https://youtu.be/dhMrKTwNI8U?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

-