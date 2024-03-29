# 주제: Virtual DOM
### Virtual DOM이란 무엇인가?
> Virtual DOM (VDOM)은 UI의 이상적인 또는 “가상”적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 “실제” DOM과 동기화하는 프로그래밍 개념입니다. 이 과정을 재조정이라고 합니다.  
> \- 리액트 공식문서  

말 그대로 가상 DOM으로, 모든 조작을 Virtual DOM에서 지지고 볶고 다 한 후에 실제 DOM에 동기화하기 위해 만든 가상의 자바스크립트 객체다.  

<br>
<br>

### 브라우저의 랜더링 과정에서 DOM
브라우저 랜더링 과정에서 DOM은 생각보다 비효율적으로 작동한다.  
DOM에 변화가 일어난 경우, 랜더트리를 재생성하기 때문에 모든 요소들의 스타일이 재계산된다.  
SPA(Single Page Application)의 경우, DOM을 조작하는 일이 잦기 때문에 브라우저가 비효율적으로 일을 처리할 수 밖에 없고, 이런 문제를 처리하기 위해 Virtual DOM의 개념이 등장한다.  

<br>
<br>

### Virtual DOM의 동작원리와 Virtual DOM의 역할 고찰
뷰에 변화가 일어날 경우, 그 상태변화를 Virtual DOM에 먼저 적용시킨다.  
Virtual DOM은 랜더링이 일어나지 않기 때문에 실제 DOM을 업데이트하여 연산시키는 것보다 효율적이다.  

정리하자면, Virtual DOM은 DOM flagment을 자동으로 모아주고 업데이트하여, 기존의 DOM에 적용한다.  
사실 이 과정은 Virtual DOM이라는 개념이 없어도 가능하다.  
우리가 DOM의 상태변화가 일어나는 부분을 따로 인지하고 한꺼번에 DOM을 업데이트하면 DOM은 리플로우 발생을 최소화하여 효율적인 랜더링을 할 수 있다.  

그럼 Virtual DOM의 진정한 사용 의미는 무엇일까?  
그것은 우리가 귀찮게 모든 변화를 인지하거나 생각할 필요가 없다는 점이다.  
즉, 우리가 수동으로 DOM flagment를 모아서 마지막에 DOM을 업데이트하는 과정을 자동화, 추상화한 것이 Virtual DOM 되시겠다.  

<br>
<br>

### 아 ㅋㅋ 그럼 DOM보다 Virtual DOM을 사용하는 React가 더 빠른거 맞지?
질문 자체가 잘못되었다.  
물론 굳이 답하자면 환경에 따라 다르다고 할 수 있겠다.  
그리고 역할이 다르다.  
Virtual DOM의 역할은 가상 DOM을 생성하고, 기존 상태와 변화된 상태를 비교하고, 가상 DOM을 업데이트하고, 실제 DOM에 적용한다.  
실제 DOM은 브라우저가 랜더링하는 과정에서 DOM의 상태변화가 생기면 리플로우가 일어난다.  
즉, DOM 접근이 매우 잦은 환경에서는 Virtual DOM을 사용하는 것이 빠르겠지만, DOM 접근이 많이 일어나지 않는 환경에서는 단순히 DOM을 사용하는 것이 더 빠를 수 있다.  

> Myth: React is "faster than DOM".  
> Reality: it helps create maintainable applications, and is fast enough for most use case.  
> \- Dan Abramov 트윗

Dan Abramov는 React가 대부분의 유스 케이스에서 충분히 빠르고 유지보수에 좋다고 트윗을 올렸다.  
충분히 빠르다. 즉, 대부분의 상황에서 react는 느리지 않다. 그리고 유지보수가 가능한 어플리케이션을 만들도록 도와준다.  

Virtual DOM도 비슷한 맥락이라 생각한다.  
VDOM이 없어도 되지만 VDOM은 DOM 접근에 대해 리플로우가 일어나는 상황을 고려하지 않고 코드를 작성할 수 있다. 때문에 생산성이 올라가고 유지보수에 적합하다. 그리고 VDOM이 실제 DOM보다 불리한 환경에서도 VDOM이 충분히 빠르기 때문에 유지보수의 강점을 가져올 수 있는 것이 아닐까 생각한다.

<br>
<br>
<br>
<br>

### 출처
https://velopert.com/3236  
https://ko.reactjs.org/docs/faq-internals.html#gatsby-focus-wrapper  
