# Chapter 4&5_Python

## 4.1 Python Language

+ 파이썬이란?
  - High-Level이며, 일반적으로 많이 쓰이는 프로그래밍 언어 
  - Guido van Rossum 이라는 사람이 만듬(1991).
  - 오픈소스로써 구현되었으며, 세계의 많은 프로그래머들이 개발하고 유지보수함.
 
+ 코드의 가독성
+ 객체지향언어
+ Dynamically Typing(슈도코드처럼 쓸 수 있는 특성을 이야기하는 것 같다.)

+ 인터프리터 언어이다
  - 한줄씩 기계어로 번역해서 바로바로 실행한다 
  - 많은 OS(Window, Linux 등)에서 사용가능하다.

## 4.2 Python 문법

#### 들여쓰기

+ 중괄호로 묶을 필요가 없다.
+ 들여쓰기로 해결한다.(탭)

<pre><code>
if True :
    print "True"
else:
    print "False"
</code></pre>

+ **탭이 아니라 스페이스로 하면 에러난다!!**
    
#### 주석
+ 여러 줄을 주석처리 할 때는, 다른 언어의 경우
<pre><code>
/* 주석주석주석 */
</code></pre> 

로 해결한다. 하지만 파이썬에서는, 

<pre><code>
"""  ~~~~~~~~~~~~~~ """ // (큰따옴표 3개)
</code></pre>

로 해결한다!

#### Python에서의 데이터 타입

+ Numeric(숫자) 타입 : (계산은 여타 다른 언어와 같다)
  - 정수 : 무한정 늘릴 수 있다는 것 같다.(기능구현이 되어 있음)
    - Integer
    - Long
  - float 
  - complex(복소수)

+ Sequence Types(데이터에 순서가 존재하는 Type) :
  - range(객체) : 
    - 아예 그냥 range라는 객체가 따로 존재한다.
    - range(1,10,1) 해주게 되면, 1부터 '9'까지! 하나씩 증가시켜가며 늘어가게 된다. 마지막수가 2면 1,3,5... 이렇게 간다.
    - range(10) : 0부터 9까지 / range(MIN,MAX) : MIN부터 MAX-1까지 1씩 증가 

  - list
    - 데이터들을 잘 관리하기 위해 묶어서 관리할 수 있는 "자료형"(Data Type) 중 하나이다! 라고 정의되어 있다.
    - 대괄호를 이용해서 정의할 수 있다
    <pre><code>
    a = [1,2,3,4,5] 
    b = ['blockdmask',2,4,'blog']
    c = []
    d = list()
    </code></pre>
    - list 내부에 String이 오든, 숫자가 오든, 데이터 타입이 통일되어 있지 않아도 상관없다고 한다. 
    - 그냥 "객체"의 Array이라고 생각하면 된다.
    - c에는 아무것도 넣지 않은 대괄호가 있는데, 요소가 비어 있는 list이다. 
    - d처럼, list()을 이용해 리스트 타입의 객체를 만들 수 있다. 이때, 해당 list는 비어 있다.
    - 수정가능(mutable) 하다.
    <pre><code>
    [1,2,3] + [4,5,6] -> [1,2,3,4,5,6]
    ['Ni'] * 4 -> ['Ni','Ni','Ni','Ni']
    str([1,2]) + "34" -> '[1,2]34'
    [1,2] + "34" -> 에러
    3 in [1,2,3] -> True // in 키워드!! 리스트에 요소를 찾을 수 있다.
    
    L = ['spam' ,'Spam', 'SPAM!']
    L[1] = 'eggs'
    L -> ['spam', 'eggs', 'SPAM!']
    
    L = [1,2,3,4,5]
    L[1] -> 2 
    L[-1] -> 5
    L[-2] -> 4 // - 붙이면 거꾸로 들어간다.
    </code></pre>
      - List Slice : list[start:end+1:(step)]
    <pre><code>
    L = [1,2,3,4,5]
    L[0:3] -> [1,2,3]
    L[:2] -> [1,2]
    L[2:] -> [3,4,5]
    L[:] -> [1,2,3,4,5]
    L[0:5:2] -> [1,3,5]
    L[:5:2] -> [1,3,5]
    L[::2] -> [1,3,5]
    </code></pre>
      - Mutable Assignment
    <pre><code>
    L = [1,2,3,4,5]
    L[1] = 2.5
    L -> [1,2.5,3,4,5]
    L[2:4] = [3.5,4.5]
    L -> [1,2.5,3.5,4.5,5]
    L[2:3] = [3.7,3.9] 
    L -> [1,2.5,3.7,3.9,4.5,5] // 끼워넣기도 가능
    L[2:2] = [3.5,3.6]
    L -> [1,2.5,3.5,3.6,3.7,3.9,4.5,5] // 아무것도 안 바꾸고 2 자리에 그냥 삽입도 가능. 
    L[2:3] = [] 
    L -> [1,2.5,3.6,3.7,3.9,4.5,5] // list[2]를 삭제하는 경우. 다 당겨짐.
    del L[3:5] // 3,4번째 지움.
    L -> [1,2.5,3.6,4.5,5]
    </code></pre>
      - len(s) : s의 길이
      - min(s) : s에서 가장 작은 애
      - max(s) : s에서 가장 큰애
      - sum(s) : s 항목을 모두 더한 total
      - s.append(x) : 맨끝에 x 더하기
      - s.clear() : 항목 다 지우기
      - s.copy() : 얕은복사(그냥 주소값만 찍는것)
      - s.extends(t) or s+=t
  - tuple
    - 불변하는(immutable), 순서가 있는 객체의 집합인 "자료형"(Data Type).
    - list형과 비슷하지만, 한 번 생성되면 값을 변경할 수 없다고 한다. 
    - 소괄호 "()"로 정의하고 나타낼 수 있다.
    - 순서가 있기 때문에, 인덱스로 접근가능하며, len 내장함수로 길이를 구할 수 있다. for loop도 돌수 있음.
    - '+' 연산으로 tuple(튜플)을 추가할 수 있고, * 연산을 이용하여 tuple(튜플)을 반복시킬 수 있음.
<pre><code>
 t = (1,'korea',3.5,1 )
 t = t + (3,5)
 t
 ( 1,'korea',3.5,1,3,5)
 t * 2
 (1,'korea,3.5,1,3,5,1,'korea'3.5,1,3,5) // 두번 반복했다.
</code></pre>
    
    - 튜플 속에 튜플이 포함될 수도 있다. 
    - 튜플에 하나의 원소만 존재하는 경우에는, tuple(튜플)이 되지 않지만, 회피하는 방법이 존재한다. 한개의 원소뒤에 콤마 찍어주면 튜플이 된다.
    - tuple에 괄호가 필수조건은 아니라고 한다
    - 튜플을 이용하여 함수에서 여러 값을 한번에 리턴시킬 수도 있다. 변수도 한꺼번에 할당가능하다.
    - 
    <pre><code>
     >>> p = 1,3,2,5,7
     >>> type(p) 
     <class 'tuple'>
    </code></pre> 

+ Text Sequence Type
  - str (string)
  
+ Set Type

  - set/frozenset : 
    - 집합에 관련된 것을 처리하기 위해 만들어진 자료형이다.
    - set 키워드를 사용하거나 중괄호를 이용해 표현할 수 있다.
    - 아래의 3개(s1~s3) 다 같은 집합을 만든다.
    <pre><code>
    s1 = set({1,2,3})
    s2 = set([1,2,3])
    s3 = {1,2,3}
    s4 = set()
    </code></pre>
    - 비어 있는 집합을 만들기 위해서는 s4와 같이 진행한다.
    
    
+ Mapping Type
  - dictionary : key : value pair로 이루어진 자료형
  
+ 비교연산
  - is : Object의 주소값을 비교함.(같은 '객체'면 true) 
    - id(a) -> 주소값
    - a is b -> boolean 반환, 동일 객체인가?
  
  - x < y <= z 와 같은 연산 가능. (한방에 비교가능하다)
  
+ boolean 연산
  - and/or/not : 직접 키워드로 만들었나보다. 원래 ||, &&, ! 들어갈 자리에 저렇게 키워드로 만들어놓았다.
  
+ 주요 함수들(차이점만 서술함) 
  - if 문

<pre><code>
  if(statement) : // 중괄호가 아닌 colon(:)
      command
  elif(statement) :  // else if 가 아닌 elif
      command
  else :

</code></pre>

  - for문 
  
<pre><code>
  for <variable> in range(a,b,c) : 
  // for(int i = 0; i < n ; i++) 로 하지 않고, range 객체를 이용해 처리하고 있다.
  // enhanced for 같은 느낌이다.
</code></pre>

  - string
    - 큰 따옴표면 큰따옴표, 작은 따옴표면 작은 따옴표 둘중하나로 씌우면 된다. 내부에 같은 따옴표면 안되지만, 다른 따옴표 그냥 넣는것 가능.
    
  - print 함수
    - 콤마(,)로 구분하면 자동으로 띄워쓰기된 것으로 나온다
    - sep=~~ 로 변환할 수 있다. 저 자리에 "," 넣으면 띄워쓰기 대신 콤마가 들어가는 식
    - 자동으로 print에 개행문자 "\n" 이 들어간다.
    - 역시 end=~~ 로 해당 기능을 다르게 해줄수 있다.

  - String Formatting
    - formatting 연산자 '%'
    - 물론 위에서, formatting 해줘야 할 애가 하나면 굳이 괄호 안씌워도 된다.
    <pre><code> print("my name is %s and weight is %d kg" % ('Tom",60) </code></pre>
      
  - ".format() : formatting 함수!
  <pre><code> print("the sum of {0}+{1} is {2}".format(1,2,3)) </code></pre>
  
  - {0:<10} : {0} 값을 10자리로 표현하는데, 왼쪽 정렬한다!
  - {1:>5} : {1} 값을 5자리로 표현하는데, 오른쪽 정렬한다!

  - ASCII 관련 함수
    - ord(text) : text를 ASCII 숫자로 바꾸어 주는 것.
    - chr(number) : 숫자를 ASCII 테이블에 연동하여 해당하는 character 로 만드는 것.
    
* * *

### 각종 유용한 함수 
 
#### .split 함수
+ 문자열.split() 
  - 띄어쓰기, 엔터를 구분하여 문자열을 나누게 된다.(Default)
  - 나눌 수 있을때까지 나누게 된다

+ 문자열.split('문자') = 문자열.split(sep='문자')
  - 해당 <문자>를 기준으로 하여 나누게 된다. 
  
+ 문자열.split('문자', 숫자) = 문자열.split(sep='문자', maxsplit=숫자)
  - <문자>를 기준으로, maxsplit 숫자만큼만 띄우고, 나머지는 split하지 않는다.
  
  
#### dict.get(keyword,number) 
+ 해당 keyword 에 대응하는 value를 반환하고, 없으면 keyword : number 로 새로 저장함.

#### dict.item() : key : value 쌍을 반환
