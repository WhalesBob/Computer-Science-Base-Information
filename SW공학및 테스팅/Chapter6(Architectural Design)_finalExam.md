+ 수업을 들으면서 교수님께서 하신 말씀을 정리하는게 제일 좋지만, 시간이 없는 관계로 먼저 강의자료를 한글로 정리함.


#### Pipe and filter Architecture 

<img src = "https://mingrammer.com/images/2017-09-10-pipe-filter-pattern.png">

+ 파이프를 따라 데이터가 이동하고 처리되며, 중간에 필터가 걸려 있는 형태라고 생각하면 편하다. 
+ 데이터 처리 시스템에서 광범위하게 사용되는 Batch Sequential Model이다. 
+ 데이터 처리 프로그램에서 많이 사용되며, 입력을 따로 받는 경향이 있다. 
+ Interactive System에서는 적합하지 않다. (한 방향으로 흐르듯이 처리되기 때문.)
+ 장점 : 
  - 이해하기 쉽고, 다른 곳에서 재사용하기 쉽다. 
  - Workflow Style이 다른 프로그램에서 사용되는 것과 비슷한 부분이 많다.
  - 파이프에 처리를 더 추가해서, 간단하게 더 발전시킬 수 있다. 
  - Sequential System으로도, Cuncurrent System으로도 구현될 수 있다. 

+ 단점 : 
  - 데이터 전송에서의 Input 과 Output의 형식을 합의해서 각 함수들을 만들어야 한다.
  - 이렇게 처리하다보면, 받은 Input을 다시 쓰기 편한 형태로 재가공해야 하고, Output도 맞게끔 만들어줘야 하다 보니, 시스템 오버헤드가 증가한다. 
  - 해당 데이터 구조에 호환되지 않는 Function을 단순히 재사용하는 것은 불가능하다. 


## Application Architecture

+ 프로그램들은, 결국 특정 회사나 조직, 소비자들의 욕구를 충족하기 위해 만들어졌다.
+ 소비자들은 많은 공통점들을 가지고 있다.(사람이 생각하는게 다 거기서 거기다.)
  - 결국 이런 욕구를 만족시키는 프로그램들은 각기 다른 공통 Architecture를 갖는 경향이 있다.

#### Use of Application Architecture

+ 이런 Application Architecture는 언제쓰나?
  - Architectural Design의 시작지점.(미리 해당 Architecture를 갖고 간다고 생각하면, 거기서 조금만 더 수정하면 된다. 그래서 시작지점으로 활용할 수 있다.)
  - Design의 Check List(비슷한 디자인이라고 생각하면, 구현했는지 안했는지 체크리스트로 사용가능)
  - 개발팀의 일을 정하는 방법이 되기도 한다. (무슨 일을 먼저 할지, 무슨일을 언제할지 등)
  - Component의 재사용을 평가하기 위한 수단이 되기도 한다. 
  - 어떤 프로그램 타입인지 말하기 위한 단어의 역할도 된다. 

#### Application Type

+ Data Processing Application 
  - 데이터 기반 Application은, 처리 중 사용자가 명시적으로 개입하지 않고 일괄적으로 데이터를 처리함.

+ Transaction Processing Application(혹은 System)
  - 시스템 DB에서 사용자 요청 및 업데이트 정보를 처리하는 Data 중심 Application이다.
  - Ex) E-commerce System / 예약 시스템
  - DB에서의 정보요청 또는 DB 업데이트 요청을 처리하는 System이다 
  - 유저 입장에서 보는 "Transaction"(처리) 은,
     - DB에서 런던에서 파리까지 가는 비행기 시간을 찾는 것을 요청함. 
     - DB에서 해당 정보를 가져오기 위해, "일관성 있는 순서" 로 작업을 처리함.

  - 도식표 및 예시
  
  <img src = "" > 

+ Event Processing Systems
  - 프로그램의 Action이, 시스템 환경에서의 이벤트 해석에 따라 달라지는 Application이다. 
  - 해당 이벤트를 긴 터치라고 받아들였을 땐 A라는 Action을 취하고, 짧은 터치라고 받아들였을 때는 B라는 Action을 취하는, Android Application 처럼 이해하면 받아들이기 편할 것 같다. 
  
+ Language Processing Systems
  - "시스템에서 처리 및 해석하는 공식 언어로 사용자의 의도를 지정하는 응용 프로그램" 
  - 기계어로 작성하는 것이 불편하기 때문에 만들어진 프로그래밍 언어와, 컴파일러라고 생각하면 쉽다. 
  - 프로그래밍 언어를 공식 언어로, 우리는 코딩을 해서 우리가 의도한 대로 컴퓨터를 동작시킬 수 있는 것과 같다. 
  -  Ex) 컴파일러 / Command Interpreter
  
+ 주로 Transaction Processing System과 Language Processing System이 많이 쓰이는 것으로 알려져 있다.

