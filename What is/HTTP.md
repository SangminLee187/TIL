# HTTP(Hyper Text Protocol)
```
그래도 백엔드 개발을 꿈꾸는데 HTTP에 대해 한번쯤은 제대로 정리하고 가야하지 않을까..
하는 마음에 얼추 알고 있던 내용에 정확한 정보를 얻어 정리해보기위해 작성
```


## 개념
* 서버와 클라이언트간 메시지교환 프로토콜
* 클라이언트가 요청(Request)하면 서버는 응답(Response)하는 구조

### 프로토콜(Protocol)
* 네트워크기기 간 원활한 통신을 위한 약속

### TCP(Transmission Control Protocol)
* 트랜스포트 계층으로 Server와 Client 사이의 통신연결을 제어
* 바이트스트림 서비스제공
  - 큰 데이터를 작게 쪼개서 전송하는 서비스
* 3way handshaking
  - TCP통신을 이용해 데이터를 전송하기 위해 네트워크 연결을 설정하는 과정
  - 3번에 거쳐 요청, 요청+응답, 응답(응답+데이터 가능) TCP 접속(or연결) 과정을 가짐
  - 양쪽 모두 데이터를 전송할 준비가 되었다는 것을 알 수 있음.

### IP(Internet Protocol)
* 분할된 데이터 패킷(통신단위)을 서버로 전송
* IP 주소 = 논리주소 / Mac 주소 = 물리주소
* ARP(Address Resolution Protocol)
  - 논리적인 주소를 물리적인 주소로 변환하는 작업
  - 수신IP조사 - 도착MAC주소조사 - 경로확인
  - 서버 - 라우터 - 라우터 - 클라이언트

## DNS(Domain Name System)
* 도메인 이름 및 IP주소 확인 / 도메인이름을 IP주소로 변환 / 어떤 서버로 연결할지 제어
* URI(Uniform Resource Identifier)
  - 특정 리소스를 식벼하는 통합자원 식별자로 논리적 또는 물리적 식별을 하는 고유한 문자열 시퀀스 
* URL(Uniform Resource Locater)
  - 특성 서버의 한 리소스의 구체적인 위치를 서술
  - 흔히 사용하는 인터넷주소 _(<k>www<k>.naver.com 등)_

## HTTP 프로토콜
* Request 
  - 클라이언트가 서버로 하는 요청
  - 메소드, URI, 프로토콜 버전, 헤더, 바디로 구성
* Response  
  - 클라이언트의 요청에 서버가 클라이언트로 보내는 응답
  - 프로토콜, 상태코드, 상태코드설명, 헤더, 바디로 구성
* StateLess
  - 서버가 클라이언트의 상태를 보존하지 않는 방식
  - 상태가와 무관하기 때문에 확장성이 좋음
  - 로그인과 같이 상태유지를 하는 경우가 있으며 일반적으로 쿠키와 세션을 사용해 상태유지   
    (상태유지는 최소한으로)
* URI로 리소스 식별
  - URI에 포함 : ```GET http://www.forRest.com/board/10 HTTP/1.1 ```
  - HOST헤더에 포함 
    ```
    GET /board/10 HTTP/1.1
    Host:forRest.com
    ```
  - 와일드카드 지정 : ``` OPTIONS * HTTP/1.1```
* 지속연결
  
  

### 통신과정
*  C = Client / S =Server
*  C.HTTP - C.TCP - C.IP - C.Network - S.Network - S.IP - S.TCP - S.HTTP
