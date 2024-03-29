# 주제: OAuth(Open Authorization)
### OAuth(Open Authorization)이란 무엇인가?
> OAuth 2.0 is the industry-standard protocol for authorization. OAuth 2.0 focuses on client developer simplicity while providing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices. \- oauth.net

OAuth 2.0은 권한 부여를 위한 업계표춘이다. 웹 앱이나 데스크탑 앱, 모바일, 그리고 리빙 룸 디바이스들을 위한 특정 권한 부여 flow를 제공하면서 클라이언트 개발자의 단순성에 중점을 둔다. 이러한 명세와 확장은 IETF OAuth Working Group에서 개발된다.  
설명은 이렇게 복잡해보여도 우리가 아는 '카카오톡으로 로그인하기', 'Google로 로그인하기'가 이에 해당한다.  
어떤 웹사이트에서 카카오 계정이나 Google 계정의 정보에 접근권한을 안전하게 부여할 수 있는 개방형 표준이다.  

<br>
<br>

### 왜 필요할까?
어느 순간부터 웹 서핑을 하다보면 심심치 않게 회원가입창에서 OAuth를 찾아볼 수 있다.  
그럼 OAuth가 왜 필요하고 어떻게 사용될까?  
1. 쉬운 웹 사이트 가입을 위해 (사용자의 입장에서)
2. 어떤 웹 사이트에 필요한 정보를 신뢰가능한 서비스 제공자로부터 안전하게 제공받을 수 있기 때문 (웹 개발자의 입장에서)

즉, 1번을 위해 개발하다보니(물론 다른 이유도 있었겠지만) 어떻게 하면 다른 서비스의 정보를 신뢰성 있게 주고 받게 할 수 있을지 고민한 결과, OAuth가 탄생하게 된 것이다.

<br>
<br>

### OAuth를 이해하기 위한 등장인물
상황: 컴퓨터 쇼핑몰에 접근하려는 A씨가 카카오로 로그인을 하려는 경우  
1. 사용자(User): 쇼핑몰을 이용하려는 A씨
2. 서비스 제공자(service provider): A씨의 정보를 알고있는 카카오
3. 소비자(Consumer): 카카오의 OAuth API를 이용하여 카카오에 접근하는 컴퓨터 쇼핑몰 웹 사이트

<br>
<br>

### OAuth의 Flow
컴퓨터 쇼핑몰을 카카오 로그인을 통해 사용하려는 A씨의 일화이다. 
1. A씨가 컴퓨터 쇼핑몰에서 매우 마음에 드는 스팩의 컴퓨터를 찾았다. A씨는 컴퓨터를 사려했지만 회원가입 후에 구매할 수 있었다. A씨는 회원가입창에서 카카오로 로그인 버튼을 클릭한다.
2. A씨가 카카오로 로그인 버튼을 클릭한 순간, 컴퓨터 쇼핑몰에서 카카오 API에 ``요청토큰(Request Token)``을 요청한다.
3. 카카오는 컴퓨터 쇼핑몰에 요청토큰을 발급해준다.
4. 컴퓨터 쇼핑몰은 A씨를 카카오 로그인창으로 이동시킨다. 여기서 A씨는 카카오에 본인의 계정으로 로그인한다.
5. 카카오는 A씨를 다시 컴퓨터 쇼핑몰로 이동시킨다.
6. 컴퓨터 쇼핑몰은 카카오에 ``접근토큰(Access Token)``을 요청한다.
7. 카카오는 접근토큰을 발급해준다.
8. 컴퓨터 쇼핑몰은 발급된 접근토큰을 이용하여 A씨의 정보에 접근한다.

<br>
<br>

### 접근 토큰(Access Token)
임의의 문자열 값이며 서비스 제공자가 생성한 값이다.  
접근 토큰은 사용자가 서비스 제공자에게 본인 계정을 인증(로그인)한 경우 발급해준다.  
물론, 해당 접근 토큰을 소비자가 받는 방법은 여러가지가 있다. 가장 일반적인 방법에 대해 알아보자   
1. 직접 복붙하기: 서비스 제공자 측의 인증 후, 서비스 제공자는 단지 접근 토큰만 제공하고, 소비자 측에서는 폼으로 접근 토큰을 입력받게 함.
2. Redirect: 서비스 제공자에 로그인 인증 후, 소비자 측의 사이트로 Query String과 함께 토큰값을 받아올 수 있다. 

<br>
<br>

### 리다이렉트에서 XSS공격이나 피싱사이트에 의한 redirect_uri 조작
만약 XSS공격이나 피싱사이트에 의해, redirect_uri를 조작하여 악의적인 사이트로 서비스 제공자에게 사용자의 정보를 탈취하면 어쩌지? 라는 의문이 생길 수 있다.  
이런 경우를 대비하여 OAuth를 사용하기 위해 소비자측은 서비스 제공자로 하여금 본인들의 사이트 정보를 등록해야한다.  
서비스 제공자는 등록된 소비자 사이트만 OAuth를 사용하여 사용자의 정보를 구할 수 있도록 설계한다.




<br>
<br>
<br>
<br>

### 출처
https://ko.wikipedia.org/wiki/OAuth  
https://oauth.net  
https://tecoble.techcourse.co.kr/post/2021-07-10-understanding-oauth/  
https://velog.io/@undefcat/OAuth-2.0-%EA%B0%84%EB%8B%A8%EC%A0%95%EB%A6%AC  
https://developers.kakao.com/docs/latest/ko/kakaologin/rest-api  




[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/

