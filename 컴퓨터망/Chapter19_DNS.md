# Chapter 19. Domain Name System(DNS)

<img src="images/CompNetwork_Ch19_1.png"/>

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

<img src="images/CompNetwork_Ch19_2.png"/>

+ Domain 
  - Domain 안에 Domain이 들어갈 수 있는 구조이다. 그냥 tree 구조 상에서 묶음이면 다 domain 이다.

+ Distribution of Name Space
  - 하나에만 다 넣고 관리할려니까, 너무 방대하다. 
  - 하나만 failure 나도 전체 인터넷이 망가질 수 있다. 
  - 그래서, DNS Servers 들을 분산시켜서 역시 똑같이 Tree 구조로 관리할 수 있다. 
  - DNS는 작은 domains(subdomain)들로 나뉘어지고, 계속 tree 처럼 아래로 내려가면서 관리될 수 있다.

<img src="images/CompNetwork_Ch19_3.png"/>
  
+ Zone  
  - domain name들이 모여 있는 전체 .com 이런 애들은, 서버 하나로 관리가 안된다. 
  - 그래서 많은 서버들로 나뉘어져 있다. (하나의 node인데도 불구하고)
  - 그래서 domain 이 더 나눌 수 있는 domain 이며, 여러 개로 되어 있으면 domain=zone
  - 나눌 수 없으면 domain != zone
  
+ Primary and Secondary Servers

  - primary server는 디스크 파일에서부터 모든 정보를 load 해 옴
  - secondary server는 primary server로부터 모든 정보를 가져 옴.
  - secondary 가 primary로부터 정보를 갖고오는 것을 보고 zone transfer 라고 부른다. 

### DNS IN THE INTERNET

<img src="images/CompNetwork_Ch19_4.png"/>

+ DNS used in the Internet
  - Generic Domain
    - 아래에서부터 위로 읽어나간다. 그렇게 root 까지 접근함
    - 그냥 맨 끝에 오는 애들이 다르다. 
  - Country Domain
    - 마찬가지!
    - country domain 이다보니, 맨 끝에 오는 애들이 으레 국가이다.
  - Inverse Domain
    - <img src="images/CompNetwork_Ch19_5.png"/>
    
    - 숫자가 앞에 오고, 그다음에 root로 갈수록 다시 기존 domain 처럼 name 가지면서 올 수 있다. 

### RESOLUTION

+ Resolution : 
  - name을 address에 매핑시키거나, address를 name에다가 mapping 시키는 것을 보고 name-address resolution 이라고 부른다.

<img src="images/CompNetwork_Ch19_7.png"/>

+ Recursive Resolution
  -  최종적인 답을 찾아갈 때까지 recursive 하게 resolution을 찾아가는 것
  
<img src="images/CompNetwork_Ch19_8.png"/>  
  
+ Iterative Resolution 
  - Recursive하게 안 가면, 반복적으로(iteratively) mapping할 수도 있다. 
  - 만약에 server에 name에 대한 authority가 있으면, 바로 답을 보내줄 것이다. 
  - 아니면, 이것을 해결해 줄 수 있다고 믿는 서버의 IP주소를 다시 준다. 
  - 반복적으로 찾게 된다.

### DNS MESSAGES

+ query 와 response. 두 가지 타입의 메세지를 주고받을 수 있다. 

<img src="images/CompNetwork_Ch19_6.png"/>

+ query message는 header와 question record 가 들어감
+ response message는 header, question record, answer record, authoritative record, additional record가 온다. 

<img src="images/CompNetwork_Ch19_9.png"/>

+ Header format

### ENCAPSULATION

+ DNS는 응용계층인데, TCP를 쓰는가 UDP를 쓰는가?
  - 서버가 일단 UDP를 하고, 응답할게 많아서 512byte가 넘고 있는것 같으면 TCP로 전환
  - 512byte보다 작으면 UDP, 넘어가면 TCP
  
### DDNS

+ DDNS(Dynamic DNS)
  - 보통 DNS는 static이다. 너무 자주 바뀌면 혼란을 줄 수 있기 때문
  - 가끔씩 바꿔야 할 때가 있다.(name 등록을 자주 하는것)
  - 보안 때문에 정보를 바꿔서 주기도 함. 

### SECURITY OF DNS
  - 만약에 해커들이 경북대 name server 3개 다 무너뜨리면, 통신 안되는 것임. 
  - DNS를 방어하기 위해, security를 강화해서 나온 것이 DNS Security(DNSSEC)
    - IETF 표준이다. 
    
