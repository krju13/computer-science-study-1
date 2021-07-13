## [UDP 프로토콜](https://youtu.be/3MkI3FBFzX8?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)
비연결지향형 UDP 프로토콜
### UDP가 하는 일
-  사용자 데이터 그램 프로토콜(user Datagram Protocal ,UDP)은 유니버설 데이터크램 프로토콜(
   Universal Datagram Protocal)이라고 일컫기도 한다.
    
- UDP의 전송 방식은 너무 단순해서 서비스의 신뢰성이 낮고, 데이터그램 도착 순서가 바뀌거나, 중복되거나, 심지어는 통보없이 누락시키기도 한다.

- UDP는 일반적으로 오류의 검사와 수정이 필요없는 프로그램에서 수행할 것으로 가정한다.

|1-2바이트|3-4바이트|
|---|----|
|source port |destination port|
|length|Checksum|

### UDP 프로토콜을 사용하는 프로그램
- DNS 서버 : 도메인을 물으면 IP를 알려준다.
- tftp 서버: UDP로 파일을 공유한다.
- RIP 프로토콜: 라우팅 정보를 공유한다.
   

## [tftpd로 파일 전송 실습](https://youtu.be/5Woau-EJChw?list=PL0d8NnikouEWcF1jJueLdjRIC4HsUlULi)

- udp 는 작은 파일이나 동영상 스트리밍에서 사용한다.