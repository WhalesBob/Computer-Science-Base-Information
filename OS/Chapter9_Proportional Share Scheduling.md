# Chapter 9. Proportional Share Scheduling

+ 기존 Scheduling 기법(MLFQ) 에서의 문제점
  - MLFQ 에서는 Starvation 문제가 생길 수 있었다
  - 성능도 중요하지만, 특정 Process 가 CPU 권한을 오랫동안 받지 못하는 것이 상당히 좋지 않다.
  - __Fairness를 보장하는 Scheduling 기법이어야 한다.__
    - 실제 System 에서는, 성능과 Utilization 도 중요하게 생각하지만, Fairness 도 굉장히 중요하게 생각한다. 
    - Starvation 을 회피하는 방법을 찾아 보자!
    
+ 이 시간에 중점을 두어 보는 것
  - __어떻게 하면 Ready Queue 에 있는 Job 들이 CPU 권한을 최대한 공평하게 받을 수 있을까?__
  - Fare Share

+ Proportional-Share Scheduling(비례되어 나누는~ )
  - Fair-Share Scheduling 이라고도 불린다. 
  - 모든 Process 가 똑같은 권한으로 CPU 에 접근하는 것을 보고 Fair 하다고 부르지는 않는다. 
  - Example 1
      - 10 개의 Process 가 10% 씩 CPU 권한을 갖는 것은 얼핏 보면 Fair 해 보일 수 있다.
      - 하지만, 각각의 process 의 중요도가 완전히 동일한 것은 아니다. 
      - 훨씬 더 중요한, 혹은 덜 중요한 Job 들이 있기 마련이다. 
    
   - Example 2
      - 스마트폰으로 카카오톡을 한다고 했을 때, 사용자가 주로 쓰는 카카오톡은 foreground, 메모리를 관리하는 눈에 보이지 않는 Process 들은 Background 에서 동시에 돌아갈 것이다.
      - Background 작업들이 중요하기는 하지만, User Experience 를 위해서라면 Foreground 에서 돌아가는 것이 훨씬 중요하다.
      - 그렇다면, Background 와 Foreground 에 똑같은 CPU 권한을 주는 것은 과연 Fair 한가?
      
   - 특정 Process가 , CPU 에 대한 권한을 오랫동안 차단당하는 Starvation 이 일어나지 않게 되는 것으로 이런 개념이 출발했다. 
   - "각각의 Process 가 특정 percentage 만큼의 CPU 권한을 가져야 한다"
   - 그러면서, 설정해준 Process 의 CPU 권한 가지는 시간 대비 효율을 계산해 주면서, 해당 Process 의 CPU 권한을 갖는 시간을 조절해 나갈 수 있다.
   - __각각 개별 Process 들에게는, 최소한의 Percentage 를 가지고, CPU 권한을 획득할 수 있는 기회를 제공할 수 있다.__
   
     
    
