# Chapter 19. Domain Name System(DNS)

<img src="CompNetwork_Ch19_1.png"/>

+ TCP/IP Protocol은 IP Address가 필요한데, 이런 복잡한 숫자 대신에 그냥 "이름" 을 사용하고 싶더라
+ name 을 address에 매핑하거나, address를 name에 매핑하는 등의 작업이 필요하다. 

### Name Space 

+ IP Address가 Unique하기 때문에, name도 그래야함. 
+ flat 과 hierarchical 한 방법 두가지가 있다.
  - flat : 구조없이 그냥 이름
  - hierarchical : 구조 있고, 다 따로 따로 되어있는게 조합된것. 

+ Tree 형식으로 가는 방법 : com.aaaa.bbbb. 이렇게되면 bbbb.aaaa.com 이렇게 되겠지.
  - Label : 최대 63개 char로 되어있는 node
  - domain name : 거꾸로 올라가면서 읽는 label의 조합. dot로 구분됨. 
+ 당연히 거꾸로 올라가면서 읽는다. 

+ FQDN & PQDN
  - FQDN(Fully Qualified Domain Name)
    - 전체 주소 도메인 네임, 절대 도메인 네임이라고 부르며, 호스트 이름과 도메인 이름을 포함한 "전체 도메인 이름"을 일컫는 용어이다.
    - host의 완전한 이름이다. 
    - 맨 뒤에 root domain(".")도 포함해야 하지만, 보통 도트까지는 생략함.

  - PQDN(Partially Qualified Domain Name)
    - 부분 주소 도메인 네임, 혹은 상대 도메인 네임이라고 부르며, DNS root의 모든 label을 포함하지 않는다. 
    - 단순히 호스트네임이라고 하며, 전체 주소 도메인 네임의 가장 왼쪽에 위치한 label 이다. 
