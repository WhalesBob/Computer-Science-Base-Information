# Chapter 3. Introduction to Computing Systems

### Schematic Overview of Computer System

<img src="image/Ch3_1.png"/>

#### 위 그림에 대한 설명

+ mode bit(Register) : 컴퓨터가 동작할 때 2가지 mode가 존재한다
  - CPU 권한을 누가 가지고 있냐에 따라 mode가 달라진다
  - mode bit 1(User Mode) : User가 CPU 권한을 가지고 있을 때, User Program이 돌게 된다. 
  - mode bit 0(Kernel Mode) : CPU에 대한 권한을 OS가 가지고 있을 때이다. 
  - 이렇게 나눈 이유 
    - 컴퓨터 OS는 관리해야 할 것이 많은데, User 에게 이런 Resource 고나리를 모두 일임했을 때 문제가 발생할 수 있다. 
    - 이런 접근(Critical 한 동작)들을 OS 가 관리하는 것이다. 
    - OS가 사전에 약속된 동작들을 수행하게 된다.(Protecting)

+ 휘발성 메모리(Volatile Memory) : 전원을 끄면 데이터가 날아감. 
  - 대표적인 예시 : SRAM, DRAM

+ 비휘발성 메모리(Non-Volatile Memory) : 전원을 꺼도 데이터가 날아가지 않는 것. 
  - 대표적인 예시 : 하드디스크나 낸드플래스 메모리

