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
   
+ Lottery Scheduling & Stride Scheduling 이 있다.

## Basic Concept : Tickets Represent Your Share

+ 기본 Concept : Tickets(몇 퍼센트의 티켓을 가지고 있는지?)
  - 몇 퍼센트의 Ticket 을 가지고 있는가는, 각 Process 가 전체 CPU 중 몇 퍼센트의 CPU 사용권한 시간을 가질 수 있는가로 결정된다. 
  - Ticket 을 몇 개 가지고 있느냐에 따라(Ticket 수에 비례해서) CPU 권한을 그만큼 많이 획득한다(percentage 에 비례한다)
  - 이렇게 Ticketing 을 통해 Scheduling 하면, Starvation 을 막을 수 있을 것이다. 하지만, 정말 그 해당 Percent 만큼 맞아떨어지지는 않는다. 
  - 개별 Process 에게 최대한 골고루 Ticket 을 나눠 주는 것이 기본적인 Idea 이다.
  
#### 이렇게 각 Process 에 Ticket 을 줬다면, 어떻게 그 확률만큼 실제로 CPU 권한을 갖게 할 수 있는가?

## Lottery Scheduling(확률 기반)

<img src="image/Ch9_2.png"/>

+ 진행과정
  - Scheduler 가 Winning Ticket 을 한장 뽑는다.
  - 만약 Scheduler 가 63번을 뽑았다면, A가 승자이다. A를 실행ㅎ나다 
  - 다시 Ticket 뽑기를 진행한다. 
  - 이런 식으로 계속 뽑기로 Ticket 을 줘서 진행한다 
  
+ 과연 그래서 그 퍼센트만큼 잘 맞아 떨어지나?
  - Percentage 를 줬다고는 하지만, 정확히 그렇게 시행되지는 못한다. 
  - 확률적이기 때문이다. 물론 엄청 긴 시간동안 실행한다면 CPU 를 75:25 정도로 근접하게 배분할 수 있을 것이지만, 정확히 Lottery Scheduling 에서 우리가 원하는 정도의 CPU 권한을 나눠갖게 되는 것은 아니다. 
  - 그저 그 수치에 근사하게는 만들 수 있다. 
  
+ Lottery Scheduling 장단점
  - 장점 : 
    - Simple 하게, 각 Process 가 가지고 있는 Ticket 수에 비례해 CPU 권한을 할당할 수 있다. 
    - 계속 돌리면, 근차시로 맞아떨어질 수는 있다.
    
  - 단점 :
    - 딱 그만큼 정확히 맞아떨어지지는 않는다.
    - 그래서 정확히 그 배분을 Guarantee(보장) 하지는 못한다. 
    
+ 핵심 Idea : "Random Selection"
  - 특징 : 확률적으로 Fair 하게 이루어진다. 
  - 정확하게는 아니지만, 그들이 들고 있는 Ticket 에 비례하게 CPU 권한을 할당해 준다. 

#### 이런 Simple 한 Ticket 방식을, 실제 System 에서 활용하기 위해서는 몇 가지 Technique 이 필요하다. 

## A. Ticket Currency

<img src="image/Ch9_3.png"/>

+ 그림 설명
  - Base 에서 Alice 와 Bob 에게 각각 3000,2000 만큼 나눠 주었는데, Alice와 Bob 은 각각 하위 Task 에게 자기들이 나눠주고 싶은 만큼 잘라서, Ticket 을 각각 할당했다. 
  - 아무리 Alice 와 Bob 이 그렇게 할당했다 하더라도, 결국 base 입장에서 보면, 2000/1000/1000 정도로 나뉘어 분배가 된 것이다. 
  - 다시 base 입장에서 환산해서 CPU 에 대한 권한을 획득하게 된다. 
  
+ Ticket Currnecy Concept
  - Main System 이 자기가 알아서 CPU 권한을 할당해서 Sub-System 에게 주고, Sub-System 이 자기가 하고 싶은 단위대로 아래 Task 에게 CPU 권한을 나눠줄 수 잇다. 
  - 물론, Task가 받은 CPU 권한들은, __다시 제일 위에 있는 Main System 의 Percentage 기준으로 환산하여 사용해야 하지만, Sub-System 들도 자기 식대로 Ticket 을 발행해서 나눠줄 수 있는 것이다.__
  
+ Ticket Transfer
  - Ticket 을 다른 Process 에게 주거나, 받아올 수 있다. 
  - Ticket 을 매개로 한 Communication  이 가능한 것이다,
  
<img src="image/Ch9_4.png"/>

+ 가장 대표적인 예시 : Server - Client
  - Client 는 Server 에게, 자신이 수행해야 할 일이 있으니 이 일을 빨리 처리해 달라고 Message 를 보낼 것이다. 
  - Client 는 자신이 요청한 일이 빨리 처리되었으면 하는 희망이 있는데, 막상 Client 자신은 그 결과를 기다리는 상황이라 막상 할 일이 없다. 
  - 그러니, Server 에 요청을 보낼때 자신이 가지고 있는 Ticket 까지 같이 보내면, Server 가 가지고 있는 Ticket 갯수가 올라갈 것이다. 
  - 그럼 Server 가 CPU에 대한 권한을 획득할 확률이 올라간다. 
  - Server 는 해당 결과를 Feedback 해 주고, Client 에게 빚졌던 Ticket 을 다시 돌려주면 된다. 
  - Client 도, 그 Ticket 을 돌려받아야 그 뒤에 수행할 후속 작업을 CPU에 접근해 진행할 수 있을 것이다. 
  
  
  



     
    
