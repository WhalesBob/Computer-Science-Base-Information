# Chapter 7. Internet Protocol Version 4(IPv4)

### Introduction 

+ Internet Protocol(IP)는, network layer(L3) 에서 진행되는 TCP/IP protocol 이 사용하는 Protocol이다.

<img src="images/CompNetwork_Ch7_1.png"/>

### Datagrams

+ Network Layer 상의 패킷을 보고 Datagram 이라고 한다.
+ Datagram은 헤더와 데이터 두 부류의 가변형 길이를 가지는 패킷이다.
+ header는 20~60 바이트 사이의 길이를 가질 수 있고, routing과 delivery에 필수적인 정보들을 담고 있다.
+ TCP/IP 에서는 헤더를 4 byte section 안에 나누는 것이 일반적이다. 

