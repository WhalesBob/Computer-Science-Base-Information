# Chapter 28. ICMPv6

<img src="images/CompNetwork_Ch28_1.png"/>

+ ICMPv4 에서는 IP 위에 IGMP, ICMP, 아래에 ARP 가 있었는데, version 6로 넘어오면서 IGMP, ICMP, ARP를 하나로 합침.
+ ICMPv6 = IGMP + ICMP + ARP

+ ICMPv6 Msg의 종류
  - Error Message
  - Informational Message(v4에서의 Query)
  - Neighbor discovery Message(ND Protocol)(v4에서의 ARP)
    - ARP라는 것은 해당 IP 쓰는 애의 MAC주소가 무엇인지 팡가하는 것이었다.
    - Neighbor Discovery Protocol 도 마찬가지고, 주변에 있는 애들이 무엇인지 파악하는 Protocol 이다.(굳이 Address 따질 것 없이)
  - Group Membership Message(MLD Protocol)(v4에서의 IGMP)
    - IGMP : Multicast 할 때, Multicast Router로 하여금 해당 사실을 인지시킨 것 
    - 이름이 MLD(Multicast Listener Discovery) 로 바뀌었다. (Multicast 듣고 있는 애를 파악하겠다는 의미)

### ERROR MESSAGE

+ Error-reporting Message
  - Destination Unreachable
  - Time Exceeded
  - Parameter Problems
  - Packet Too Big

