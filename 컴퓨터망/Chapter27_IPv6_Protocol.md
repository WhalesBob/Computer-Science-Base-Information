# Chapter 27. IPv6 Protocol

### PACKET FORMAT

<img src="images/CompNetwork_Ch27_1.png"/>

+ IPv6 Datagram
  - Base Header Size : 40byte
    - V4는 20byte 에 옵션이 있어서 60byte까지 늘어날 수 있었음
    - v6에서는 40byte 고정. 하지만, Payload 에 Extension Header가 존재한다. 
    - Extension Header가 v4 에서의 Option 과 같은 비슷한 역할을 한다. 
  
  - Extension Header 뒤에는 Data가 온다. 

<img src="images/CompNetwork_Ch27_2.png"/>

+ Format of the Base Header
  - 한 줄의 크기가 4byte(32bit)
  - VER(4bit) : 4라고 적혀 있으면 V4, 6이라고 적혀 있으면 V6
    - 버전정보가 15까지 올 수 있다. 
    
  - Traffic Class(8bit) : V4의 Type of Service 와 같은 개념
    - Type of Class가 V6에서는 이름으로 바뀌었다. 
    - 일반 사람들이 Traffic Class에 관해 쓸일은 거의 없고, Backbone 망에서 Deep Server 다룰 때 들어감. 
  
  - Flow Label(20bit) : 
    - 의도 : Flow가 Socket 과 비슷해서, 송수신자 간의 Port 로 정의되기도 함
    - Rule : 이 컴퓨터와, 멀리 있는 어떤 컴퓨터가 Flow가 연결되어 Flow-Control 하기 위해서 만들어짐. 
    

