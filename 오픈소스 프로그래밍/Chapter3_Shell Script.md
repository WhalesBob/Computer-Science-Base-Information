
# Ch3. Shell Script 


## 3.1 Shell이란 ?  

컴퓨터 운영체제와 사용자가 명령어로 소통하는 유저 인터페이스.  사용자가 Shell을 통해서 컴퓨터에 실제 명령을 입력할 수 있다!
Shell같은 경우엔, 컴파일 해야 되는 언어와 다르게 컴파일하는 과정 없이, 명령어로 한줄씩 실행하는 특징이 있음. (Interactive)
Command Interpreter라고 할 수 있다. UNIX나 LINUX에서 동작하는, 명령어를 해석해 주는 인터페이스를 Shell이라고 한다. 


   (번외) 운영체제(OS)는 커널이라 하는 핵심 부분이 있음. 전원을 키면 OS 부분이 메모리에 순차적으로 올라오게 되는데, 
   여기서 제일 먼저 올라오는 것이 커널이다. 커널이 로드가 되면, 사용자의 입력장치를 로드하는 절차를 거쳐야 할 것이다. 
   그래야 이래저래 명령을 내릴 수 있음.

+ Shell 종류 
  - 윈도우 기반 : 명령 프롬프트, PowerShell
  - UNIX/Linux 기반 : sh, csh, bash, tcsh, zsh
  - Ubuntu Linux를 포함한 대부분의 Linux의 경우, "bash"를 디폴트로 사용


## 3.2 Linux 명령어

### 3.2.1 리눅스 명령어 기본 - 1. :"ls" : 
+ ls : 파일 조회
+ ls -a : 모든 파일 조회(숨김 파일까지 조회)
 - (Linux에서는 .으로 시작하는 파일들을 숨김 파일로 간주함)

+ ls -l : 파일 목록을 자세히 조회
+ ls -al : 모든 파일에 대한 목록을 자세히 조회
  - ls -al 결과에 대한 내용 : drwxr-xr-x
  -drwxr : 
      
        앞의 d는 directory(폴더)인지 아닌지 여부를 가르쳐 줌.
        r은 read, w는 write, x는 execute. 처음 3개는  본인, 중간 3개는 그룹, 끝 3개는 모든 사용자에 대한 설명

### 3.2.2 리눅스 명령어 기본 - 2. : 디렉토리/폴더 명령어 : 
+ mkdir : 폴더 생성 
+ cd : 폴더 이동
+ rm : 파일/폴더 삭제


### 3.2.3 리눅스 명령어 기본 - 3. : 일반 사용자/루트 사용자 
+ whoami : 현재 사용자가 누구인지를 확인하는 명령
+ sudo[명령어] : 루트 사용자(관리자) 권한으로 명령 실행
+ sudo -i : 루트 사용자 권한으로 쉘을 실행
  - 참고) bash에서 '$'는 일반 사용자 쉘, '#'은 루트 사용자 쉘
+ exit : 쉘 빠져나오기

+ **Linux Tip** 
  - Ctrl + U : 전체 줄을 삭제 
  - tab : 자동완성을 위해 사용함

### 3.2.4 Shell 에 대한 본격적인 내용 
+ Shell Script : 

    여러 줄을, 프로그래밍과 비슷하게 , 사용자가 여러 줄로 입력해서 동작하게 하는 방식을 Shell Script라고  한다. 
    여러 개의 일련의 명령어들을 나열하는 것임. 그 결과를 터미널에서 확인할 수 있다. 일련의 명령어들을 한 파일에 가지고 있으면, 
    이것들을 실행시키는 것이 Shell Script가 하게 된다.  
  
+ Shell Prompt : 우분투 위에서는 "bash"라는 prompt를 사용한다. 이 수업에서는 bash 위에서 동작시킴. 
  
     (번외) : 윈도우/윈도우 서버를 관리할 때는 powershell, LINUX/UNIX 기반으로 관리할 때는 Shell Script를 많이 사용한다 

    Shell은 무엇인가?


## 3.3 Shell Script 문법 : 

+ #(으로 시작하면) : 주석
   - (예외 : #!/bin/bash >> #!가 /bin/bash에서 실행시켜야 한다고 명시해 주는 역할을 한다)

+ echo "" : 출력문(따옴표 안에 내용넣으면 된다.)
+ pwd : 현재 위치한 디렉토리 

+ ls : 파일 조회
    
   - ls -a : 모든 파일 조회(숨김 파일까지 조회)
      (Linux에서는 .으로 시작하는 파일들을 숨김 파일로 간주함)

   - ls -l : 파일 목록을 자세히 조회
   - ls -al : 모든 파일에 대한 목록을 자세히 조회
    
+ vi myprog.sh >> vi 편집기 실행
   - vi 위에서 ':'(colon) 누르기 : 명령어 실행으로 감
   - (vi에서) esc : 실행 모드에서 빠져나오기,
   - (vi에) a 또는 i : 삽입이 가능한 모드.
   - (vi에서) : 누른 후 wq : 저장하고 빠져나오기

+ **Shell Script 만든 이후 실행하는 방법 3가지!**
   1. chmod(파일 실행 권한 관련) : 
      
      - chmod +x ./myprog.sh >> 실행시킬 수 있게 해준다! (Excutable하게) (이후 ./myprog.sh 실행하면 그것 그대로 일련의 명령어들이 
      순차적으로 실행되는 것을 볼수있다)
      - (번외) 맨 앞의 l : 링크, 소프트링크(클릭하면 어느경로로 가라고 알려주는 것)

      - (Shell Script는 필요한 명령어들을 한방에 실행시킬 수 있다는 장점이 있다!)

   2. 특정 무엇인가를 쳤을 때, shell script에서 뭔가를 가져와서 실행시키려 하면 어떻게 해야 하나?(입력)
      - set A B C D 하면 $1 $2 $3 $4에 각각 저장된다. 
      - 출력 시에는 "echo $*" 하면, argument에 들어간 A B C D가 쭉 출력이 된다. 

      - $0에는 파일의 이름이 argument로 들어간다. $1 $2 $3~ $9까지, C언어의 argv가 들어간다고 생각하면 된다 .

+ **Shell 상에서 연산하기**
   - 값 할당 :
   <pre><code>#!/bin/bash
   
   a = 10
   b = 20
   sum = $(($a + $b)) // 값을 연산에 이용하려면, 이렇게 앞에 달러 글자를 붙여주면서 진행한다.
   echo $sum // 부를 때도 요런 식으로 해준다.
   </code></pre>
   

  **[제어문]**

#### if statement 

<pre><code>
 if command
 then 
     statement
 fi
</code></pre>

#### if-else statement
<pre><code>
if [ condition ]; then
    statement
elif [ condition ]; then
    statement
else
    statement
fi
</code></pre>

   - and, or, not은 같으나, 소괄호 말고 전부 대괄호로 처리한다는 차이가 있다. and나 or은 괄호 두개로 묶어서 확실하게 처리하기.
           (대괄호 두개로 묶어야한 한다고 한다)
   - 키워드 사이에 싹 다 띄워쓰기 해야 할 것 같다. 지키자!
        
#### Case Statement

<pre><code>
case word in
   pattern1) command-list
   ;;
   pattern2) command-list2
   ;;
   pattern3) command-list3
   ;;
esac >> 이렇게 뒤집어 주기.
</code></pre>
        
#### While Loop
<pre><code>
while [ expression ]
do
   command-list
done
</code></pre>

#### For Loop

<pre><code>
for i in 1 2 3 4 5 6 7 <- list
do 
    command-list
done
</code></pre>

#### Continue and Break

이것도 말그대로, 원래 쓰임새에 맞게 쓰면된다     
    
+ 비교구문 : 
   - gt : ~보다 높은(greater than)
   - ge : ~보다 높거나 같은(greater than or equal)
   - lt : ~보다 낮은(less than)
   - le : ~보다 작거나 같은(lass than or equal)
   - eg : ~와 같은(equal)
   - ne : ~와 같지 않은(Not equal)

+ File Testing
   - d file : 디렉토리에 있는 애 이름이냐?
   - r file : 읽을수 있는가?
   - w file : 쓸 수 있는가? 쓰기에 접근할 수 있는가?
   - x file : 실행가능한 상태의 파일인가?
   - s file : file의 길이가 0이 아닌가?
    
#### 함수
+ 사용하는 이유 : 코드를 재사용하기 위함. 
     
     while loop example2 해보기

+ 지역 변수 
   - 해당 script에서만 동작하는 코드.

      (ps -ef : 프로세스를 보고, 원하지 않는 것을 종료시킬때 사용함)

   - pid - 실행중인 프로세스는 각각의 고유의 id, 즉 pid 라는 것을 갖는다!
      >> 1번은 "리눅스를 시작시키는" 프로세스에 대한 ID

      ppid - 해당 process의 부모 프로세스의 id
      
   - **함수 호출시** : 선언할 때는 앞에다가 괄호 붙이지만, 뒤에 이용할 때는 괄호 없이 바로 입력하면 된다.

#### 강제종료(리눅스)
+ Signal : IPC(Inter-Process Communication ) 
   - 다른 프로세스에 신호를 보내주는 방식.
+ 비동기적인 방식 
   - 실행 중이더라도 언제나 호출해서  전달할 수 있는 방식. 
+ 해당 프로세스에서 실행되는 이벤트를 전달한다 .

+ 강제종료 명령어 : 
   - kill (PID 번호) - 종료시키는 명령어
   - kill -9 (PID 번호) - 강제종료시키는 명령어. 얘는 Killed 하고 자기가 죽었다는 표시를 내준다. 

+ Shell Script에서는 변수의 type을 명확히 선언해 주지 않는다.
+ Shell Script에서는 변수 선언 시 어떻게 해야 하는가? 
   - 띄워쓰기 하면안된다. 
        TEST=0 (O) / TEST = 0 (X) <띄워쓰기 ㄴㄴ>

#### 환경 변수 : 
+ (지역) 환경 변수
+ 전역 환경 변수 : 
   - export라는 키워드를 사용함.
+ 변수 사용 방법
   - echo $TEST
   - echo ${TEST}  (값을 더 명확히 하기 위해서 사용) >> 두가지 방법이 있다. 
   - echo $TEST+1 vs ${TEST+1} 차이 :
   
        - TEST가 0이라 하면, 앞에거는 0+1로 출력
        - 뒤에거는 1로 출력된다! 차이 알고 쓸 것!

+ 환경 변수를 사용할 때 문자열 내에서의 사용
   - 수식과 함게 사용 등의 이슈가 있을 때는 ${변수명} 식으로 사용

#### Shell Script와 주석
+ 주석이 잘 되어야 읽는 사람이 해당 소스코드/스크립트를 읽고 이해하는 사람에게 큰 도움을 준다. 
+ 첫줄은 반드시 #!{실행기} <- /bin/bash
      (참고)  #! 를 "Shebang"이라고 이야기하기도 함. 
+ 그래서 첫줄부터 주석을 쓰지는 말자!


#### (번외) 
+ 쉘 스크립트 활용도가 높은 몇 가지 사례
      1. 어떤 명령어의 출력 결과물을 변수에 저장하거나, 다음의 입력물로 활용하는 경우 
           1.1 pipe ( | ) : 왼쪽 실행 명령어의 결과가 입력으로 사용됨
           1.2 ` ` (역따옴표, 1옆에 있는거) : 실행 결과가 텍스트가 되어서 변수에 대입 해주는 식으로 활용 가능.

      2. sort / 3. awk / 4. sed
      
+ (번외2) ls -al | grep ~~~ : ~~~로 되어 있는 것만 필터링 해서 보여주는 기능!

#### Array
+ declare -a 명령어로 배열을 선언한다.
+ 혹은 바로 배열을 만들수도 있다.
<pre><code>
declare -a sports // 선언식
sports = (ball frisbee puck) // 항목을 안에 넣어서 만들어주는 Array
moresports = ( ${sports[*]} tennis ) // 위의 sports 안에 tennis를 추가해서 배열을 만들어줌.
</code></pre>     
