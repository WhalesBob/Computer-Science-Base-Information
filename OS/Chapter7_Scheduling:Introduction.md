# Chapter 7. Scheduling : Introduction

+ 여전히 CPU Virtualizaiton 에 대한 부분을 다룬다.
  - CPU 는 여전히 하나이지만, Logical CPU는 무한개를 제공하고 싶다.
  - 그러기 위해서는 2가지 기법이 필요하다. 
    - 하나는, 프로세스를 멈추고 다른 프로세스를 구동했다가, 다시 돌아와서 해당 프로세스를 문제없이 진행하는 것이다.
    - Context Switching 이 이것을 가능케 했다.  
    - 다음 OS가 할 일은, 만약 수행중인 프로세스를 멈추었다면 다음은 어떤 것을 수행해야 괜찮을지에 대한 부분이다.
    - __메모리에 10개,100개의 프로세스가 올라가 있으면, 다음은 무엇을 실행할 것인가?__

+ 더 발전되는 질문
  - 100개의 Process 중 하나를 선택해야 한다면, 나머지 99개의 Process는 어떤 상태에 있어야 하는가?
  - 당연히 Ready, 적어도 Suspended Ready 에 있어야 한다. 
  - Block 에게 CPU 실행권한을 줘봤자, Resource가 모자라기 때문에 실행할 수 없다. 
  - __그러므로, Ready State 에 한해서 Scheduling 을 적용해 보자!__
  - Blocked State는 이 단원에서 신경쓰지 않아도 될 것이다. 

## Process Scheduling

+ Ready Queue 에 있는 Process 를 대상으로 한다. 
+ 수행하기 위해 필요한 모든 Resource를 가지고 있고, CPU 권한만 기다리고 있는 Process 중, 그 다음 어떤 것을 실행할 것인가?
  - 이런 주제가 Scheduling 이다.

+ CPU Scheduling, __Job Scheduling__, Process Scheduling 다 같은 말이다. 
  - Job Scheduling 이라는 말을 자주/쓴다. 
  - OS 역사에서 처음에 한 일은, 동시에 수행될 수 있는 Job 이나 Task를 Batch 형태로 모아서 순서대로 수행시키는 것(Single Batch) 였다.
  - OS와 비슷한 역할을 하는, 모니터라는 장치가 등장했고, 순서를 결정했었다. 

+ 하지만, Thread Scheduling 은 당연히 다른 말이다. 



