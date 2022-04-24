# Chapter3. 정보의 표현

**중요한 부분만 정리하고, 계산하는 부분은 제외**

#### 컴퓨터의 자료 표현
+ bit (**bi**nary digi**t**) : 이진 숫자. 0이나 1을 가질수 있는 최소값. 그냥 이진수 한 자리라고 생각하면 된다.
+ nibble : 4개의 bit가 모여서 생김. 4bit = 1 nibble
+ byte = 8개의 bit가 모여서 생김. 8bit = 1 byte
+ word : 1 word는 컴퓨터에 따라 다름. 
    - 32bit 컴퓨터에서는 1 word = 32 bit이므로, 1 word = 4 byte
    - 64bit 컴퓨터에서는 1 word = 64 bit이므로, 1 word = 8 byte
    - 명령이나 데이터들을 가져올 때, 한 번에 가져올 수 있는 데이터의 최고 크기를 1 word 라고 한다.

#### 저장 용량 
+ 저장 용량 : 파일이나 주기억장치, 저장장치의 크기는 byte 단위로 표기한다.

+ 단위
  - 1 B  (Byte)      = 1 Byte(2^0)       -> 8bit
  - 1 KB (KiloByte)  = 2^10 Byte(1024B)  -> 1/2 페이지 분량
  - 1 MB (MegaByte)  = 2^20 Byte(1024KB) -> 책 한권 분량
  - 1 GB (GigaByte)  = 2^30 Byte(1024MB) -> 영화 한 편 분량
  - 1 TB (TerraByte) = 2^40 Byte(1024GB)
  - 1 PB (PetaByte)  = 2^50 Byte(1024TB)
  - 1 EB (ExaByte)   = 2^60 Byte(1024PB)
  - 1 ZB (ZettaByte) = 2^70 Byte(1024EB)
  - 1 YB (YottaByte) = 2^80 Byte(1024ZB)

#### Sign and Magnitude
+ Sign-and-Magnitude 표현 : 부호만 다르고 양수크기와 같도록 처리하는 것
  - +3 = 0011
  - +5 = 0101
  - -5 = 1101 
  - 컴퓨터에서 부적합
    - 피연산자 부호 다를때, 크기비교/뺄셈 회로 피료하다. 컴퓨터에서 사용하지 않는다.
    

+ 1's Complement : 관련된 양수에서 부호 포함하여 단순히 2진 표현을 반전처리함.
  - -3 = (0011)->(1100)
  - -5 = (0101)->(1010) 
  - 산술 연산에서 추가 덧셈회로가 필요하다.

+ 2's Complement : 관련된 양수에서 1의 보수표현 + 1 해줌.
  - -3 = (0011) -> (1100) -> 1101
  - -5 = (0101) -> (1010) -> 1011
  - 컴퓨터에서 실제 사용
