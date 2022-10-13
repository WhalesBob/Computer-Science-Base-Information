# Chapter 3. Introduction to Computing Systems

### Schematic Overview of Computer System

<img src="image/Ch3_1.png"/>

#### 위 그림에 대한 설명

+ 색상 설명
  - 파랑 네모 : Memory
    - Device에 붙어 있는 Memory는, 해당 device를 controll 하기 위한 정보도 메모리에 포함되어 있다. 
  - 빨강 네모 : register
  - Green Circle : Processing Unit(Controller)
  - 보라색 선 : System Bus

+ mode bit(Register) : 컴퓨터가 동작할 때 2가지 mode가 존재한다
  - CPU 권한을 누가 가지고 있냐에 따라 mode가 달라진다
  - mode bit 1(User Mode) : User가 CPU 권한을 가지고 있을 때, User Program이 돌게 된다. 
  - mode bit 0(Kernel Mode) : CPU에 대한 권한을 OS가 가지고 있을 때이다. 
  - 이렇게 나눈 이유 
    - 컴퓨터 OS는 관리해야 할 것이 많은데, User 에게 이런 Resource 고나리를 모두 일임했을 때 문제가 발생할 수 있다. 
    - 이런 접근(Critical 한 동작)들을 OS 가 관리하는 것이다. 
    - OS가 사전에 약속된 동작들을 수행하게 된다.(Protecting)
    
+ Timer : Time-Sharing 을 위한 시간을 hardware 적으로 측정해 주는 것.(hardware)
  - Computer 가 시간에 대한 정보가 필요할 때, Timer로부터 알 수 있음. 
  - Interactivce Computing 을 만들기 위해서 Time-Sharing System 이 필요하다. 
  - Timer 에서 1초가 지나면, Operating System 에서 mode bit을 0으로 돌리고 Context Switching 해줌.

+ I/O Device : 모니터, 프린터, 키보드 등
  - 이 I/O Device 내에도, Device Controller 와, 내부의 local buffer가 들어 있음.  
    
+ 휘발성 메모리(Volatile Memory) : 전원을 끄면 데이터가 날아감. 
  - 대표적인 예시 : SRAM, DRAM

+ 비휘발성 메모리(Non-Volatile Memory) : 전원을 꺼도 데이터가 날아가지 않는 것. 
  - 대표적인 예시 : 하드디스크나 낸드플래스 메모리

## Computer System - Timer

+ Timer & mode bit 의 연관성
  - Time-Sharing 할 때, 타이머를 써서 time-slicing하는 것이다. 
  - 이때, Time-Sharing 하면서 중간중간에 OS가 권한을 가지게 된다. 
  - 프로그램이나 유저가 권한을 가지고 있으면 CPU가 유저에게 사용권한을 준다. 
    - 이때 mode bit은 user mode(1)
  
  - 중간중간에 서로 다른 프로그램으로 CPU 권한을 넘길 때, CPU를 OS가 받아야 다른 쪽으로 권한을 줄 수 있다. 
    - 이때 중간중간에 mode bit은 kernel mode(0)
    - Timer Interrupt를 걸면서 mode bit을 0으로 갖고 온다. 
     
