# Chapter 25. Multimedia

+ 인터넷에서 동영상 볼때 등 사용함
+ 멀티미디어 : 여러 개의 미디어.
  - 한 개의 media인데 섞여 있다. 
  - ex) 동영상 : 영상, 텍스트 등이 섞여 있을 수 있다. 

+ 인터넷 상에서 주고받는 것은 크게 3가지 type으로 구별할 수 있다. 
  - Streaming Stored Audio/Video(녹화방송, VOD)
    - 그냥 TCP로 안전하게 주고받아도 된다.
    - On-Demand Request : 압축된 Audio/Video 파일을 다운받는다. 
    
  - Streaming Live Audio/Video(생방송, 생중계)
    - 안전하게 주고받는것도 중요하지만, Real-Time 이 되어야 하는 것도 중요하다.
    - 안전하게 해도, 10분 뒤에 오면 의미가 없다. 
    - Broadcast 라고도 한다. 
    
  - Interactive Audio/Video(대화형, 양쪽으로 주고받음, 게임형)
    - Conference 라고도 함(Zoom, 전화 등)
  
  - 아래로 내려올 수록 난이도가 높아진다. 올라갈수록 쉽다. 
  
### DIGITIZING AUDIO AND VIDEO

+ 이런걸 할려면, 인터넷 상에서 디지털 정보를 주고받는 것인데, 그럴려면 모든 아날로그 정보를 0과 1로 다 바꿔야 한다. 
  - 이런 과정을 보고 Digitizing 이라고 한다. 
  - Digitizing Audio(오디오를 디지털화)
  - Digitizing Video(비디오를 디지털화)

+ 바꾸면서 압축도 된다
  - 압축을 얼마나 세게 하냐에 따라 효율성이 좋은지 나쁜지 결정되기도 한다. 
  - 압축 하지 않고 그냥 원본 데이터를 보내면, 용량이 대단히 크고, 실시간 통신이 불가능하다. 
  - 그러므로 압축은 꼭 필요하다!

+ 오디오 & 비디오 압축기술
  - Video 압축 : JPEG(image 압축) / MPEG(video 압축)
  - JPEG(Joint Photograph Expert Group) : 사진 압축 전문가 그룹
    - 사진을 8 byte pixel 로 쪼개 놓고, block 화를 시킴. 
    - 8 by 8 matrix가 기본 단위이다. 
    

  - MPEG(Moving Picture Expert Group) 

