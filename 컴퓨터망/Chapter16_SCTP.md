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
    - 데이터 내용을 보면, 한명 것이 아니라 여러 명 것이다보니, 
    
