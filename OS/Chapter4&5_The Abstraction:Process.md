# Chapter 4 & 5. The Abstraction : Process

+ Virtualization : 내가 가지고 있는 resource가 물리적으로 제한되어 있음에도 불구하고, User에게는 무한한 Logical 한 Resource를 제공할 수 있는 것만 같은 illusion을 제공하는 것.
+ 수업에서는 single-core 환경을 가정함

+ CPU Virtualization : 한개의 CPU가 있지만, 사용자에게는 무한개의 logical CPU가 있는 것처럼 환상을 주는 기법

+ Memory Virtualizaiton : 물리적 메모리의 사이즈는 제한되어 있지만, 어떤 기법들을 가지고 사용자에게 무한한 크기의 logical 메모리 크기가 있어 보이는것같은 illustion을 제공해 주는 기법.


## Von Neumann Machine

<img src="image/Ch4_1.png"/>

+ 폰 노이만 머신(Von Neumann Machine) : 모든 성격의 머신의 Prototype
+ 폰 노이만 머신에 포함되어야 하는 것
   - 산술 논리 장치와 프로세스 레지스터를 포함하는 "처리 장치"
   - 명령 레지스터와 Program COunter를 포함하는 Control Unit
   - 데이터와 명령어를 저장하는 (Main)Memory
   - 외부 대용량 저장장치
   - 레지스터 
      - 컴퓨터 프로세서 내에서 자료를 보관하는 아주빠른 기억 장치. 
      - 메모리 계층의 최상위에 위치하며, 가장 빠른 속도로 접근 가능한 메모리.

+ 폰 노이만 Architecture에서, CPU 는 오로지 메인메모리하고만 통신함.

+ Von Neumann Machine 과 지금의 컴퓨터
   - Von Neumann Machine 에서의 레지스터 숫자 보다는 지금의 레지스터가 16개(혹은 32개)로 더 많다. 
   - 하지만, 레지스터가 하는 역할 자체는 Von Neumann Machine 에서나 지금의 컴퓨터에서나 같다. 
   - 같은 프로그램을 수행하기 위해 필요한 Information 들을 레지스터에 담아와서, 레지스터에 있는 값들을 가지고 연산하는 것이다. 
   - 연산된 값도 다시 메모리에 주는 것도, 현재의 컴퓨터나 그때의 Von Neumann Machine과 같다. 
      - Output Device에 CPU가 직접적으로 데이터를 줄 수가 없다. 
      - 무조건 메모리에 담아야 하고, 메모리에 담고 있는 데이터를 Output Device에 넘겨주는 것이다. 
      
+ Registers
   - AC(Accumulator Register) : 누산 레지스터. 연산장치의 입출력 데이터를 임시적으로 기억하는 레지스터.
   - PC(Program Counter) : CPU가 그 다음 참조해야 하는 명령어 코드 주소를 가지고 있는 레지스터. 
   - CIR(Current Instruction Register) : 명령어 레지스터. 명령어를 읽어와 저장하는 레지스터. 해독,수행하기 전에 이 레지스터를 거친다. 
   - MAR(Memory Address Register) : 현재 접근할 메인 메모리의 주소를 기억하는 레지스터
   - MDR(Memory Data Register) : 메인 메모리로부터 읽거나 쓰여질 데이터를 일시적으로 저장하는 레지스터

+ Register가 필요한 이유 : CPU는 동시에 여러 개를 계산할 수 없으니, 중간에 저장하기 위해 레지스터가 실제로 필요할 수 밖에 없다. 
<img src="image/Ch4_2.png"/>

+ Programmer의 관점에서 바라보는 CPU와 Main Memory
   - CPU 안에는 여러 register들이 있어서, CPU를 보조해줌. 
   - 메모리는, Array of Byte로 되어 있음. 
      - 그냥 1byte 가 아래로 쭉 있는 배열
      
## Appendix : Instruction Set Architecture(ISA)    

<img src="image/Ch4_3.png"/>

+ Instruction Set Architecture : (프로세서가 인식해서 기능을 이해하고, 실행할 수 있는 기계어)명령어 집합.
   - 명령어 : 프로그래밍 언어로 짠 코드를 컴파일한, 기계어 level의 instruction (Machine Level Language)
   - 컴퓨터와 대화하기 위해서는, 기계어가 되어야 함. 
   - 컴퓨터를 잘 몰라도, 기계어로 컴퓨터와 대화할 수 있음. 기계어도 Interface 라고 할 수 있다. 
   
   - 명령어의 각 비트는 기능적으로 분할하여 의미를 부여하고 숫자화한다. 
   
<img src="image/Ch4_4.png"/>

+ Software 에서 Hardware 로 넘어가는 단계에서 중재자 역할을 해 주는 것이 ISA라고 할 수 있다.

+ State Machine
   - 우리가 어떤 명령어를 주면, state가 하나씩 바뀌는 Machine
   - 우리가 아는 모든 디지털 기기는 finite state machine 이다. 
   - state 라고 하는 것은, 메모리나 레지스터 두개를 묶어서 말하는 것이다. 
   - Insturction Set 이라고 하는 것은, 결국에는 "State를 바꾸는 일" 밖에는 하는 것이 없다. 
   - ex)
      - 1+2 = 3을 계산할 때, Register 두개에 1,2를 넣고, 결과를 다른 레지스터에 넣는다. 
      - 결과를 다른 레지스터에 넣었으면, 해당 레지스터에는 이전의 어떤 값에서 3으로 그 state가 바뀌는 것이다. 
      - 반대로, 이 결과값을 출력하고 싶으면, 레지스터 값을 출력하고 싶은 메모리에 다시 넣어 주어야 한다. 
   
   - Instruction Set이라고 하는 것은, 복잡한 문법을 다 차치하고, 결국에는 State를 바꾸는 것이다. 
   - 그리고 State는 메모리 와 레지스터를 말한다. 
   
   

### Appendix : Instruction Set Architecture Example

<img src="image/Ch4_5.png"/>

+ lw : word 단위로 load

1. lw r1,1(r0) : r0 에 있는 값을 +1 한 메모리 주소로 가서 거기에 있는 값을 r1 레지스터에 집어넣기
   - r0에 있는 값은 1, 거기에 +1 하면 2, 2번지에 있는 값을 r1에 저장해서, r1에 2가 저장되었다.
   - Program Counter : 21로 바뀜

2. lw r2,2(r0) : r0 에 있는 값을 +2 한 메모리 주소로 가서, 거기서 있는 값을 r2 레지스터에 집어넣기 
   - r0 에 있는 값은 1, 거기에 +2 하면 3, 3번지에 있는 값을 r2에 저장. r2가 7이 되었다. 
   - Program Counter : 22로 바뀜.
   
3. add r3,r1,r2 : r1, r2에 있는 값을 더해서 r3에 업데이트.
   - r1 : 2 / r2 : 7  이므로, r3에 2+7 = 9. 9를 r3에 업데이트.
   - Program Counter : 23으로 바뀜. 
   
4. sw r3,0(r0) : r3에 있는 값을 메모리 주소 r0에 저장하기.
   - r3에 있는 값인 9가 1번지 메모리 주소에 저장됨. 
   - Program Counter : 24로 바뀜. 
   
5. j 15 : 다음 수행할 명령어인 15로 점프할 것
   - Program Counter 만 15로 바뀜. 
   
#### 1 by 1 으로 수행하면서, 레지스터나 메모리에 업데이트함.    
   
## Appendix : (Virtual) Memory (Logical Memory)

+ Logical Memory 부분이라는 것을 잊지 말자! 

+ 그리고 당연히, Memory 는 Byte Array이다.

+ 32bit Architecture
   - 32bit Architecture는 4 byte 단위로 명령어가 이루어져 있다(1byte = 8bit)
   - 명령어 길이가 32bit이다. 
   - 32bit Architecture 는, 메모리 구조도 32bit 단위로 어떻게든 이루어진다. 
   - 32bit을 가지고 표현할 수 있는 경우의 갯수는 2^32 개 이다. 2^32 B 는 4GB이다.
      - 그래서 32bit Architecture가 가질 수 있는 Maximum Memory Size 가 4GB 이다. 
   - 메모리 주소 길이가 32bit을 넘지 못한다. 
      
#### 질문 : 32 bit Architecture 에서, 1byte가 쭉 이어져 있는 것이 메모리이고, 명령어의 길이가 32bit 으로 이루어져 있는데, 하나의 메모리 주소가 가질 수 있는 size 는 어떻게 1byte 인가? 
#### 혹시 하나의 메모리 주소가 가리키는 부분이 1byte 라는 의미로 받아들이면 되는 것일까? 메모리 "한 칸" 이라서?

+ CPU가 바라보는 메모리는, bytes Array이고, 메모리 size는 CPU가 몇 bit Architecture 이냐에 따라 다르다
   - 32bit Architecture 일 때는 4GB, 64bit Architecture 일 때는 4 * 2^32 GB

<img src="image/Ch4_6.png"/>

   
