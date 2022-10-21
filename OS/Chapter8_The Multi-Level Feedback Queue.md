# Chapter 8. The Multi-Level Feedback Queue(MLFQ)

+ 개요
  - 우리가 Runtime 을 모르지만, 그것을 고려해서 만든 새로운 Scheduling 기법이다. 
  - System 에 지금 사용되고 있는 Scheduling 기법이기도 하다.  
  - Multi-Level Feedback Queue
    - Multi-Level Queue : 여러 개의 레벨(층) 이 있는 Queue.
    - Ready Queue 가 하나가 아닌 여러개의 Level 이 중첩되어 있는 것이다. 
    - Feedback : 일반적으로, 한 번 수행했을 때 나오는 결과를 그 뒤에 반영하여, 정책이나 다른 것을 바꾸는 것을 보고 Feedback 이라고 부른다.
    - "한번 수행해서 이런 결과가 나왔으니, 다음에는 이렇게 바꿔야지!" 하는 것이다. 
  
  - Queue 가 여러개 적층되어 있고, Job 이 수행하는 Scheduling 의 결과를 가지고 Feedback 하여 정한다 라고 볼 수 있겠다.

## Multi-Level Feedback Queue(MLFQ)

+ Multi-Level Feedback Queue 는, 처음에는 Multi Level Queue 에서 시작했다. 
  - 그러다가 Multi-Level Feedback Queue 로 발전해서, 현재 사용하고 있다. 

+ Multi-Level Queue : 기본적으로는 Turnaround Time 을 최적화하는 것을 일차적인 목표로 하고, Response Time 도 2차적으로는 최소화하는 것으로 한다. 

+ Runtime 을 모르지만, 그럼에도 불구하고 수행에 있어 가능한 Turnaround Time 을 최적화 하면서도, Response Time 을 최소화 할 수 있다. 


## MLQ : Basic Rules

+ 실질적으로 Multi-Level Queue 가 먼저 개발되고, 이후에 MLQ가 가지고 있는 문제들을 해결하기 위해 MLFQ가 나왔다.

+ Rules
  - MLQ는 기본적으로, Process 실행에 있어 각각의 Job 에게 Priority 를 세팅했다. 
  - Priority 를 주었다는 이야기는, Scheduling
