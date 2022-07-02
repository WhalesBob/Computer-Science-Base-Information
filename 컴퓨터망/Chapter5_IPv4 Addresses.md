# Chapter 5. IPv4 Addresses


### Introduction

+ IP Address는 모든 컴퓨터에서 Unique하게 다 얻을 수 있어야 한다. 그래야 Global 하게 어떤 것이 어떤 컴퓨터인지 파악할 수 있다.
+ IPv4 Address는 32bit 길이의 IP 주소이다.
+ 지구상에서 IPv4로 가져갈 수 있는 IP 주소의 갯수는 대충 42억개이다.
  - 지구상의 인구는 7~80 억인데 비해, 42억개의 주소는 모자란다.

<img src = "images/CompNetwork_Ch5_1.png" />

+ 1byte 하나가 10진수로 대응이 된다!(4byte의 주소에서)
  - 숫자 하나당 8 bit이다!
  - 0~255 사이의 숫자가 올 수 있다.
  - 틀린 주소 잡아낼 수 있어야 함!

### Classful Addressing

+ 지구 상의 IP 주소들을 Class A,B,C,D로 쪼개 놓았다.

<img src = "images/CompNetwork_Ch5_2.png" />
