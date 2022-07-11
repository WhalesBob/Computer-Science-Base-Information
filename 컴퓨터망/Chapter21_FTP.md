# Chapter 21. File Transfer : FTP and TFTP

### FTP(File Transfer Protocol)

+ FTP를 구현한 Protocol 이 많다. 
+ 파일 다운로드, 업로드할 때 사용한다. 
+ FTP의 underline은 TCP를 사용한다. (오랫동안 해야해서)
+ FTP는 2개의 connection 사용한다
  - 21번은 control connection을 위한 Port
  - 20번은 data connection을 위한 Port
  - 한 Port에 섞여 버리면 어디가 control, 어디가 data인지 구별할 수 없을 것이다.
  
<img src="images/CompStart_Ch21_1.png"/>  

+ FTP
  - 멀리 있는 사람이, 서버에서 파일을 업로드하거나 다운로드 받는 것.
  - Connect가 2개 있다.
    - Control Connection : 이것부터 먼저 시작함. 
    - 필요하면 데이터 업로드하거나 다운로드 할 수 있다. 
    - Control 은 Port 21번으로 열고 있다가, Client가 접속해 오면 Control Channel 이 시작된다. 
    - Data Connection
    - 필요하면 파일을 구체적으로 다운로드 해야 함. 
    - 파일 내용 자체는 Data Channel로 주고받는다. 데이터만 이 채널로 주고받음.

<img src="images/CompStart_Ch21_2.png"/>  
    
+ Opening the control Connection
  - Control 정보가 망을 지나갈 때 역시 NVT Format으로 통일시켜서 간다. 

<img src="images/CompStart_Ch21_3.png"/>

+ Creating the data Conneciton
  - Data 만 가는 Data Connection 이 별도로 존재한다. 
  - Control  쪽에서 Command를 주고받을 때 보내는 것이 Command/Response
    - DHCP는 Request/Reply 였음.
    - DNS는 Query/Response 였음.
    - 약간씩 표현이 다르지만, 보내는것/받는것임.
  - Command도 여러 가지 할 수 있고, Response도 여러가지 할 수 있다.
  - Command 종류(다양함)
    - Access (접속) 에 관한 Command
    - File 관리에 관한 Command
    - Data Formatiing에 관한 command
    - Port 정하는 Command
    - File Transfer Command
    - Miscellaneous(기타) Command
  
  - <img src="images/CompStart_Ch21_4.png"/>
  
  - Response 
    - 처리결과를 알려주는 애
    - 숫자 3개로 simple 하게 이야기한다. 
    - 100 번대 : 완전히 끝난 것이 아님.(예비)
      - 긍정적인데 예비 응답. 아직 안끝나고 진행중.
      
    - 200 번대 : 완전히 성공적으로 끝남
    - 300 번대 : Positive 하긴 하지만, 후속 작업이 필요하다는 의미. 
    - 400 번대 : Negative. 아직 안되었는데, 일시적으로 안된 것.
    - 500 번대 : 완전히 안 된것. 
    - 이렇게 3자리의 응답코드로 응답을 준다. 
    - 요청한 것에 대해 잘 되었는지, 진행중인지, 번호별로 왜 안되었는지에 대한 정보를 모두 준다. 
    - 구현하는 입장에서, 이 코드정보를 알아야(왜 안되는지 알아야) 그 다음 Action을 취할 수 있다. 
 
+ File Transfer
  - 데이터를 저장할 수 있고(Storing a file), 데이터를 당겨 올 수 있다(Retrieving)
  - 파일을 당겨올 수도 있고, 목록을 당겨 올 수도 있다. 
  - 보통 목록 보고, 파일을 당겨 올 것이다. 

<img src="images/CompStart_Ch21_5.png"/>

+ 실제 Flow로 보는 사례
  - 먼저 Cliet가 Control Process를 열고, 필요한 정보를 주고받는다.
    - 협상, ID/PW 로그인, Port 번호 어떤 것을 쓸지 등등 정함.
    - List 주고받으며 어떤 파일(Directory)이 있는지 보냄. 
    - 물론 파일 내용 자체는 Data Connection으로 주고받아야 함. 
    
  - Data Connection 이 생성됨.
    - 필요한 정보(Data Information)를 알려줌.
    - 파일을 다운로드, 지우기, 업로드(Store), 
  
  - Control 정보를 주고받다가, 필요한 경우에 Data Connection을 연결해서 사용하는 구조이다. 
  - Control : 21 / Data : 20번!
  
+ FTP 정리
  - Underline : TCP
  - Port 번호 : 20 , 21
  
### TFTP()
