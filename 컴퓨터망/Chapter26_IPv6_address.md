# Chapter 26. IPv6 Addressing

+ IPv6 Address는 32 bit가 아닌 128bit 짜리 Address이다.
+ 32 bit로 하면 다 해봐야 48억개인데, 인구는 지금 70억 가까이 된다. 
  - 문제를 해결하려고 나온 것이 IPv6 이다. 

+ Colon Hexadecimal Notation 
  - 16진수로, 4bit 씩 4개씩 자르고, Colon 붙여서 구별함

+ Zero Compression 
  - 0 부분을 다 Compression 해서 압축한다 
  - ex) FDEC:0:0:0:0:BBFF:0:FFFF -> FDEC::BBFF:0:FFFF
    - 0 부분이 :: 로 다 압축되었다. 
    - :: 사이에 0이 다 있다는 것. 
  - 연달아 있는 colon은 반드시 한 쪽만 있으면 안된다. 
    - 연달아 있는 colon 이 두개 있으면 어디에 다 128bit 에 맞게 채울 수 없다. 
    - 0 은 가급적 안쓰는 것으로 해서, 효율적으로 표기할 수 있다.
    
+ CIDR Address
  - ex) FDEC::BBFF:0:FFFF/60
  - 앞부분 60bit가 Network Prefix 라는 의미(슬래시 뒤 60)
    - Routing 할때 앞 60bit만 보면 되는 의미
    
  - 당연히 prefix length는 128bit 까지 가능하다. 
  
+ 압축 예시
  - 0000:0000:0000:0000:FFFF:FFFF:FFFF:FFFF -> ::FFFF:FFFF:FFFF:FFFF
  - 0000:0000:0000:0000:0000:0000:0000:0000 -> ::
  - FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF:FFFF -> 압축해도 똑같다 
  - AAAA:AAAA:AAAA:AAAA:AAAA:AAAA:AAAA:AAAA -> 압축해도 똑같다. 

+ 맨 끝부분에 Version 4 Address가 오기도 한다
  - Version 6와 Version 4가 혼재되어 있기 때문에, 맨 끝부분에 Version 4가 오기도 하게 만들었다.

+ 푸는 예시
  - 1111::2222 -> 1111:0000:0000:0000:0000:0000:0000:2222
  - :: -> 0000:0000:0000:0000:0000:0000:0000:0000
  - 0:1:: -> 0000:0001:0000:0000:0000:0000:0000:0000
    - 1이라고 그냥 되어있으면 0001 이다
  - AAAA:A:AA::1234 -> AAAA:000A:00AA:0000:0000:0000:0000:1234  
  
### ADDRESS SPACE ALLOCATION

<img src="CompNetwork_Ch26_1.png"/>

+ 128bit를 8분의 1씩 쪼개어 보는 것
+ 왼쪽 오른쪽은 Reserved 나 특별 Address
+ 2번째 block이 Global Unicast 이다. 
+ 나머지는 안쓰고 있다. 안써도 충분히 남아돈다. 
  - 주소 Range가 엄청나고, 이중에 일부만 할당을 해 놓았다. 
  
   
    
