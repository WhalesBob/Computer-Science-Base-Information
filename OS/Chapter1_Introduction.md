# Chapter1. Introduction

<img src="image/Ch1_1.png"/>

+ 운영체제(Operating System, OS)란? : 
  - 컴퓨터 하드웨어의 자원을 효과적으로 잘 관리해 주는 시스템 프로그램이며, 사용자가 컴퓨터에 대해 잘 모르더라도 컴퓨터를 원활하게 잘 다룰 수 있도록 중간에서 도와주는 프로그램.
  
  - Application Software : High-Level Language(C/C++, Python, SQL...)로 쓰여진 프로그램
  - Hardware : Processor, Memory, I/O Controller 같은 것들
  - System Software(OS단) 
    - Compiler : High Level Language를 Machine Code로 컴파일해줌. 
    - __Operating System__ : I/O 핸들링해주며, 메모리와 보조 저장장치를 관리하며, Job Scheduling이나, resource를 sharing 해주는 등의 역할을 수행함. 
    
  - OS는 컴퓨터 하드웨어와 User Application Software 사이에서, 그 둘의 Interface 역할을 수행한다. 
    - Interface : 중간 사이의 소통창구 정도로 생각해도 좋다.
    - UI(User Interface) : 유저와 프로그램(?) 사이에서, 서로의 소통창구가 되어주는 것. 
    
    
+ Kernel

  - <img src="image/Ch1_2.png"/>
  - 커널(Kernel) 이란, 운영체제의 핵심 부분으로, 커널의 역할 역시 운영체제의 핵심 부분임. 
  - 뒤에 나오는 운영체제의 내용은 당연히, 커널이 하는 역할이기도 하다. 
  - 커널 내에 있는 기능
    - Utility : 사용자에게 다양한 부가기능을 제공한다. 
    - System Call Library : 개발자가 OS를 통해, 시스템에서 제공해주는 기능을 call 할 수 있게 해주는 Library
  - 좁은 의미의 Operating System 는, "커널" 그 자체라고 이야기할 수 있을 정도이다. 
  
  - 운영체제의 목적 : 컴퓨터를 잘 모르는 사람들도 원활하게 사용할 수 있게 해주는 것이다. 
  - 운영체제가 하는 역할 : 
    - 보안 : 컴퓨터 하드웨어와 프로세스의 보안을 책임지는 역할을 함. 
    - 자원 관리 : 한정된 시스템 자원을 효율적으로 관리하여 프로그램의 실행을 원활하게 만듬. 특히 프로세스에 처리기를 할당하는 것을 스케쥴링이라고 함. 
    - 추상화 : 같은 종류의 부품에 대해 다양한 하드웨어를 설계할 수 있기 때문에, 하드웨어에 직접 접근하는 것은 문제를 매우 복잡하게 만들 수 있음. 일반적으로 커널은 운영 체제의 복잡한 내부를 감추고, 깔끔하고 일관성 있는 인터페이스를 하드웨어에 제공하기 위해 몇 가지 하드웨어 추상화(같은 종류의 장비에 대한 공통 명령어의 집합)들로 구현된다. 이 하드웨어 추상화는 프로그래머가 여러 장비에서 작동하는 프로그램을 개발하는 것을 돕는다. 하드웨어 추상화 계층(HAL)은 제조사의 장비 규격에 대한 특정한 명령어를 제공하는 소프트웨어 드라이버에 의지한다. 
    - System call을 통한 하드웨어에 접근 : 읽고/쓰고/수정하는 등의 역할을 도와준다. System call을 통해서만 하드웨어에 접근 가능하다.
    
      - 컴퓨터 하드웨어를 안전하게 보관하기 위한 필수적인 기능이다.
      - 그렇지 않으면 하드웨어가 망가지거나, 하드웨어가 제 기능을 온전히 사용하지 못할 수 있다
      - 컴퓨터가 동작하는 일은, 운영체제 안에서 해결하거나, System Call에 접근해서 하는 일이다.
      
+ OS의 두가지 측면
  - <img src="image/Ch1_3.png"/>
  - 시스템 자원은 언제나, 동서고금을 막론하고 항상 한정되어 있다. 
  - 그래서 언제나 OS는 hardware 자원을 효율적으로 관리해야 한다. 그래서 performance를 최대화해야 한다. 
    - 한정된 자원을 효율적으로 잘 써서, 컴퓨터 성능을 Maximize 해야만 한다. 
    
  - OS는 hardware 자원을 공정하게 각 프로세스에 배분해서, "사용자 경험"을 언제나 일정 수준 이상 보장해야 한다. 
  - 결론적으로, OS는 컴퓨터 시스템을 사용자가 편하게 사용할 수 있도록 만들어 줘야 한다!
    - 유저 프로그램을 실행시켜, 유저가 문제를 해결할 수 있도록 도움을 줘야 한다. 
    
+ Categories Of Operating System(Two Aspect)
  - 얼마나 많은 유저들이 "그 순간에" 사용할 수 있는가?
    
    1. Single User System : 
        - "한 순간"에 한 사람이 시스템에 접근할 수 있음.
        - 간단하지만, 제한된 성능을 낼 수 있음 
        - MS-DOS, Windows, Mac-OS
    
    
    2. Multi-User System:
        - 한 순간에 여러 사람이 시스템에 접근할 수 있음
        - 복잡하고, 여러 다른 일들을 스케쥴링해야 하며, 각 유저에 대해 접근 권한도 관리해야 하고, 보안에도 신경써야 함. 하지만 전반적인 퍼포먼스를 올릴 수 있음
        - Unix, Mainframe, Windows NT, Linux 등
    
  - "동시"에 일을 얼마나 많이 할 수 있는가    
  
    1. Single Tasking System 
        
        - 한 순간에 하나씩 할 수 있음
        - MS-DOS, Windows CMD
        
    2. Multi Tasking System 
        - 한 순간에 여러 일을 할 수 있음
        - 대부분의 현대 OS like Linux, Unix, Windows...
        
  - Open Source vs Closed Source System
  
    1. Open Source OS(Linux) : 
        - 소프트웨어 값이 공짜이며, 소스코드를 제한 없이 고쳐 쓸 수 있다. 
        - 소스 코드가 해커 연습용으로 풀려 있다. 
        
    2. Closed Source OS(Windows) :
        - 값을 지불하고 사용해야 함. 
        - 소스 코드를 볼 수 없고, 바꿀수 없음. 
        - 보안에는 더 강력하다고 알려져 있다. 
        
  <img src = "Ch1_4.png"/>      
  
  - Monolithic Kernel(단일 커널) vs Micro Kernel(마이크로 커널)
  
    1. Monolithic Kernel(단일 커널) 
        - 커널의 다양한 서비스 
        
