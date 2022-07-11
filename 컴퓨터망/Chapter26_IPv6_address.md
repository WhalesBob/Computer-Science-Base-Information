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
  
