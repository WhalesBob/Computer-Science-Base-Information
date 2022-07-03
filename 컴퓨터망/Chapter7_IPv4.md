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
    - Header의 크기가 20~60 byte 사이여야 하기 때문에, HLEN은 20/4 = 5. 5 보다는 커야 한다. 아니면 잘못된 정보이다. 
    
  - Service Type : 네트워크를 통해 데이터를 전송하고자 할 때 사용자의 데이터마다 우선권을 부여할 수 있는, 그러한 것들을 표시해 놓은 것.(8bit 차지)
    - Routing 할때 중요하게 보는 것.
    - D,T,R,C
      - D : 지연시간 최소화
      - T : 처리율 최대화
      - R : 신뢰성 최대화
      - C : 비용 최소화

  - Total Length(16bit) : 전체 패킷 길이. IP 데이터그램의 총 길이를 나타낸다. 
    - byte 단위!! 패킷의 끝이 어디인지를 확실히 알 수 있다.
    - Header를 더한, Datagram의 전체 Length.

  - Identification ,Fragmention, flag : fragmentation과 관련 있는 애들이다.
    - 패킷이 지나가는 네트워크가 다양하다.(이더넷, 이동통신, 블루투스 등).
    - 그러므로, 네트워크를 지나갈 때마다, 해당 네트워크마다 맞는 size가 존재한다.
    - MTU : Maximum Transmitting Unit
    - 처음에 2000byte를 보내도, 쪼개져서 여러 갈래로 나뉠 수가 있다. 그럼 도착하면 다시 정렬해줘야한다. 그와 관련된 정보가 2번째 줄에 있다. 

  - Identification : 16bit. 패킷의 id이다. 
    - 패킷 id가 있어야 그 뒤에 다시 합칠 때 아이디가 같은것들끼리 뭉칠 수 있다. ID 숫자는 65536개까지 가능함. 

  - Flag : 3bit. Fragmentation 되었는지 안되었는지 확인하는데 사용되는 애.
    - 실상은 2bit만 쓴다.
    - 처음에는 3bit 다 사용할 줄 알고 할당해 두었다고 하는데, 안써서 하나가 낭비되고 있다고 한다. 
    - 실제로 쪼개진 것인지 안된것인지/쪼개어도 되는지 안되는지 두 개를 나타낸다. 

  - Fragmentation Offset(13bit) : 
     - "차감하다" 라는 의미를 가지고 있다.
     - 쪼개었을때 상대적으로(3개로 쪼개었다고 가정하면), 첫번째 쪼갠 것인지 두번째 쪼갠것인지 그런내용을 가르쳐 준다. 
     - 그리고 다시 모았을때 몇 번째 fragmentation인지 가르쳐 주는 역할도 한다.
     - 패킷이 잘 쪼개지지는 않긴 하지만, 이동통신망 등을 이용할때나 v6로 가면 쪼개어서 보내기도한다. 

   - TTL(Time To Leave) : 패킷 생존기간. 8bit
     - 패킷이 얼마나 생존할 수 있는가를 가르쳐주는 애로, 몇 개의 hop을 지날 수 있는지 체크해주는애. 
     - 일정 수치 이상의 hop을 지나면 해당 패킷을 폐기한다.
     - Ex) TTL = 10 >> 11개째 HOP을 지나려고 하면 폐기된다. 수명을 다한 것이라고 보아도 된다.
     - 왜 수명을 정해두느냐?  : router에서 routing table이 바뀔때가 있다. 이때 packet 이 이동중이었다면 중간에 꼬일 수 있다. 이때 자칫 무한 loop 에 빠져 버렸는데, 이런 것들이 여러 수억 개 만들어 버렸다면, 망이 다운될 수 있다. 그래서 망 관리 차원에서 만들어 둔 것이다. 
     - 중간에 만약에 정말 Packet이 사라졌다면, ICMP라는 애가 일단 packet 을 없애버린 후, 어떤 이유 때문에 패킷이 없어졌다고 최초로 보낸 컴퓨터에게 알려주는 역할을 한다. 
     - 0부터 255까지 나타낼 수 있긴 하지만, 어지간하면 20개 이내에서 끊는다. 어지간하면 20개 이내에서 전달이 끝나기 때문. 이 hop 갯수가 넘도록 못 가고 있다는 이야기는 문제가 생겼다는 의미이다. 
     
  - Protocol(8bit) : TCP, UDP 등 어떤 Protocol을 사용하고 있는지 알려주는 애.
    - Protocol이 다 표준 번호가 있는데, 그 번호를 보고 어떤 Protocol이 사용되고 있는지 알 수 있다. 
  
  - Header Checksum(16bit) : Header 에 대해서 Checksum 해주는 애. 
    - 전부다 더한 후, 1의 보수 연산을 통해 나오는 숫자. 
    - Header에 있는 것을 전부다 더한 후, Checksum 까지 더한 합이 0이 나와야 하는데, 나오지 않으면 중간에 무엇인가가 바뀌었다는 것을 암시한다. 
    - 간단하게나마, 문제가 생겼는지 안생겼는지 파악할 수 있다. 
  
  - Source IP Address / Destination IP Address
  - Option : 들어갈 수도 있고 안들어갈수도 있음. 
          
+ Service Type : CodePoint라고 있는데, 지금은 잘 안쓰인다고 한다. 
  - 이 Packet의 Payload가 어떤 종류의 Service인지 알려줌. 
  
<img src="images/CompNetwork_Ch7_3.png"/>  

+ About Eternet Frame 
  - MAC에서 L2 Trailer, L2 Header가 있는데, 그 사이에 size가 보통 정해져 있다. 
  - 위의 그림에서 적혀 있는 46 byte. 저 값의 Maximum Size가 MTU(Maximum Transmitting Unit) 이다. 
  - 이동통신망은 MTU가 몇 byte인지, Ethernet은 MTU가 몇 byte인지 다 정해져 있다. 
  - 이 MTU 정보로 Fragmentation 할지말지 결정하는 것이다.
  
<img src="images/CompNetwork_Ch7_4.png"/> 

+ About Protocol Info in Packet 
  - Header 의 Protocol Field에서, 어떤 Protocol이 올 수 있는지 에 대한 부분.
  - TCP, UDP, ICMP, IGMP, OSPF 등 올 수 있다. 
  - 각 Protocol 마다 숫자가 정해져 있다. 
  - Header 내의 Protocol Field 정보를 바탕으로, Router도 해당 패킷의 Protocol 정보를 알 수 있음. 
 
+ 연습문제 
  - 01000010 은 에러이다
    - 0100 : Version 정보. 4면 ㄱㅊ
    - 0010 : 최소한 Header Length 가 5 이상으로 나와야 하는데, 2면 안된다. 2면, header length가 2*4 = 8byte라는 소리다. 에러라서 폐기.
    
### Fragmentation

+ Network 마다 MTU 정보가 있어서, 그것에 따라서 Packet이 쪼개질 수 있다!(Fragmentation)
+ MTU :
  - 위의 그림에서 적혀 있는 46 byte. 저 값의 Maximum Size가 MTU(Maximum Transmitting Unit) 이다. 
  - 이동통신망은 MTU가 몇 byte인지, Ethernet은 MTU가 몇 byte인지 다 정해져 있다. 
  - 이 MTU 정보로 Fragmentation 할지말지 결정하는 것이다.
  - MTU에 맞출려면, Packet을 쪼갤 수 밖에 없음. 그렇게 Packet을 쪼개는 것이다. 
  - 물론 Header값은 쪼개질 수 없다. Data 부분만 쪼개진다고 생각하면 된다. 
  - Data 길이가 MTU 보다 클 때 쪼개는 것이다. 
   
<img src="images/CompNetwork_Ch7_5.png"/>  
  
+ Flags Field
  - D(DO NOT) : 쪼개어도 되는지 안되는지? 
    - 쪼개지면 의미가 사라지는 경우, 1로 표기 해 둔다.
    - 만약에 쪼개어야 하는 상황인데, 쪼개지 말라고 표기된 경우, 해당 Packet을 없애버리고, 발신 컴퓨터에 알려준다. 
    - 보내는 애가 이 D 값을 세팅한다. 
  - M(More) : 1로 세팅 된 경우. "쪼개졌다!" 라는 것을 의미한다. 
    - M 값이 1이라는 이야기는, 뒤에 정보가 더 있다는 의미이다. 
  
  - 해당 값은 11이 올 수 없다.
    - 1이 쪼개지 말라는 의미인데, 뒤에 1은 쪼갰다는 의미이니까, 오면 에러이다. 
   
  - 반면, 당연히 00은 올 수 있다. 
    - 쪼개어도 된다고 해 두었는데, 쪼갤 필요가 없어서 00이 올 수 있다. 

<img src="images/CompNetwork_Ch7_6.png"/> 

+ Fragmentation Example 
