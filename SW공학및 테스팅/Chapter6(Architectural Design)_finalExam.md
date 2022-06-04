+ 수업을 들으면서 교수님께서 하신 말씀을 정리하는게 제일 좋지만, 시간이 없는 관계로 먼저 강의자료를 한글로 정리함.


### Pipe and filter Architecture 

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

