# Chapter 8. Address Resolution Protocol(ARP)

### Address Mapping

+ 같은 Layer(L3)이기는 함.
+ IP Header를 쓰지 않고, MAC Layer(Physical Adress)와 직접 통신하는 Protocol.
+ IP Address / MAC Address 가 있으면, Router는 어떤 IP가 어떤 MAC Address 와 Mapping 되는지 알아야 함. 
  - 이 Mapping 정보를 알아내는 것이 ARP가 하는 역할이다! 
  - arp -a 를 cmd 에 입력하면, 같은 LAN 안에서 IP와 MAC Mapping 정보를 알아올 수 있다.

<img src="images/CompNetwork_Ch8_1.png"/>

+ ARP가 어떻게 동작하는지?
  - System A 에서 IP Addressfh Request를 해당 네트워크의 모든 애들한테 다 보낸다(Broadcast). 
  - 이후, 그 IP를 사용하는 컴퓨터가 응답하며(물론 응답 안할수도 있음), unicast로 arp로 reply
  - 이런 과정들이 수시로 컴퓨터들 사이에서 주고받게 된다. 
  - request 이후 reply!
  
<img src="images/CompNetwork_Ch8_2.png"/>  

+ ARP Packet의 format
  - 위 그림의 분홍색 부분을, 처음 reply에서는 빈칸으로 만들어 보낸다. 
  - 응답할 때는 채워서 보내주는 것임. 
  - 이런 식으로 상대방의 IP와 MAC
  - 이 ARP 자체는 IP Header를 쓰지 않는다!
    - L2 Frame에서는 IP Header가 없음. L2 Frame 안에 ARP가 바로 들어간다고 한다. 
    - 어차피 MAC 주소를 몰라서 못쓰는 것도 있음.

<img src="images/CompNetwork_Ch8_3.png"/>  

+ ARP 쓰는 4가지 case
  - Host - Host
  - Host - Router
  - Router - Host
  - Router - Router

+ ARP 주고받는 Example

<img src="images/CompNetwork_Ch8_4.png"/>   

+ Proxy ARP

  - <img src="images/CompNetwork_Ch8_5.png"/> 
  
  - Proxy : 위임받는다 라는 한글 뜻이 있다. 
  - ARP 기능을 위임받아서 다른 애가 대신 해준다. 
  
  
