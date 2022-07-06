# Chapter 16. Stream Control Transmission Protocol(SCTP)

+ SCTP(Stream Control Transmission Protocol) 은, 신뢰할 수 있는, 메세지 지향 transport-layer protocol 이다. 
+ SCTP는 UDP와 TCP 의 좋은 점만 취했다!
  - TCP의 좋은 점만 취하고, 안 좋은 것은 다 뺐다.
  - UDP에서는 메세지 기반인 것만 따왔다고 한다. 
  - 기본 단위를 byte가 아닌 packet 단위로 했다.
    - 어차피 패킷이 왔냐가 중요하지 몇 byte인지는 그렇게 중요하지 않다.
    
  - 실제로 쓰이고 있는데, 데스크탑이나 노트북 PC에서는 안 쓰인다고 한다. 
    - 이미 되어 있는 기존 응용을 바꾸기가 쉽지 않았다고 함. 
    - 기존 TCP/UDP로 짠 것을 바꾸려면, 분명히 이유가 있어야 해서 그렇다. 
    - 서버급 통신(SKT 망 같은 사업자 망, 큰 장비들끼리) 에서는 많이 쓰인다. 
    
### SCTP Services

+ SCTP가 들어가는 기능을 보면 TCP가 들어가는 애와 큰 차이가 없다. 
    - Process to Process Communication
    - Full Duplex Communication
    - Connection-Oriented Service
    - Reliable Service
    - Multiple Stream(TCP에 없음)
    - Muitihoming(TCP에 없음)
    
<img src="images/CompNetwork_Ch16_1.png"/>    
    
+ Multiple Stream 
  - TCP는 Single Stream인데 반해 SCTP는 Stream Pipe 여러 개를 열어서 일을 처리할 수 있다. 
  - Packet 내에서 Stream을 구분하는 ID가 존재한다.(중요)
  - 왜 Multiple-Stream이 필요했나?
    - TCP의 경우, 모든 데이터가 Stream 한개로 가니까, 하나만 loss 나도 그 뒤에 복구하느라고 뒤에 것의 진도가 나가지 않는다. ALL STOP 때리고 복구하는 것임.
    - 데이터 내용을 보면, 한명 것이 아니라 여러 명 것이다보니, 보내는 내용이나 받는 사람 등에 따라 여러 개로 분리해 놓아서 Stream을 보내면, 한개가 loss가 나더라도 나머지 n-1 개의 stream에서는 문제가 없이 보내질 수 있다. 
    - TCP는 Stream 하나에서 하나만 loss 나도 뒤에 것들이 다 죽음. 이것을 극복하려고 나온 것이 multi-streaming 이다!
    
  - 두 컴퓨터가 통신을 하는데, TCP는 파이프가 한개, SCTP는 여러개이다.
  - 컨텐츠를 분리해서 보내는 것이다. 
  - Stream ID 정보가 Packet에 포함되어 있음. 
  - 하나가 에러가 생겨 복구하는데 많은 시간을 쓰는 것보다, 하나가 loss 나도 나머지를 잘 보낼 수 있게 한다!
  
+ Stream 이 여러개 이다 보니, TCP에서는 단순히 Connection 이라고 부르는데, SCTP에서는 Association 이라고 부른다.(Association이라고 부른다!)
+ Port 는 한개지만, IP 주소는 여러개를 쓴다!   
    
<img src="images/CompNetwork_Ch16_2.png"/>    
    
+ Multihoming 
  - Home 이 여러개이다! Address 를 두개 이상 쓴다. 
    - TCP/UDP 는 Adress를 한개만 썼는데, SCTP는 Address를 여러 개 사용할 수 있다!(Port는 한개인데도 불구하고)
    - Address 가 두개라는 이야기는, router가 두개일 수 있다는 이야기.
    - 만약에 한쪽 route가 막히면, 다른쪽으로 보낼 수 있을 것이다!
    - router가 두개 이상 물려있다 보니, 한쪽이 많이 안좋으면, 다른 쪽으로 연결해서 쓸 수 있다!
    - 통신할 때는 하나만 쓴다.(Primary Path) 
    - 문제가 생기면, 다른 쪽으로 넘어가 쓴다.(Secondary Path, Backup Path)
    - 문제가 생기면, Secondary Path로 Switching 해서 쓴다. 그럴려고 Router 를 여러 개 붙이는 것이다. 
    
+ Multiple Stream 과 Multihoming 두가지가 성능을 급격히 올려줄 수 있다!
+ 위의 2가지와 Message 기반 으로 하는 것이 SCTP
+ 사용예시
  - 인터넷 전화(SIP) : 인터넷 전화의 응용 계층 프로토콜을 TCP가 아닌 SCTP를 사용한다. 
  - 계산 정보나 보안 정보는 반드시 도착해야 하기때문에, SCTP를 사용한다.
  - 사업자 망에서는 TCP 로는 이제 어림도없다고 한다. 
    - Multi Streaming : 수만명의 Call 정보가 몰려 있는데, Call 마다 Stream을 하나씩 줄 수 있다. 
    - 1명이 Loss 되어도, 9999명의 것을 잘 처리할 수 있을 것이다. 
    - Multihoming : 만약에 한 데이터가 없어지면, 바로 복구해야 함. 다시 끊었다가 TCP 연결하면 시간이 별로 없다. 
  - end 급 유저가 아닌, 서버 통신에서 주로 사용된다!
  
  + TCP 와의 추가적인 차이점 
    - TSN(Transmission Sequence Number) : Byte 단위로 전송하는 것이 아닌, packet 단위로 전송해 보낸다. 
    - SI(Stream Identifier) : Stream ID가 다 할당이 되어 있다. 
    - SSN(Stream Sequence Number) : Stream 내에서도 순서가 있다!
    - Packets : TCP에서는 Segment 라고 했지만, SCTP 에서는 그냥 Packet이라고 부른다. 
