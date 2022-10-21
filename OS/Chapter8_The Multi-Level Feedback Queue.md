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

+ 
