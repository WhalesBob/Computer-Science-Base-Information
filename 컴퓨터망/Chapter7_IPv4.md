# Chapter 7. Internet Protocol Version 4(IPv4)

### Introduction 

+ Internet Protocol(IP)는, network layer(L3) 에서 진행되는 TCP/IP protocol 이 사용하는 Protocol이다.

<img src="images/CompNetwork_Ch7_1.png"/>

### Datagrams

+ Network Layer 상의 패킷을 보고 Datagram 이라고 한다.
+ Datagram은 헤더와 데이터 두 부류의 가변형 길이를 가지는 패킷이다.
+ header는 20~60 바이트 사이의 길이를 가질 수 있고, routing과 delivery에 필수적인 정보들을 담고 있다.
+ TCP/IP 에서는 헤더를 4 byte section 안에 나누는 것이 일반적이다. 

<img src="images/CompNetwork_Ch7_2.png"/>

+ IP Datagram의 구조
  - VER : IP 버전을 나타내기 위한 버전 영역.(4bit 차지)
  - HLEN : 4 byte를 기본 단위로 하는 헤더의 길이를 규정해 놓은 것. 헤더 크기.(4bit 차지)
    - HLEN = 5 : 5*4byte = 20 byte
    
  - Service Type : 네트워크를 통해 데이터를 전송하고자 할 때 사용자의 데이터마다 우선권을 부여할 수 있는, 그러한 것들을 표시해 놓은 것.(8bit 차지)
    - Routing 할때 중요하게 보는 것.
    - D,T,R,C
      - D : 지연시간 최소화
      - T : 처리율 최대화
      - R : 신뢰성 최대화
      - C : 비용 최소화

  - Total Length : 전체 패킷 길이. IP 데이터그램의 총 길이를 나타낸다. 
