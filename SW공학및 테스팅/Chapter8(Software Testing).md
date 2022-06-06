# Chapter 8. Software Testing

## Topics Covered

+ Development Testing
+ Test-Driven Development
+ Release Testing
+ User Testing

### Program Testing

+ Testing 이란 무엇인가? 
  - Program Defect(결함) 찾기!
  - 프로그램을 만들었으면, 의도한 대로 잘 동작하는지 확인하기
+ 인위적인 Data로 테스트를 한다!
  - 물론 실제 데이터로 할 수도 있음. 하지만 그게 실제 데이터라 할지라도, 동작하면서 나오는 데이터가 아니다 보니 진짜 "실제 데이터"는 아니다!
  - 실제 데이터를 다시 가져와서 넣는것 자체가 이미 인위적인 데이터이다.(이미 한차례 가공이 된 것임)

+ Error 결과 확인하고 고치기
+ Non-Functional 적인 부분 확인하기. 여기서 Non-Functional 만족하지 못하면, 잘못된 것이라고 인식을 한다.
+ Testing을 했다고 해서, Error 가 없다는 것을 완전히 보증할 수는 없다. 에러가 있는데 못찾은 것일수도 있음.
+ 테스팅한 부분만 에러가 없다는 것을 보증할 수는 있어도, 나머지 테스팅이 안된 부분은 보장할 수 없는 것이다.
  - 모든 경우에 대해서 다 테스팅 해볼수 있다면, 에러가 아예 없다는 것을 보증할 수 있지만, 현실적으로 불가능하다. 

+ 크게 나누면, Verification & Validation 두개로 나눌 수 있다. 
  - Verification : 스펙에 적혀있는 의도대로 되어 있는지?(스펙에 적혀져 있는 대로 되어 있는지?)
  - Validation : 유저가 의도하는 대로 만들어져있는지?

+ Testing하는 목적 : 
  - Developer와 Customer에게 보여주기 위한 목적이 있다.
  - Testing이 잘 수행되면, 해당 Software가 잘 만들어졌고, Requirement를 달성했다고 볼 수 있다. 
  - <strong> 1. 앞서 User Story, User Senario가 있었고, 그것을 가지고 System Requirement를 뽑아낼 수 있었다. 그럼 그 Requirement가 잘 되는지 보여주어야 테스트가 끝나는 것이다.(Validation)</strong>
  - <strong> 2. 스펙과 맞지 않는 이상한 짓을 하는지 여부를 체크하는 것. (Defect 체크) </strong>
  - Validation 이 되기 전에, Verification을 체크하지 않으면 이후 Validation이 될 수가 없다.
    - 애초에 스펙이 다 만족이 되지 않으면, Validation에서 통과가 될 리가 없다. 
    - Validation은, Verification 이후 유저가 직접 눌러보면서 확인하면 그것이 Validation이다.
  - 일단 먼저, 맨날 쓰던 대로 써보고 그것부터 다 만족이 되어야, 그다음에 Error를 찾는것이 의미가 있다.
    - 애시당초에 맨날 쓰던대로도 충족을 못하는데 Error를 찾는게 무슨 의미가 있을까?
  
### Validation & Defect Testing
  
+ Validation Testing : 개발자와 Customer가 만나서 스펙에 따라 다 짜여졌는지 확인하는 것.
+ Defect Testing : Defect, Error, Failure 등을 찾아내는 것.
  
### Testing Process Goals
+ 기본적으로 원하는 Input을 넣어보고, 원했던 Output이 잘 나오는지 부터 테스트해보는 것이다.
    - Black-box Testing : 시스템 내부는 아무것도 모르는 상태로, 입력을 줬을 때 출력이 제대로 나오는지 확인하는 방식.

### Verification vs Validation 

+ Verification : Product를 만들 때 올바르게 만들었는가?
  - 만들어야 하는 것을 만들었는가?
  - 스펙에 맞게 만들었는가?

+ Validation : 유저가 원하는 대로 만들었는가? 유저가 실제로 요구하는 것이 무엇인가?

+ Verification 과 Validation 중 하나라도 빠지면 안된다. 
+ Software 목적/유저가 바라는 사항/Marketing 환경 등은 Validation 에 속한다
  - 저런 것들은 Requirement랑은 관계없는 경우가 많다.
  - 꼭 보고 싶었으면 Requirement에 집어넣었을 수도 있지만, 대체로 집어넣을 수 없는 것들이 많다. 

### Inspection(검사,점검) & Testing

+ 흔히 Review라고 많이 이야기한다. 
+ Inspection : Requirement 에 있는 애들과 소스코드를 비교하며, 맞는지 아닌지 "검사"할 수도 있다. (정적 분석, Static Verification 이라고도 부름)
  - 문서만, 코드만 봐도 당장 앞뒤가 안맞는 부분들, 모순되는 부분들이 나올 수 있다! 그런것들을 찾는 것이다.
  - 동작시켜서 찾는것보다 훨씬 더빨리 찾을 것이다. 
  - Tool based document : IDE에서 제공되는 Tool에서 경고 뜨는것들로 충분히 찾을 수 있다!
  - Inspection 할때는, 스펙, Architecture, 설계, Schema 등 다 "검사"할 수 있다.
  - 프로그램이 개발 안된 상태에서도 할 수 있다.
  - 동작시켜서 보는것만큼 디테일하게 볼 수는 없다. 동작시켜서 보는것만큼 더 많은 것을 할 수는 없다. 대신, 전 단계에 걸쳐서 할 수 있다.
  - 실행하지 않고서도 볼 수 있다

+ Testing : 실제로 Product를 돌려보면서 찾을 수도 있다. (동적 분석, Dynamic Verification) 
  - 실행시키면서 잘 동작하는지 보는 것을 동적 분석이라고 많이 이야기한다. 
  - 결과물이 있어야만 테스팅할 수 있다.

+ 둘다 해도 못 찾는 에러가 나타날 수 있다. 그러므로, 최소한 Inspection, Testing 둘 다 해보면서 에러를 찾아야만 한다.
+ V&V(Verification & Validation) Process 안에서, 두개 다 할 수 있다. 
  - Inspection 같은 경우, Non-Functional Check 하는 것이 불가능하다. 
  - Performance, Usabilty, 기타등등 특성에 관련된 것들은 Inspection 으로 파악하는 것이 불가능하다. 직접 해봐야 알 수 있다.
  - 스펙 문서만 보고 파악하는 것이기 때문에, 유저의 요구사항은 확인할 수 없다.(문서도, User Requirement가 한번 거쳐서 온 것임)
  - 동적 테스팅할 때는, 유저가 옆에서 보고 있으니 유저의 실제 요구사항을 반영할 수 있다.

### A model of the software testing process

<img src = "Ch8_1.png" />

+ Test Case : Test Input과 기대값(expect value)가 합쳐진 것.
  - 설계할 때 Requirement 보고 이야기할 때, 어떤 것을 눌렀을 때 무엇이 나와야 하는지 같은 것들.
  - 처음에 기대했던 것과, 나중에 나오는 것을 비교하면서 테스팅을 진행할 수 있다.
+ Test Data : Test에서의 Input
+ Test Result : Test에서의 Output
+ Test Report : 몇개 통과했는지, 몇개 Fail났는지 나오는 Report

### Stages of Testing(테스팅 단계)

+ Development Testing(개발 테스팅)
  - 시스템 개발할 때, 개발 중간에 이루어지는 여러 가지 테스팅. 
+ Release Testing
  - 개발이 끝났고, 출시하려고 하는 프로그램을 다른 테스트 팀(QA 팀)에서 테스트해 보는 것.
+ User Testing
  - 실제 사용자가 테스팅하는 것. 결국 Release Testing하는 사람도 개발자임. 실제 사용할 사용자가 할때는 또 다르게 될 수도 있다.
  - ex) 핸드폰을 샀는데, 기능 다 매장에서는 잘 되었는데 집에서는 안되는 경우, 와이파이 표시는 떠있는데 실제로는 데이터를 소모하는 경우 등이 있을 수 있다.
  - 유저가 사용하는 환경에서 사용해 보아야 한다. 


