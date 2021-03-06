# 주제: FTP 프로토콜 
### 📌 FTP 프로토콜이란?
FTP란 파일 전송 프로토콜(File Transfer Protocol)의 약자

<br>
<br>

### 📌 프로토콜은 뭔데요?
프로토콜은 컴퓨터 내부에서, 또는 컴퓨터 사이에서 데이터의 교환 방식을 정의하는 규칙 체계.  
FTP는 `TCP/IP` 네트워크(인터넷)상의 장치가 파일을 교환할 때 사용하는 규칙.  
특히, FTP는 클라이언트 - 서버 사이의 데이터 교환에 사용하는 프로토콜이다.

<br>
<br>

### 📌 FTP에 대해 더 자세하게 설명해주세요.
클라이언트 - 서버 사이의 데이터 교환이기 때문에 클라이언트와 서버 중심으로 전개된다.  
클라이언트가 서버에 접속하면 두 개의 연결이 생성된다.  

1. `명령연결`
2. `데이터 전송용 연결`  
  2-1. `Active 모드`  
  2-2. `Passive 모드`  
  
<br>
<br>

### 📌 명령연결은 뭔가요?
데이터 전송을 제어하기 위한 신호를 주고받기 위한 연결.
제어포트 21번을 사용하여 사용자 인증, 명령을 위한 연결이 형성되고, 이를 통해 클라이언트에서 지시하는 명령어가 전달된다. 

<br>
<br>

### 📌 데이터 전송용 연결은?
실제 데이터 송수신에 사용되는 연결. 20번 포트를 사용한다.  
이는 상황에 따라 두 가지로 나뉘는데 이의 기준은 '포트 정보를 누가 주느냐'에 따라 정해진다.  
`Active 모드`에서 포트 정보를 주는 주체는 '클라이언트'고 `Passive 모드`에서 포트 정보를 주는 주체는 '서버'이다.  

<br>

#### 포트 정보를 누가 주느냐의 의미는??  
> (A가 포트번호를 B에게 주었다.)  
> A: "나 이 포트로 너의 데이터를 받을테니 데이터를 이쪽으로 보내주면 돼!'  
> B: "ㅇㅋ 데이터 간다!"  

<br>

![image](https://user-images.githubusercontent.com/93513959/168470507-ebabb354-3b61-4ff6-9d64-fa1156fe4e18.png)

출처: 가비아 라이브러리, https://library.gabia.com/contents/domain/2560/

정리하자면, `Active 모드`, `Passive 모드` 둘 다 누구의 입장으로 생각하면 될까?  
바로 ____ 의 입장으로 생각하면 된다!  

<br>
<br>

### 📌 FTP! 단점도 있나요??
FTP는 간단하게 파일 송수신을 진행할 수 있기 때문에 기존 웹에서 파일을 다운 받는 것보다 대량으로 쉽게 파일을 주고 받을 수 있다는 장점이 있지만  
FTP는 간단하게 파일 송수신만을 목적으로 만든 프로토콜이기 때문에 수많은 보안 취약점이 존재한다.

- 무차별 대입 공격
- FTP 바운스 어택
- 패킷 가로채기
- 포트 훔치기 (다음에 열릴 포트를 추측하여 적절한 연결을 빼앗는 것)
- 스푸핑 공격
- 사용자 이름 열거  

<br>

출처: https://datatracker.ietf.org/doc/html/rfc2577

때문에 FTP보다는 보안성이 고려된 FTPS나, SSH 프로토콜을 사용한 SFTP 등을 선호하는 추세다.



<br>
<br>
<br>

### 📌 참고자료 
https://namu.wiki/w/FTP  
http://wiki.hash.kr/index.php/FTP#cite_note-3  
https://ko.wikipedia.org/wiki/%ED%8C%8C%EC%9D%BC_%EC%A0%84%EC%86%A1_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C  
https://library.gabia.com/contents/domain/2560/  
https://datatracker.ietf.org/doc/html/rfc2577  
  
