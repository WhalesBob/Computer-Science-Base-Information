# Chapter 21. File Transfer : FTP and TFTP

### FTP(File Transfer Protocol)

+ FTP를 구현한 Protocol 이 많다. 
+ 파일 다운로드, 업로드할 때 사용한다. 
+ FTP의 underline은 TCP를 사용한다. (오랫동안 해야해서)
+ FTP는 2개의 connection 사용한다
  - 21번은 control connection을 위한 Port
  - 20번은 data connection을 위한 Port
  - 한 Port에 섞여 버리면 어디가 control, 어디가 data인지 구별할 수 없을 것이다.
